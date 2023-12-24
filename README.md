# Multiple server with infinite capacity - (M/M/c):(oo/FIFO)
## Aim :
To find (a) average number of materials in the system (b) average number of materials in the conveyor (c) waiting time of each material in the system (d) waiting time of each material in the conveyor, if the arrival  of materials follow poisson process with the mean interval time 10 seconds, serivice time of two lathe machine follow exponential distribution with mean serice time 1 second and average service time of robot is 7seconds.

## Software required :
Visual components and Python

## Theory:
Queuing are the most frequently encountered problems in everyday life. For example, queue at a cafeteria, library, bank, etc. Common to all of these cases are the arrivals of objects requiring service and the attendant delays when the service mechanism is busy. Waiting lines cannot be eliminated completely, but suitable techniques can be used to reduce the waiting time of an object in the system. A long waiting line may result in loss of customers to an organization. Waiting time can be reduced by providing additional service facilities, but it may result in an increase in the idle time of the service mechanism.

![image](https://user-images.githubusercontent.com/103921593/203238035-1c8109bc-cbf2-4c77-baea-c5b682a752ef.png)

## Procedure :

![image](https://user-images.githubusercontent.com/103921593/203238265-176740b0-eae2-4772-90be-5449869ac9b0.png)




## Experiment:
![image](https://private-user-images.githubusercontent.com/94154780/239796810-1d35f4d1-3104-44f4-8c5c-269d611eaee2.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTEiLCJleHAiOjE3MDM0MzAyMjMsIm5iZiI6MTcwMzQyOTkyMywicGF0aCI6Ii85NDE1NDc4MC8yMzk3OTY4MTAtMWQzNWY0ZDEtMzEwNC00NGY0LThjNWMtMjY5ZDYxMWVhZWUyLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFJV05KWUFYNENTVkVINTNBJTJGMjAyMzEyMjQlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjMxMjI0VDE0NTg0M1omWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWIxYzU0ZGJkYTQ4MmI2ODlkOTE4MzlhODQ5NWE3ZjBjYjZjOWNmMjJiOWM5ZTYwZTZhM2JjZmQwNWEwN2M2MzImWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JmFjdG9yX2lkPTAma2V5X2lkPTAmcmVwb19pZD0wIn0.1Qf9nMvx81hQF53YUlSdV-JmWKyLiu19wmazfFZP1Nw)
![image](https://private-user-images.githubusercontent.com/94154780/239796837-13d30585-0c48-4b29-be60-57aa39e77fbf.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTEiLCJleHAiOjE3MDM0MzAzNzUsIm5iZiI6MTcwMzQzMDA3NSwicGF0aCI6Ii85NDE1NDc4MC8yMzk3OTY4MzctMTNkMzA1ODUtMGM0OC00YjI5LWJlNjAtNTdhYTM5ZTc3ZmJmLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFJV05KWUFYNENTVkVINTNBJTJGMjAyMzEyMjQlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjMxMjI0VDE1MDExNVomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTBlMTMyNDQzNDFmNGIxNDAwODQ0OTg1ZTM5ZWU3Yjk1YTY4ZTE3ZTI1YzRiYTI5MjgxYjNlYjMyNzMxNzIyNzcmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JmFjdG9yX2lkPTAma2V5X2lkPTAmcmVwb19pZD0wIn0.BI96dMbLj_bN2AUoCIan7gNHACOYlhIGrBp4xYdIscU)

## Program
```
import math
arr_time=float(input("Enter the mean inter arrival time of objects from Feeder (in secs): "))
ser_time=float(input("Enter the mean  inter service time of Lathe Machine (in secs) :  "))
Robot_time=float(input("Enter the Additional time taken for the Robot (in secs) :  "))
c=int(input("Number of service centre :  "))
lam=1/arr_time
mu=1/(ser_time+Robot_time)
print("--------------------------------------------------------------")
print("Multiple Server with Infinite Capacity - (M/M/c):(oo/FIFO)")
print("--------------------------------------------------------------")
print("The mean arrival rate per second : %0.2f "%lam)
print("The mean service rate per second : %0.2f "%mu)
rho=lam/(c*mu)
sum=(lam/mu)**c*(1/(1-rho))/math.factorial(c)
for i in range(0,c):
    sum=sum+(lam/mu)**i/math.factorial(i)
P0=1/sum
if (rho<1):
    Lq=(P0/math.factorial(c))*(1/c)*(lam/mu)**(c+1)/(1-rho)**2
    Ls=Lq+lam/mu
    Ws=Ls/lam
    Wq=Lq/lam
    print("Average number of objects in the system : %0.2f "%Ls)
    print("Average number of objects in the conveyor :  %0.2f "%Lq)
    print("Average waiting time of an object in the system : %0.2f secs"%Ws)
    print("Average waiting time of an object in the conveyor : %0.2f secs"%Wq)
    print("Probability that the system is busy : %0.2f "%(rho))
    print("Probability that the system is empty : %0.2f "%(1-rho))
else:
    print("Warning! Objects Over flow will happen in the conveyor")
print("--------------------------------------------------------------")
```

## Output :
![image](https://private-user-images.githubusercontent.com/94154780/239796920-d961ec39-3eb9-44d5-875b-375f5694d5df.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTEiLCJleHAiOjE3MDM0MzAzNzUsIm5iZiI6MTcwMzQzMDA3NSwicGF0aCI6Ii85NDE1NDc4MC8yMzk3OTY5MjAtZDk2MWVjMzktM2ViOS00NGQ1LTg3NWItMzc1ZjU2OTRkNWRmLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFJV05KWUFYNENTVkVINTNBJTJGMjAyMzEyMjQlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjMxMjI0VDE1MDExNVomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTBiYjcxYjRlNWE4ZWMxMDA3M2FlODZhMzQzMzc0NmVhZDU0MjJmMmMzMGQ3M2EwMzU0YjhmOWYzZDRjY2U0OTcmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JmFjdG9yX2lkPTAma2V5X2lkPTAmcmVwb19pZD0wIn0.ycOGjuP9nuK1EgPN7hm8h9mlWpzqxBIGjF53rz02Qu4)

## Result : 
Thus the average number of materials in the system and conveyor, waiting time of each material in the system and conveyor is found successfully.
