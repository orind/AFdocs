## Analysis Facilities

### Brookhaven National Lab (BNL)

The Shared Physics Analysis Resources (SPAR) @ BNL is a project to provide computing resources (CPU, disk space, analysis support) for a "shared" T3 at BNL. These computing resources are available for use and testing to all US ATLAS members (not explicitly BNL users). The system uses the already existing [Scientific Data and Computing Center (SDCC)](https://www.sdcc.bnl.gov/information/about-sdcc). It is supported with the help of the [US ATLAS Technical Support Group](https://po.usatlas.bnl.gov/programoffice/ps.php).
 

### University of Chicago (UChicago)

The ATLAS Analysis Facility at UChicago offers users a mix of traditional batch computing alongside of forward-looking technologies like Kubernetes, Jupyter and Dask. This af is funded by NSF and co-located with MWT2-UC to complement the two DOE funded analyss facilities at SLAC and BNL. 

This facility offers 3 modes of access: Traditional Tier-3, Jupyter Notebook and Coffea. It provides up to 1PB of local disk storage, ~1000 CPU cores and close integration with MWT2, each user starts with 5TB$DATA (which can be raised up to 10TB) and 100GB$HOME.
UChicago is available to all US-ATLAS collaborators with secure authentication through federated login via CIlogon including cern login.


### Stanford Linear Accelerator Center (SLAC)

The SLAC Analysis Facility is open to and welcome all US ATLAS physicists and their ATLAS collaborators. The AF provides backup-ed user home directories, dedicated private data space, and several Rucio endpoints for user to bring official ATLAS data products to site for local processing. A Xcache is also available for users to quickly scan though official ATLAS data product without moving data to SLAC. SLAC AF uses SLURM to manage batch systems. US ATLAS has deploy dedicated CPU resource and GPU resource at SLAC AF. AF users also have opportunistic access to a very large pool of GPUs via SLURM.

ATLAS software and Grid/Panda/Rucio client environment are available at SLAC AF via CVMFS. SLAC AF provides a user expandable Jupyter environment. The ATLAS Jypyter environment includes kernels that integrates PyROOT/uproot and ATLAS software releases. It also includes kernels to support a set of common industry AI environments such as TensorFlow/Keras and Rapids AI. User can expand this environment to include their own software packages or kernels by following the instruction in US ATLAS AF document. Furthermore, users can bring their own Jupyter environment and run at SLAC AF. 

SLAC AF supports their users via a CERN MatterMost channel, and will migrate the support to a Discourse service centrally hosted by BNL for all US ATLAS AFs.
