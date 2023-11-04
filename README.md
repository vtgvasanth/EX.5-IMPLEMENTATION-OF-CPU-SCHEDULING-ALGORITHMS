# Aim

To implement the first come first serve scheduling algorithm

# Algorithm
1. Start the process
2. Get the number of processes to be inserted
3. Get the value for burst time of each process from the user
4. Having allocated the burst time(bt) for individual processes , Start with the first
process from its initial position let other process to be in queue
5. Calculate the waiting time(wt) and turnaround time(tat) as
6. Wt(pi) = wt(pi-1) + tat(pi-1) (i.e. wt of current process = wt of previous process + tat of
previous process)
7. tat(pi) = wt(pi) + bt(pi) (i.e. tat of current process = wt of current process + bt of
current process)
8. Calculate the total and average waiting time and turnaround time
9. Display the values
10. Stop the process

# GANTT CHART

![image](https://github.com/Harsayazheni/EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS/assets/118708467/4cf27afa-57b7-4d4b-a04e-367b6d127f00)

# PROGRAM
```
#include<stdio.h>
int main()
{
int bt[20],p[20],wt[20],tat[20],i,j,n,total=0,pos,temp; float
avg_wt,avg_tat;
printf("Enter number of process:");
scanf("%d",&n);
printf("\nEnter Burst Time:\n");
for(i=0;i<n;i++)
{
printf("p % d:",i+1);
scanf("%d",&bt[i]);
p[i]=i+1; //contains process number
}
wt[0]=0; //waiting time for first process will be zero
//calculate waiting time
for(i=1;i<n;i++)
{
wt[i]=0;
for(j=0;j<i;j++)
wt[i]+=bt[j];
total+=wt[i];
}
avg_wt=(float)total/n; //average waiting time
total=0;
printf("\nProcess\t Burst Time \tWaiting Time\tTurnaround Time");
for(i=0;i<n;i++)
{
tat[i]=bt[i]+wt[i]; //calculate turnaround time
total+=tat[i];
printf("\np%d\t\t %d\t\t %d\t\t\t%d",p[i],bt[i],wt[i],tat[i]);
}
avg_tat=(float)total/n; //average turnaround time
printf("\n\nAverage Waiting Time=%f",avg_wt);
printf("\nAverage Turnaround Time=%f\n",avg_tat);
}
```
# OUTPUT

![image](https://github.com/Harsayazheni/EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS/assets/118708467/a667c592-6abd-41ae-b97c-dff48e236c3c)

# RESULT

Thus, the first come first serve scheduling algorithm is implemented successfully.

# Aim

To implement the shortest job first scheduling algorithm

# Algorithm
1. Start the process
2. Get the number of processes to be inserted
3. Get the value for burst time of each process from the user
4. Having allocated the burst time(bt) for individual processes , Start with the first
process from its initial position let other process to be in queue
5. Calculate the waiting time(wt) and turnaround time(tat) as
6. Wt(pi) = wt(pi-1) + tat(pi-1) (i.e. wt of current process = wt of previous process + tat of
previous process)
7. tat(pi) = wt(pi) + bt(pi) (i.e. tat of current process = wt of current process + bt of
current process)
8. Calculate the total and average waiting time and turnaround time
9. Display the values
10. Stop the process

# GANTT CHART

![image](https://github.com/Harsayazheni/EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS/assets/118708467/0f412720-6a23-41a4-85d0-ec25adf68845)


# PROGRAM
```
#include<stdio.h>
int main()
{
int bt[20],p[20],wt[20],tat[20],i,j,n,total=0,pos,temp; float
avg_wt,avg_tat;
printf("Enter number of process:");
scanf("%d",&n);
printf("\nEnter Burst Time:\n");
for(i=0;i<n;i++)
{
printf("p%d:",i+1);
scanf("%d",&bt[i]);
p[i]=i+1; //contains process number
}
//sorting burst time in ascending order using selection sort
for(i=0;i<n;i++)
{
pos=i;
for(j=i+1;j<n;j++)
{
if(bt[j]<bt[pos])
pos=j;
}
temp=bt[i];
bt[i]=bt[pos];
bt[pos]=temp;
temp=p[i];
p[i]=p[pos];
p[pos]=temp;
}
wt[0]=0; //waiting time for first process will be zero
//calculate waiting time
for(i=1;i<n;i++)
{
wt[i]=0;
for(j=0;j<i;j++)
wt[i]+=bt[j];
total+=wt[i];
}
avg_wt=(float)total/n; //average waiting time
total=0;
printf("\nProcess\t Burst Time \tWaiting Time\tTurnaround Time");
for(i=0;i<n;i++)
{
tat[i]=bt[i]+wt[i]; //calculate turnaround time
total+=tat[i];
printf("\np%d\t\t %d\t\t %d\t\t\t%d",p[i],bt[i],wt[i],tat[i]);
}
avg_tat=(float)total/n; //average turnaround time
printf("\n\nAverage Waiting Time=%f",avg_wt);
printf("\nAverage Turnaround Time=%f\n",avg_tat);
}
```
# OUTPUT

![image](https://github.com/Harsayazheni/EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS/assets/118708467/523eb466-a2a3-4493-a01f-b4dd4afbae9b)


# RESULT

Thus, the first come shortest job first algorithm is implemented successfully.

# Aim

To implement the priority scheduling algorithm

# Algorithm
1. Start the process
2. Get the number of processes to be inserted
3. Get the corresponding priority of processes
4. Sort the processes according to the priority and allocate the one with highest priority
to execute first
5. If two process have same priority then FCFS scheduling algorithm is used
6. Calculate the total and average waiting time and turnaround time
7. Display the values
8. Stop the process

# GANTT CHART

![image](https://github.com/Harsayazheni/EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS/assets/118708467/87cc32d4-9b10-4f25-9e24-b8cc372f74d9)


# PROGRAM
```
#include<stdio.h>
int main()
{
int bt[20],p[20],wt[20],tat[20],pri[20],i,j,k,n,total=0,pos,temp; float
avg_wt,avg_tat;
printf("Enter number of process:");
scanf("%d",&n);
printf("\nEnter Burst Time:\n");
for(i=0;i<n;i++)
{
printf("p%d:",i+1);
scanf("%d",&bt[i]);
p[i]=i+1; //contains process number
}
printf(" enter priority of the process ");
for(i=0;i<n;i++)
{
p[i] = i;
//printf("Priority of Process");
printf("p%d ",i+1);
scanf("%d",&pri[i]);
}
for(i=0;i<n;i++)
for(k=i+1;k<n;k++)
if(pri[i] > pri[k])
{
temp=p[i];
p[i]=p[k];
p[k]=temp;
temp=bt[i];
bt[i]=bt[k];
bt[k]=temp;
temp=pri[i];
pri[i]=pri[k];
pri[k]=temp;
}
wt[0]=0; //waiting time for first process will be zero
//calculate waiting time
for(i=1;i<n;i++)
{
wt[i]=0;
for(j=0;j<i;j++)
wt[i]+=bt[j];
total+=wt[i];
}
avg_wt=(float)total/n; //average waiting time
total=0;
printf("\nProcess\t Burst Time \tPriority \tWaiting Time\tTurnaround Time");
for(i=0;i<n;i++)
{
tat[i]=bt[i]+wt[i]; //calculate turnaround time
total+=tat[i];
printf("\np%d\t\t %d\t\t %d\t\t %d\t\t\t%d",p[i],bt[i],pri[i],wt[i],tat[i]);
}
avg_tat=(float)total/n; //average turnaround time
printf("\n\nAverage Waiting Time=%f",avg_wt);
printf("\nAverage Turnaround Time=%f\n",avg_tat);
}
```
# OUTPUT

![image](https://github.com/Harsayazheni/EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS/assets/118708467/0e8eccaa-dfad-4e7d-b817-65a835968bc0)



# RESULT

Thus, the priority algorithm is implemented successfully.

# Aim

To implement the round robin scheduling algorithm

# Algorithm
1. Start the process
2. Get the number of elements to be inserted
3. Get the value for burst time for individual processes
4. Get the value for time quantum
5. Make the CPU scheduler go around the ready queue allocating CPU to each process
for the time interval specified
6. Make the CPU scheduler pick the first process and set time to interrupt after quantum.
And after it's expiry dispatch the process
7. If the process has burst time less than the time quantum then the process is released by
the CPU
8. If the process has burst time greater than time quantum then it is interrupted by the OS
and the process is put to the tail of ready queue and the schedule selects next
process from head of the queue
9. Calculate the total and average waiting time and turnaround time
10. Display the results

# GANTT CHART

![image](https://github.com/Harsayazheni/EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS/assets/118708467/21e4cb71-96d8-49ed-be60-ebc2af91ed9b)


# PROGRAM
```
#include<stdio.h>  
#include<conio.h>  
  
void main()  
{  
    // initlialize the variable name  
    int i, NOP, sum=0,count=0, y, quant, wt=0, tat=0, at[10], bt[10], temp[10];  
    float avg_wt, avg_tat;  
    printf(" Total number of process in the system: ");  
    scanf("%d", &NOP);  
    y = NOP; // Assign the number of process to variable y  
  
// Use for loop to enter the details of the process like Arrival time and the Burst Time  
for(i=0; i<NOP; i++)  
{  
printf("\n Enter the Arrival and Burst time of the Process[%d]\n", i+1);  
printf(" Arrival time is: \t");  // Accept arrival time  
scanf("%d", &at[i]);  
printf(" \nBurst time is: \t"); // Accept the Burst time  
scanf("%d", &bt[i]);  
temp[i] = bt[i]; // store the burst time in temp array  
}  
// Accept the Time qunat  
printf("Enter the Time Quantum for the process: \t");  
scanf("%d", &quant);  
// Display the process No, burst time, Turn Around Time and the waiting time  
printf("\n Process No \t\t Burst Time \t\t TAT \t\t Waiting Time ");  
for(sum=0, i = 0; y!=0; )  
{  
if(temp[i] <= quant && temp[i] > 0) // define the conditions   
{  
    sum = sum + temp[i];  
    temp[i] = 0;  
    count=1;  
    }     
    else if(temp[i] > 0)  
    {  
        temp[i] = temp[i] - quant;  
        sum = sum + quant;    
    }  
    if(temp[i]==0 && count==1)  
    {  
        y--; //decrement the process no.  
        printf("\nProcess No[%d] \t\t %d\t\t\t\t %d\t\t\t %d", i+1, bt[i], sum-at[i], sum-at[i]-bt[i]);  
        wt = wt+sum-at[i]-bt[i];  
        tat = tat+sum-at[i];  
        count =0;     
    }  
    if(i==NOP-1)  
    {  
        i=0;  
    }  
    else if(at[i+1]<=sum)  
    {  
        i++;  
    }  
    else  
    {  
        i=0;  
    }  
}  
// represents the average waiting time and Turn Around time  
avg_wt = wt * 1.0/NOP;  
avg_tat = tat * 1.0/NOP;  
printf("\n Average Turn Around Time: \t%f", avg_wt);  
printf("\n Average Waiting Time: \t%f", avg_tat);  
getch();  
}  
```
# OUTPUT

![image](https://github.com/Harsayazheni/EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS/assets/118708467/67af8c83-3863-4e6c-a650-e8c032bcf044)

# RESULT

Thus, the round robin algorithm is implemented successfully.
