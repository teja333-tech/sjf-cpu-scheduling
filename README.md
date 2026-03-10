# Shortest Job First (Non-Preemptive) CPU Scheduling

## Program
This program implements the Shortest Job First (SJF) Non-Preemptive CPU Scheduling algorithm using C.

## Input Format
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


PROGRAM

#include <stdio.h>
#include <string.h>

struct process {
    char pid[10];
    int at;
    int bt;
    int wt;
    int tat;
    int completed;
};

int main() {
    int n, i, completed = 0, time = 0, min_bt, index;
    float avg_wt = 0, avg_tat = 0;

    printf("Enter number of processes: ");
    scanf("%d", &n);

    struct process p[n];

    for(i = 0; i < n; i++) {
        scanf("%s %d %d", p[i].pid, &p[i].at, &p[i].bt);
        p[i].completed = 0;
    }

    while(completed < n) {
        min_bt = 9999;
        index = -1;

        for(i = 0; i < n; i++) {
            if(p[i].at <= time && p[i].completed == 0) {
                if(p[i].bt < min_bt) {
                    min_bt = p[i].bt;
                    index = i;
                }
            }
        }

        if(index != -1) {
            time += p[index].bt;

            p[index].tat = time - p[index].at;
            p[index].wt = p[index].tat - p[index].bt;

            avg_wt += p[index].wt;
            avg_tat += p[index].tat;

            p[index].completed = 1;
            completed++;
        }
        else {
            time++;
        }
    }

    printf("\nWaiting Time:\n");
    for(i = 0; i < n; i++) {
        printf("%s %d\n", p[i].pid, p[i].wt);
    }

    printf("\nTurnaround Time:\n");
    for(i = 0; i < n; i++) {
        printf("%s %d\n", p[i].pid, p[i].tat);
    }

    printf("\nAverage Waiting Time: %.2f\n", avg_wt/n);
    printf("Average Turnaround Time: %.2f\n", avg_tat/n);

    return 0;
}
