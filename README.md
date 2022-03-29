# worldcup2018

Dataset taken from https://www.kaggle.com/datasets/sohommajumder21/fifa-2018-world-cup-players
Additional data taken from https://en.wikipedia.org/wiki/2018_FIFA_World_Cup#Group_stage
Dataset contains data of players that competed in the 2018 World Cup

Goals:
1) Is there a correlation between height and position?
2) Does the team's average age affects the team's performance?
3) What were the top 5 leagues in terms of how many players who participated in the tournament?

Solutions:
1) Using SQL:
  SELECT position, AVG(height) AS avg_height FROM `panoply.sheets_worldcup18_all_wc_18_players_fifa`
GROUP BY position;
  
  <img width="1169" alt="Screen Shot 2022-03-28 at 6 44 14 PM" src="https://user-images.githubusercontent.com/102564831/160515783-1ad6f0db-e1e3-4db9-bebf-0ae5f80c7faa.png">

Average height for: 
Goalkeepers (GK): 188.79cm
Defenders (DF): 183.18cm
Midfielders (MF): 179.64cm
Forwards (FW): 181.39cm

Conclusion: Goalkeepers tend to be significantly taller than other positions. This is most likely due to the extra reach that height offers which helps players block shots. Difference between the other three positions are about 2cm each with defenders being the tallest; most likely due to the physicality height offers that helps with defending against players. Midfielders are statistically the shortest position, most likely due to amount of ground they need to cover compared to other positions.

2) SELECT team, AVG(age) as avg_age FROM `panoply.sheets_worldcup18_all_wc_18_players_fifa`
  GROUP BY team
  ORDER BY avg_age ASC
  
 Average age:
1 Nigeria 25.964860036
2 France 26.030136986
3 England 26.050506254
4 Tunisia 26.526742108
5 Serbia 26.761048243
6 Germany 27.139130435
7 Denmark 27.143776057
8 Switzerland 27.18308517
9 Senegal 27.184157237
10 Iran 27.231328171
11 Morocco 27.234067898
12 Peru 27.440381179
13 Belgium 27.585586659
14 South Korea 27.786063133
15 Croatia 27.903394878
16 Colombia 28.064800476
17 Uruguay 28.131268612
18 Australia 28.134842168
19 Sweden 28.237045861
20 Poland 28.311375819
21 Portugal 28.365932102
22 Spain 28.488028588
23 Japan 28.580226325
24 Iceland 28.583442525
25 Brazil 28.604526504
26 Saudi Arabia 28.730434783
27 Russia 28.838356164
28 Egypt 28.981298392
29 Argentina 29.217153067
30 Panama 29.263609291
31 Mexico 29.362954139
32 Costa Rica 29.557593806

Conclusion: The World cup winners, France, had the second lowest average age in the tournament. However, Croatia, the other finalist had 15th lowest average age in the tournament. In addition, Belgium and England made it to the semi-finals, having the 3rd and 13th lowest average age, respectively. However, Nigeria, which has the lowest average age, failed to qualify for the knockout tournament. Furthermore, Tunisia and Germany, being the 4th and 6th youngest team, also failed to qualify for the knockout stage. In conclusion, there is no clear correlation between the average age of teams and their performances in the tournament.
  
  
3) SELECT league, COUNT(league) AS players FROM `panoply.sheets_worldcup18_all_wc_18_players_fifa`
    GROUP BY league
    ORDER BY players DESC
    LIMIT 5;
    
   1 ENG 124
   2 ESP 81
   3 GER 67
   4 ITA 58
   5 FRA 49
   
Conclusion: The English league, The Premier league, produced the most amount of players in the 2018 FIFA World Cup. This shows that many world class soccer players tend to play in the Premier league, which suggests that this league is the most competitive one in the world. The gap between England and Spain is much larger than the gap between Spain and Germany, which portrays the striking prominence and the elite level of competition in the Premier league.
            
