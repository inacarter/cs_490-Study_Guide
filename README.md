# cs_490-Study_Guide
help me. 

CHAPTER 1 – COMPUTER SYSTEM OVERVIEW
	Know the purpose/function of the Program Counter, Instruction Register, MAR and MBR
	The PC holds the address of the next instruction to be pointed to by the IR.
	Pc hold address of next instruction.
	Ir holds the address of the executing instruction.
	Memory Buffer Register-> Used for moving data from immediate to memory and vice versa.	
	MAR-> Holds the memory location of where data needs to be put or taken from.  
	Understand the basic instruction execution cycle, including interrupt check/processing.
	Lea to PC-> lea PC To MAR-> inc PC-> lea needed data to MDR -> MAR to IR->jump?-y>to step one-N> exe instruct-> interrupt?-Y>service interrupt-N> to step 1. 
	What was the original motivation for multi-programming?
	I can’t say unless I interview the creators.

	The idea of multi-programming is attempting to decrees CPU idle time. If a process is doing I/O the cpu my definition is not 	needed for this task so it loads the next program from main memory to the execution state 
	Four classes of interrupts; interrupt processing
	Program (illegal instructions-> 0/number  )
	Timer (made by a clock allows for timed processing)
	I/O (signal completion of task or an error)
	Hardware failure (power, memory failure)

	Be able to describe the memory hierarchy, define hit ratio, and compute average system access time (as on your homework). Know the purpose of cache memory 
	Inboard memory
Registers, cache, main memory.
	Outboard memory
HDD, optical drive.
	Off line storage
Tape drive
(0.95)×(0.1 µs) + (0.05) × (0.1 µs + 1 µs) = 0.095 + 0.055 = 0.15 µs

	How does DMA I/O improve performance in a multi-programmed computer system?
	
	State a difference/similarity between a Symmetric MultiProcessor(SMP) and a multicore computer.

































CHAPTER 2 – OPERATING SYSTEM OVERVIEW
	Three objectives of an operating system.
	Marry/manage hardware and software.
	Allow control of system resources.
	Schedule takes and process in some given order.  

	What is an OS kernel?
	It’s the intermediate step between software applications (processes) and the systems hardware.

	Why are the following hardware features (originally introduced to support batch processing) important in multiprogrammed operating systems?
	Memory protection
	To protect data integrity
	Timers
	To schedule takes (programs) 
	Privileged instructions
	
	Interrupts 
	The main use of a multi-programmed systems to allow use while running an I\O instruction.
	Difference between user mode and kernel mode of execution
	The ability to manipulate system hardware, where’s user level processes must use an api to gain access to system headwear, 	in kernel mode there is no restriction, however if failure happens in the kernel the system 	will stop.
	Difference between batch multiprocessing and time sharing systems (ask question)
	A batch process is set up and ran in some pre-defined order, thus any interruption (failure) is expensive since 	there’s no user 	controlling the processes, time sharing systems typically involve constant use rinteraction and 	if failure happens there’s a 	user monitoring program execution. 
	Definition of process
	The action of completing the requests a program makes.

	What is the execution context, or state, of a process? (Ask question)
	The internal data by which the OS is able to supervise and control the process.

	Be sure you understand the concepts of interleaved and overlapped execution.
		Interleaved execution
			Even though this takes some overhead it still improves processing efficiency
		Overlapped execution
			(Ask question)
































