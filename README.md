# Abaqus live batch script
Monitors a folder and runs all .inp sequentially that are placed in the folder

<br>

- Place script in a dedicated folder
- Add an abaqus_v6.env in the folder to define default settings for memory and cpus/cores

- Run script in that folder (cmd: abaqus python scriptname)
- An automatically generated file named abq_queue_running.txt shows that the script is running
- The script checks regularly regarding the files in the folder
	- Sleep time is the pause between each check
- Every .inp in that folder is submitted one after another
- A .inp is not submitted when a .log file with the same name exists
- Script is not submitting a .inp while a job is running
	- The exitance of a .lck file indicates that a job is running
- Input files named *_f.inp are ignored
	- Flatted input files that may be generated by Abaqus

- Add a file named terminate.txt into the folder to terminate the current job
- Add a file named end.txt into the folder to end the script
	- A currently running job will continue to run
	- Use command line to terminate it if needed (cmd: abaqus j=jobname terminate)