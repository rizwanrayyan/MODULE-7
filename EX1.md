# Ex.No:1
# Ex.Name : write a C++ program to implement FCFS algorithm(no of.process p1,p2 and p3 and its burst time are 10,5 & 8) find out waiting time  & Turn Around time of the the process?
## Date: 18/09/2025
## Aim: To write a C++ program to implement the First Come First Serve (FCFS) CPU scheduling algorithm for 3 processes (P1, P2, P3) with burst times 10, 5, and 8, and calculate the Waiting Time (WT) and Turnaround Time (TAT) of each process.


## Algorithm:
```
1.Start the program.

2.Input the number of processes (here 3) and burst times.

3.Set the waiting time of the first process as 0.

4.For each remaining process:

5.Waiting Time = Sum of burst times of all previous processes.

6.Turnaround Time = Burst Time + Waiting Time.

7.Display all Waiting Times and Turnaround Times.

8.Stop the program.
```
## Program: 
```cpp
#include <iostream>
#include <vector>

using namespace std;

struct Process {
    int id;
    int burst_time;
    int waiting_time;
    int turnaround_time;
};

void calculateTimes(vector<Process>& processes) {
    int n = processes.size();
    processes[0].waiting_time = 0;
    processes[0].turnaround_time = processes[0].burst_time;

    for (int i = 1; i < n; ++i) {
        processes[i].waiting_time = processes[i - 1].waiting_time + processes[i - 1].burst_time;
        processes[i].turnaround_time = processes[i].waiting_time + processes[i].burst_time;
    }
}

void printTable(const vector<Process>& processes) {
    cout << "Processes   BT time   WT time   TA time" << endl;
    for (const auto& process : processes) {
        cout << "       " << process.id << "       " << process.burst_time << "       " << process.waiting_time << "       " << process.turnaround_time << endl;
    }
}

double calculateAverageWaitingTime(const vector<Process>& processes) {
    int total_waiting_time = 0;
    for (const auto& process : processes) {
        total_waiting_time += process.waiting_time;
    }
    return static_cast<double>(total_waiting_time) / processes.size();
}

double calculateAverageTurnaroundTime(const vector<Process>& processes) {
    int total_turnaround_time = 0;
    for (const auto& process : processes) {
        total_turnaround_time += process.turnaround_time;
    }
    return static_cast<double>(total_turnaround_time) / processes.size();
}

int main() {
    vector<Process> processes = {{1, 10, 0, 0}, {2, 5, 0, 0}, {3, 8, 0, 0}};

    calculateTimes(processes);
    printTable(processes);

   // cout << "Average waiting time = " << calculateAverageWaitingTime(processes) << endl;
    ///cout << "Average turn around time = " << calculateAverageTurnaroundTime(processes) << endl;

    return 0;
}
```



## Output:
<img width="883" height="251" alt="image" src="https://github.com/user-attachments/assets/aee6534c-528f-4e2a-bd3f-8072d3f5888d" />



## Result:
The FCFS scheduling algorithm was successfully implemented.
