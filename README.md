Airport Simulation

Overview

This repository contains a simulation model of an airport check-in and security process using simpy. The model was developed as part of a student project during the Georgia Tech OMSA program. The purpose of the simulation is to analyze and optimize the process flow and wait times for passengers.

Dependencies

	•	Python 3.x
	•	simpy library

Installation

To run the simulation, you need to install the simpy library. You can install it using pip:

`pip install simpy`

Simulation Parameters

The simulation uses the following parameters to model the airport process:

	•	clerks: Number of available check-in clerks.
	•	scanners: Number of available security scanners.
	•	arrival: Rate at which passengers arrive at the airport.
	•	checkin: Average time for check-in process.
	•	min_scan: Minimum time for security scanning.
	•	max_scan: Maximum time for security scanning.
	•	runtime: Total time for which the simulation runs.
	•	reps: Number of simulation repetitions to perform for averaging results.

Global Variables

The simulation tracks several global variables to accumulate statistics:

	•	clerkwait, scanwait, sysTime, timeWait, timeClerk, timeClerkFin, timeScan, timeScanFin, passengersTotal

Class Definitions

Airport

Defines the airport environment with check-in clerks and security scanners.

	•	init: Initializes the environment with given numbers of clerks and scanners.
	•	check: Simulates the check-in process.
	•	scan: Simulates the scanning process.

Passenger Path

passenger

Defines the path and actions of a passenger through the airport process.

	•	arrivalTime: Time when the passenger arrives.
	•	clerk line: Queue for the check-in clerks.
	•	scanner line: Queue for the security scanners.

Setup Function

setup

Initializes the simulation environment and creates passenger processes at random intervals.

Simulation Execution

The simulation is executed multiple times to gather average metrics:

	•	avgWait, avgClerk, avgScan, avgSysTime: Lists to store average wait times, check-in times, scan times, and total system times across repetitions.

The results are printed at the end of the simulation:

`print('Average cumulative wait time: ' + str(sim_wait_avg))
print('Average cumulative checkin time: ' + str(sim_clerk_avg))
print('Average cumulative scan time: ' + str(sim_scan_avg))
print('Average cumulative system time: ' + str(sim_time_avg))`

Running the Simulation

To run the simulation, execute the script. The simulation will print out the average cumulative wait times, check-in times, scan times, and system times based on the defined parameters and number of repetitions.

Variable Significance and Impact on Simulation

Key Variables

	1.	clerks
	•	Description: Number of available check-in clerks.
	•	Impact: Increasing the number of clerks reduces the average waiting time for check-in, as more passengers can be processed simultaneously. Conversely, reducing the number of clerks will increase the waiting time, leading to longer queues.
	2.	scanners
	•	Description: Number of available security scanners.
	•	Impact: More scanners decrease the waiting time for security checks, allowing more passengers to be scanned concurrently. Fewer scanners will result in longer wait times and queues at the scanning stage.
	3.	arrival
	•	Description: Rate at which passengers arrive at the airport.
	•	Impact: A higher arrival rate increases the number of passengers entering the system, potentially leading to longer queues and wait times at both check-in and scanning stages. A lower arrival rate means fewer passengers, which could result in shorter wait times and less congestion.
	4.	checkin
	•	Description: Average time for the check-in process (exponential distribution).
	•	Impact: A longer check-in time will increase the duration each passenger spends with a clerk, causing longer queues and wait times. A shorter check-in time speeds up the process, reducing queues and wait times.
	5.	min_scan and max_scan
	•	Description: Minimum and maximum time for security scanning (uniform distribution).
	•	Impact: A longer scanning time range (higher values for min_scan and max_scan) increases the time each passenger spends at the scanner, leading to longer queues. Shorter scanning times will speed up the process, decreasing wait times and queue lengths.
	6.	runtime
	•	Description: Total time for which the simulation runs.
	•	Impact: A longer runtime allows the simulation to capture more data and observe the system’s behavior over a more extended period. A shorter runtime might not provide a complete picture of the system’s performance.
	7.	reps
	•	Description: Number of simulation repetitions.
	•	Impact: More repetitions increase the reliability of the average results by smoothing out random variations. Fewer repetitions might result in less accurate averages due to higher sensitivity to outliers and random fluctuations.

Global Variables for Tracking Performance

	1.	clerkwait
	•	Description: Accumulates total wait time for check-in.
	•	Impact: Used to calculate average wait time for check-in across all passengers and repetitions. Higher values indicate longer wait times at the check-in stage.
	2.	scanwait
	•	Description: Accumulates total wait time for security scanning.
	•	Impact: Used to calculate average wait time for scanning across all passengers and repetitions. Higher values indicate longer wait times at the scanning stage.
	3.	sysTime
	•	Description: Accumulates total system time for all passengers.
	•	Impact: Represents the total time spent by passengers in the system (from arrival to completion). Used to calculate the average system time across all passengers and repetitions.
	4.	timeWait
	•	Description: Accumulates total waiting time (sum of clerkwait and scanwait).
	•	Impact: Reflects the overall waiting time experienced by passengers, indicating the efficiency of the process.
	5.	timeClerk
	•	Description: Tracks the time when a passenger reaches the clerk.
	•	Impact: Helps calculate the waiting time for check-in by comparing it to the arrival time.
	6.	timeClerkFin
	•	Description: Tracks the time when a passenger completes the check-in process.
	•	Impact: Used to measure the duration of the check-in process and transition to the scanning stage.
	7.	timeScan
	•	Description: Tracks the time when a passenger reaches the scanner.
	•	Impact: Helps calculate the waiting time for the security scan by comparing it to the check-in completion time.
	8.	timeScanFin
	•	Description: Tracks the time when a passenger completes the scanning process.
	•	Impact: Used to measure the duration of the scanning process and overall system time.
	9.	passengersTotal
	•	Description: Tracks the total number of passengers processed.
	•	Impact: Useful for calculating averages and ensuring all passengers are accounted for in the performance metrics.

How Inputs Affect the Simulation

	1.	Increasing clerks or scanners: Reduces wait times and queues, improving overall system efficiency.
	2.	Increasing arrival rate: Increases congestion, leading to longer wait times and queues.
	3.	Increasing checkin or scan time: Slows down the process, increasing wait times and system time.
	4.	Increasing runtime: Provides more data for a thorough analysis but requires more computation time.
	5.	Increasing repetitions: Produces more reliable averages but also increases computational effort.

By adjusting these variables, you can simulate different scenarios and optimize the airport’s check-in and security processes to improve passenger flow and reduce wait times.
