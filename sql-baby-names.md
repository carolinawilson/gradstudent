## Using SQL to find the history of my name 
### Due: Oct. 16, 2014 

**Using the ssa_baby_names table**

1. In the year 2013, find out how many babies had your name: **701**
    
SELECT Name, SUM(count)
FROM ssa_baby_names
WHERE Name='Carolina' AND Year = '2013'



2. Find the highest-rank (and the year) that your name has achieved among baby names: **rank, 9008 / year, 1996**

SELECT Name, Year, MAX(rank)
    FROM ssa_baby_names
    WHERE Name='Carolina'
    
    
    
3. Between the years 1980 and 2013, find how many babies in total have been listed by the Social Security Administration in this data: **126036079**  

SELECT SUM(count)
    from ssa_baby_Names
    
    
    
4. Find out how many babies (roughly) have had your name from 1980 to 2013: **28707**

SELECT SUM(count)
    from ssa_baby_Names
    WHERE name='Carolina'
    
    
    
5. Find the year that had the most male babies born: **68740, 1981**

SELECT Year, MAX(count)
    from ssa_baby_names 
    WHERE sex="M"
    GROUP BY Year
    
    
    
6. Find the year in which your name had the highest increase in names-per-100k-babies born: **14, 1989** (This is really funny because I was born in 1991, and I remember girls 1-2 years older than me having my name in school). 

SELECT Year, MAX(per_100k_change)
  from ssa_baby_names 
  WHERE name="Carolina"
  GROUP BY Year
  
  
  
7. Find the year in which your name had the highest decrease in names-per-100k-babies born: **-10, 2007**

SELECT Year, MAX(per_100k_change)
from ssa_baby_names 
WHERE name="Carolina"
GROUP BY Year



8. Make a line chart showing how your name has changed in popularity over the years

SELECT Name, Year, SUM(count)
FROM ssa_baby_names
WHERE name="Carolina"
GROUP BY Year


![image_sql](http://i.imgur.com/KvDDPWm.png)
![image_linechart](http://i.imgur.com/z5Z58Hc.png)



9. Find out who in our class had the most popular baby name in 1980: **Jessica, 34,045**

- Phoebe - 84
- Sabrina - 2,784
- Laura - 12,974
- Alexandra - 885
- Farida - 0
- Liam - 112
- Jay - 2,008
- Allison - 4,896
- Austin - 1,199
- Yuqing - 0
- **Jessica - 34,045**
- Sean - 7,645
- Ariha - 0
- Katharine - 571
- Mary - 11,525
- Carolina - 458
- Maren - 159
- Daniel - 30,108 *(you're right behind Jessica!)*

10. Find out who in our class had the most popular baby name in 2013: **Liam, 18,023**

- Phoebe - 1,050
- Sabrina - 1,120
- Laura - 1,006
- Alexandra - 3,494
- Farida - 27
- **Liam - 18,023**
- Jay - 761
- Allison - 5,416
- Austin - 6,545
- Yuqing - 0
- Jessica - 1,935
- Sean - 2,194
- Ariha - 0
- Katharine - 109
- Mary - 2,602
- Carolina - 701
- Maren - 21
- Daniel - 14,167 *(taking second place, again!)*

11. Find out who in our class has the name that the most babies throughout U.S. history have *(I'm only going to do from 1980-2013..........)* 
**And the winner is....DANIEL with 884,599** 


![most popular baby name](http://i.imgur.com/pDKb4Pc.png)




**Using the ssa_baby_names_by_state table**
*For this section, pick a adoptive state if you were not born in the U.S.*

1. In your home state, find out how many babies had your name in the year that you were born: **90**

SELECT Name, SUM(count)
FROM ssa_baby_names_by_state
WHERE Name="Carolina" AND Year="1991" AND State="FL"

2. In your home state, find out how many babies had your name in 2013: **58**

SELECT Name, SUM(count)
FROM ssa_baby_names_by_state
WHERE Name="Carolina" AND Year="2013" AND State="FL"

3. Find the state in which your name is the most popular in 2013: **Texas, 153**

SELECT Name, State, SUM(count)
FROM ssa_baby_names_by_state
WHERE Name="Carolina" AND Year="2013" 
GROUP BY State


4. Find the state in which your name is least popular (but still registers, i.e. has a minimum of 5 babies) in 2013: **Arkansas, Kansas, New Mexico, Utah -- all with 5**


5. Make a line chart with two lines:
  - **The popularity of your name in your home state**
  
![image](http://i.imgur.com/FwLnYeq.png)

SELECT Name, Year, SUM(count)
FROM ssa_baby_names_by_state
WHERE Name="Carolina" AND State="FL"
GROUP BY Year



  - **The popularity of your name in California**
  
![image2](http://i.imgur.com/nHLgkxl.png)

SELECT Name, Year, SUM(count)
FROM ssa_baby_names_by_state
WHERE Name="Carolina" AND State="CA"
GROUP BY Year

