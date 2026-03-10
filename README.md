# Shortest Job First (Non-Preemptive) CPU Scheduling

## Question
Write a C program sjf.c that implements Shortest Job First (Non-Preemptive) CPU Scheduling.

Input Format:
n
PID1 AT1 BT1
PID2 AT2 BT2
...
PIDn ATn BTn

## Sample Input
4
P1 0 6
P2 1 8
P3 2 7
P4 3 3

## Sample Output

Waiting Time:
P1 0
P2 15
P3 7
P4 3

Turnaround Time:
P1 6
P2 23
P3 14
P4 6

Average Waiting Time: 6.25
Average Turnaround Time: 12.25
