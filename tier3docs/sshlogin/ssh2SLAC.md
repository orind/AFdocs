<style>
  #introMore {display: none;}
  #acctsMore {display: none;}
</style>

<script type="text/javascript" src="/tier3docs/scripts/readMoreOrLess.js"></script>

# SDF: a new computing environment at SLAC

For decades, SLAC runs a high throughput computing (HTC) environment, primarily serving the HEP community. This
environment feature AFS file system home directory and LSF batch system, along with CVMFS. This environment is 
also known as the AFS environment.

SLAC is now building a new computing environment: the Scientific Data Facility (SDF). The core componment 
of SDF is a high performance computer cluster (HPC) and a GPU cluster, both managed by a single SLURM batch 
system. CVMFS is available on all nodes. For storage, 
SDF provides Luster parallel file system for user home and data. 
SDF is still expanding and will likely experenice a rapid expansion in the near future. Other types of file
systems and storage systems, as well as HTC may also be introduced. 

For ATLAS users, we currently provide GPFS filesystem for home (100GB) and data (2-10TB) in the AFS environment 
(under /gpfs/slac/atlas/fs1/{u,d} respectively). 
At SDF, ATLAS users will get a new home directory of 25GB. The GPFS file system is also available in SDF until 
the hardware retires (at that time, we will migrate users from GPFS to Lustre). AFS file system is not available 
in SDF.

## <a name="sdf"></a>SSH login to SDF

`ssh <username>@sdf-login.slac.stanford.edu`

SLAC has two different computer accounts, unix and Windows. Please use your Windows account password to login. 
You may ask: What if I only have a unix account, and do not have a SLAC Windows account? Continue reading.

SDF uses a new identity management system (aka <span style="color:red">"SLAC ID"</span> - it will be a 
computer account to login to everything at SLAC). If you already have a SLAC Windows account, you are all 
set (SLAC ID = SLAC Windows account) and go to the next step. If you don't have a SLAC Windows account, 
please go to [SLAC SDF page and click 
"Accounts Portal"](https://sdf.slac.stanford.edu/public/doc/#/accounts-and-access?id=access). 
After this, give it a hour for the changes to be proprogated through SLAC computing.

## Submit SLURM batch job at SDF

The above URL is actually [the main page of SDF](https://sdf.slac.stanford.edu) (login info at the upper half
of the page, and user document at the lower half of the page). At there you can also find [the basic info about
using SLURM batch system](https://sdf.slac.stanford.edu/public/doc/#/batch-compute?id=using-slurm). One of the
lines in the example SLURM submission script, `#SBATCH --partition=shared` 
allows you to specify "shared" or "usatlas". 

ATLAS owns a small 
fraction of CPU resource in SDF. "usatlas" will give you guranteed access to ATLAS owned CPUs but you may have 
to wait if other ATLAS users are using them. "shared" allows you to access a large pool of CPUs (own by others)
so the waiting time will likely be shorter. But there is small risk that your job will be pre-emptied. 
The rule of thumb is to run short 
jobs in "shared", and run long jobs (12h+) in "usatlas".

To request a GPU, add "#SBATCH --gpus=1" to the submission script. All installed GPUs are Nvidia CUDA GPUs. Since
ATLAS currently does not own a GPU at SDF, you will need to use `#SBATCH --partition=shared` if you request
a GPU.

## SSH login to the AFS environment and submit LSF batch jobs

`ssh <username>@centos7.slac.stanford.edu`

You should use unix account password to login. Note that as 
SLAC retires the AFS environment in the next few years, this type of account (unix) may disappear.

The following page has many useful info about using the AFS environment, esepecially with regard to using the LSF
batch system. 

https://confluence.slac.stanford.edu/display/Atlas/SLAC+Analysis+Computing+Facility

## Remote X-windows access

SLAC currently provides [Fast-X](https://confluence.slac.stanford.edu/display/SCSPub/FastX) for accelerated 
X-window access. Fast-X maybe useful when you are far away from SLAC (geographically, or over a high latency network)
and you want to diaply your ROOT 2-D or 3-D/scatter plot.
You should use SLAC unix username and password to login to Fast-X. Once you are on Fast-X, you can 
`ssh -Y` to SDF or AFS login nodes.

Note that upon login to Fast-X, you may find some space that you can save a few files. Do NOT 
use this space for anything. This space is not your main GPFS or Lustre storage, it is not accessible from 
the AFS or SDF environment. It is also subject to deletion without notice.


SLAC is investigating [NoMachine](https://www.nomachine.com) as a replacement of Fast-X.

## Setup ATLAS environment

A typical way to setup ATLAS environment upon login is to put the following in $HOME/.bashrc. This is the same
at both AFS and SDF.

```
export ALRB_localConfigDir=/gpfs/slac/atlas/fs1/sw/localconfig
export RUCIO_ACCOUNT="change_me"
export ATLAS_LOCAL_ROOT_BASE=/cvmfs/atlas.cern.ch/repo/ATLASLocalRootBase
alias setupATLAS='source $ATLAS_LOCAL_ROOT_BASE/user/atlasLocalSetup.sh'
...
```
