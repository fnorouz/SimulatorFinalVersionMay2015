# SimulatorFinalVersionMay2015
1-	Input : 
a.	DC.xml : physical layout of the data center.
b.	DC_Logic.xml  list of all systems, their corresponding applications and their associated workload are specified in this input file. Make sure that all of workloads file are existed.
c.	D matrix is a text file which should be existed. D.txt D file is actual heat recirculation matrix that is given to the simulator. To get a new D matrix for you new data center please refer to the appendix of the thesis.
d.	According to  DC_Logic.xml   each system needs to have its own XML file.
e.	Amtopology.xml is the topology file for AMs. If you have added a new AM class make sure before running the simulator go and update the AM topology. Pairing between AM and associating AM to the managed objects can be done through the user interface.
2-	There is a general system class for systems and each system inherits from this class. If you  need to define a new system based on system type (HPC, Enterprise, Interactive) follow the sample system in the code.
3-	For AM we have a general AM class, for each new class of AM we need to define a new class inherited from this class. 
4-	There is a bladeserver class which simulate the behavior of a server. Servers has a ready flag which its different values has different meanings:
a.	-3:  it is not assigned to any system yet
b.	-2: it is in a system but is not assigned to an application
c.	-1: it is idle
d.	0 or 1 is ready or not just the matter of CPU utilization over 100% or not
5-	Policies for each AM is hardcoded inside the managers class. Make sure to separate the logic of the code and write proper code in Monitoring, Analysis, Planning, and Execution module of the managers. 
a.	To write policies make sure to take care of messaging, updating the message file and also total number of messages.
b.	Use the global time Main.LocalTime to deploy the timers
6-	There are two general scheduling and resource allocation classes are defined. For each new scheduling algorithm or resource allocation algorithm, you need to create a new class from these two classes and override the proper functions which is nextJob for schedule and nextServer for the allocation algorithms. 

7-	Outputs: 
a.	For each type of defined system we have one SLALog.txt which record the SLA violation during simulation time.
b.	Power consumption of each chassis in the system will be recorded by time in out_W.txt file. Moreover, total computing power and cooling power are recorded in this log file.
c.	MessageLog.txt list of all messages passed between the managers by the time.
d.	At the end of the simulator will show information regarding total number of violation for each system and log of any allocation and release server to each system during time.
e.	Total amount of computing power for each system will be shown as simulator output.
f.	If there is any over red temperature recorded during simulation time, at the end of the simulator it will be recorded.  Note that for each over red temperature the cooling power is negative so the total power consumption is not valid.