CHAPTER 3 – PROCESSES
	How does a process differ from a program?
	A process MUST follow the steps of execution.

	A program has not predefined behavior, and thus can be/do whatever it want’s hindered only by the hardware architecture it’s 	made on/for.
	What’s the purpose of a Process Control Block? (PCB) What are some of its contents?
	Purpose: to allow the process to be halted, moved and started again. It’s basically a structure containing the state of the process.

	Contents: identifier, state, priority, program counter, memory pointers, context data, I/O status and accounting information.

	Be able to describe the 5-State process model on page 117.  Know the meaning of each state and the events that cause a process to transition from one state to another.








	How does the addition of swapping and suspended states modify the 5-state model?
	It allows toe CPU to move processes that need to do I/O to disk and will free up the processor for the next task.
	Explain the role of system calls (supervisor calls) in a typical operating system.
	
	Mechanisms for interrupting process execution (p. 137) and examples of events that might trigger them.
	Clock interrupt: If a process is taking too long.
	I/O interrupt:if a process is in an I/O state and ofther process need to execute something other than an I/O request.
	Memory fault: processor finds virtual memory address that’s not in main memory.

	Be able to distinguish between a mode switch and a process switch and give an example of an event that would cause each type of switch.
	
	In UNIX, what is the difference between the user running and kernel running state?
		
CHAPTER 4 – THREADS
	What is the relation between a process and a thread?
	This is a one to many relationship
	Be able to give one use for threads in a single-user multiprocessing system.
	Multiprocessing does not mean multithreading.
	Possibly running different threads on different cores in the CPU.
	(ASK QUESTION)  
	Disadvantage of structuring an application as multiple cooperating programs versus a single multithreaded program. (ASK QUESTION)  
	The threads of the multithreaded program can communicate faster and more efficiently.

	The separate yet cooperation programs would not share scope of variables and would be effected by any mutual exclusion 	structure.
		
	State the difference between a KLT and a ULT and give advantages and disadvantages of each type of thread.
	The scope and scheduling/execution speed. The OS does not schedule user level threads and they run slower 	because they get blocked when they need to make system calls. Kernel level threads have full scope of the threads, 	and can schedule accordingly; also if the KLT is blocked the OS can spawn another instance of the thread in hopes 	of not being blocked.

	In Windows, what is the Standby state?
	A state that a thread can possess where in it waits for its soon to be processor to become freed and available for use.













CHAPTER 6: DEADLOCK
	Define deadlock
	The happenstance where two processes are both waiting on each other to finish or release resources.  
	What are the four conditions that are necessary for a deadlock to take place?
	Mutual exclusion.
	No preemption
	Hold and wait
	Circular wait
	Know the difference between deadlock prevention & deadlock avoidance, and be able to discuss each in terms of effectiveness, cost (execution time, burden placed on programmers, etc.). Study Table 6.1 on page 266.
	What is deadlock detection?




CHAPTER 5 – CONCURRENCY: MUTUAL EXCLUSION AND SYNCHRONIZATION
	Multiprogramming versus multiprocessing
	
	Table 5.1: understand/be able to define and discuss these terms (except livelock)
	Atomic operation: an operation that is guaranteed to run till completion of not at all without out interruption.
	Critical section: a section of code that needs shared resources, where in two operations cannot both be in said section 
	Deadlock: The happenstance where two processes are both waiting on each other to finish or release resources.  
	Mutual exclusion: 
	race condition
	starvation
	Understand how interleaved or overlapped execution of critical sections can cause data incoherence. See examples on page 201 & 203 which demonstrate the problem on a uniprocessor and a multiprocessor.
	What are some hardware techniques for guaranteeing mutual exclusion?  What are their disadvantages?
	What is a semaphore?  Be able to state the algorithms for a general counting semaphore and trace its behavior.
	Know how semaphores can be used to guarantee mutual exclusion.  
	Be able to state the conditions of the Producer Consumer problem.  Understand the solution to the bounded-buffer PC problem with semaphores (page 226).  No need to memorize, but know how it works.
	What are the basic characteristics of a monitor? What is a difference between a condition variable and semaphore?
	Can messages be used for process synchronization?
	What is the difference between a blocking and a non-blocking message send or receive?
	What is a mailbox, with respect to message passing?
	Know the characteristics of the Readers and Writers problem.  If given the algorithms, be able to identify the purpose of the various semaphores and variables.
	What is a UNIX pipe?
	Be able to work problems similar to the ones on the homework.

