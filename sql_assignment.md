
### Title : Sql Flight Assignment
### Naveen Kumar Sheela

#### Question 1
Print a passenger list for flight 3 on 4-1

SQL:
```
select name from passengers join pass_ticketed
 on passengers.passid=pass_ticketed.passid where pass_ticketed.fltno=3
  and pass_ticketed.date='4-1'
  
```
#### Answer:
```

name

Duck, Donald	
Wayne, John	
Mazurki, Mike	
Marvin, Lee	
Romero, Cesar	
Lamour, Dorothy	

```

#### Question 2
Print a passenger list for flight 5 on 4-2
SQL:
```
select name from passengers join pass_ticketed
 on passengers.passid=pass_ticketed.passid where pass_ticketed.fltno=5
  and pass_ticketed.date='4-2'
```




#### Answer:
```

name

Mouse, Mickey	
Moose, Bullwinkle	

```

#### Question 3
Print a list of all overbooked flights.
SQL:
```

```
#### Answer:
```
```


#### Question 4
Print a list of passengers with more than one ticket.
SQL:
```

select name,count(name) from passengers join pass_ticketed
 on passengers.passid=pass_ticketed.passid GROUP BY passengers.passid
HAVING COUNT( * ) >1
```
#### Answer:
```
name
count(name)

Simpson, Richard	3	
Halverson, Ranette	2	
Carpenter, Stewart	2	
Wayne, John	3	
Mazurki, Mike	2	
Marvin, Lee	3	
Lamour, Dorothy	2	
Mouse, Mickey	2	
Duck, Donald	2	
Moose, Bullwinkle	2	

```


#### Question 5
Print a list of passengers with more than one ticket on the same day.
SQL:
```

SELECT name
FROM passengers
JOIN pass_ticketed ON passengers.passid = pass_ticketed.passid
GROUP BY passengers.passid
HAVING COUNT( passengers.passid )>1
```
#### Answer:
```

name

Simpson, Richard	
Halverson, Ranette	
Carpenter, Stewart	
Wayne, John	
Mazurki, Mike	
Marvin, Lee	
Lamour, Dorothy	
Mouse, Mickey	
Duck, Donald	
Moose, Bullwinkle	

```

#### Question 6
Print a list of flights that use aircraft N173WY.
SQL:
```

select distinct flights.fltno from flights join aircraft_assignments on
 flights.fltno=aircraft_assignments.fltno where aircraft_assignments.acno='N173WY'
```
#### Answer:
```
fltno

2	
5	
1	
4	

```



#### Question 7
Print a list of pilots who fly on April 1.
SQL:
```

select name from pilots 
join pilot_assignments on pilots.pilotid=pilot_assignments.pilotid
where pilot_assignments.date = '4-1'
```
#### Answer:
```
name

Wright, Orville	
Post, Wiley	
Lindergh, Charles	
Yeager, Chuck	
Wright, Orville	
Post, Wiley	
Lindergh, Charles	

```

#### Question 8
Print a list of pilots who fly on both days.
SQL:
```

select name from pilots 
join pilot_assignments on pilots.pilotid=pilot_assignments.pilotid
where pilot_assignments.date = '4-1' or pilot_assignments.date = '4-2'
```
#### Answer:
```

name

Wright, Orville	
Post, Wiley	
Lindergh, Charles	
Yeager, Chuck	
Lovell, James	
Wittman. Steve	
Boyington, Greg	
Hoover, Bob	

```

#### Question 9
Print a list of pilots who have two flights on the same day.
SQL:
```

```
#### Answer:

#### Question 10
Print a List of flights that do not have a complete crew.
SQL:
```

```
#### Answer:

#### Question 11
Print of list of flights where destination is DFW.
SQL:
```

SELECT distinct fltno from flights where destination='DFW'
```
#### Answer:
```
fltno
4
5
6

```
#### Question 12
Print a list of flights where origin or destination is LAX
SQL:
```

SELECT  fltno from flights where origin='LAX' or destination='LAX'
```
#### Answer:
```

fltno

3	
6	
3	

```
#### Question 13
Print the origin and destination of flights with passenger equals Duck, Donald or Wayne, John.
SQL:
```

select distinct origin,destination from flights join passengers 
join pass_ticketed on flights.fltno=pass_ticketed.fltno 
and passengers.passid=pass_ticketed.passid 
where passengers.name='Duck, Donald' or passengers.name='Wayne, John'
```
#### Answer:
```

origin
destination

DFW	LAX	
LAX	DFW	
ORD	DFW	
DIA	DFW	

```
#### Question 14
Print a list of flight numbers and origins.
SQL:
```

SELECT distinct fltno,origin from flights
```
#### Answer:
```

fltno
origin

1	DFW	
2	DFW	
3	DFW	
4	DIA	
5	ORD	
6	LAX	

```
#### Question 15
Print a list of aircraft types from equipment assigned where pilot number=1030.
SQL:
```

select distinct type from aircraft join aircraft_assignments
 join pilot_assignments on aircraft.acno=aircraft_assignments.acno and
  aircraft_assignments.fltno=pilot_assignments.fltno where 
pilot_assignments.pilotid=1030
```
#### Answer:
```
type

B-18	
C-172	

```
#### Question 16
Print a list of pilots who fly with at least two other pilots.
SQL:
```

```
#### Answer:
```
```
#### Question 17
Print a list of pilots who fly only one type of plane.
SQL:
```

select name from pilots join pilot_assignments
 on pilots.pilotid=pilot_assignments.pilotid
  group by pilots.name having count(pilot_assignments.pilotid)=1
```
#### Answer:
```

name

Boyington, Greg	
Hoover, Bob	

```












#### Question 18
Print a list of passengers booked on flights assigned to pilot=1030.
SQL:
```

select distinct name,passengers.passid from passengers 
join pass_ticketed join pilot_assignments on passengers.passid=
pass_ticketed.passid and pass_ticketed.fltno = pilot_assignments.fltno 
where pilot_assignments.pilotid=1030
```
#### Answer:
```
 
Simpson, Richard	1001
 
Halverson, Ranette	1002
 
Griffin, Terry	1004
 
Bunny, Bugs	1103
 
Carpenter, Stewart	1003
 
Wayne, John	1011


```
#### Question 19
Print a list of pilots assigned to fly plane=N35A.
SQL:
```

SELECT name
FROM pilots
JOIN pilot_assignments
JOIN aircraft_assignments ON pilot_assignments.fltno = aircraft_assignments.fltno
AND pilot_assignments.pilotid = pilots.pilotid
WHERE aircraft_assignments.acno = 'N35A'
```
#### Answer:
```

name

Wright, Orville	
Post, Wiley	
Lindergh, Charles	
Lovell, James	
Wittman. Steve	

```


