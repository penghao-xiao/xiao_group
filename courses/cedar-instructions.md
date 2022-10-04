# Job Submission on a Compute Canada Cluster

    1. Login to the cluster by running the following command on your terminal  
Linux: `$ssh –y username@cedar.computecanada.ca`   
Windows: MobaXterm  

    2. Enter your password  
    
    3. Change your directory to scratch  
    
`$ cd ~/scratch`  
    4. Make a new directory (e.g. LNO) 
    
`$ mkdir LNO`  
    5. Copy the 4 files to this new directory using either the protocols described on the [cc doc on transferring data](https://docs.alliancecan.ca/wiki/Transferring_data/en)  You can achieve this by downloading [FileZilla- GUI utility](https://filezilla-project.org/download.php?platform=osx)
Complete the setup.  Launch FileZilla utility and you’ll see 3 fields on the top. Copy and paste-  
host: sftp://cedar.computecanada.ca  
username: username  
password: password  
Click quick connect. Now you have connected to the server for file transfer.  You just need to drag and drop the 5 VASP input files to the location ~/scratch/LNO/

    6. Get back into the terminal and launch the calculation.  
`$ sbatch sbatch.cedar`  
  
###### Re-running the calculations to convergence  
In your folders, run the command   
`$ vef.pl`  
to see if the forces are below (or close) the no. we set in the INCAR (compare with EDIFFG tag).  If not, then copy WAVECAR by typing  
`$ cp WAVECAR WAVECARCP`  
Then type  
`$ vfin.pl run0`
Rename WAVECARCP by  
`$ mv WAVECARCP WAVECAR`  
Finally rerun the calculations again  
`$ sbatch sbatch.cedar`
