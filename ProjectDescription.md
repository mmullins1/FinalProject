# 2021 NFL Passing Statistics
Final project for J124
## Story Proposal
In my opinion, the most notable finding from my five questions is that touchdown percentage is the most indicative component of passer rating when compared to record, and that interception percentage is the least correlated. I would write a story about how to measure quarterback performance, and using the statistics I’ve found along with expert opinions I would seek to determine whether or not the metrics commonly used to evaluate passers are outdated. The quarterback is the most important player on the football field, and I think there is significant demand for new and up-to-date ways to evaluate performance and pinpoint what traits and approaches lead to wins with the most consistency. 

Two potential interview sources for this story would be Packers head coach Matt LaFleur and Rams head coach Sean McVay. Both of those coaches are younger coaches who are good with the media, and are reasonably open about explaining football concepts. More importantly, they coach the two quarterbacks with the highest touchdown percentages, Aaron Rodgers and Matthew Stafford. They may have some insight as to how they manufacture touchdown opportunities for their quarterbacks. A journalist with NFL media credentials could interview them at press conferences at their respective teams’ practices. A third 

Other data sources that could augment the article include the NFL Hall of Fame database, which could give me context for whether or not the trends I have noticed about 2021 apply to the historical greats of the NFL. A second additional data source would be the previous decade of passing data from Pro Football reference, which would be useful in illustrating if the trend is consistent with other years, and if there is a direction that these correlations are moving year-to-year.

## Data Visualization
![passer-s-touchdown-percentage-vs -winning-percentage (2)](https://user-images.githubusercontent.com/25110547/183278720-e979ae00-ad70-432b-81d0-6e6ee6c53a6b.png)
https://datawrapper.dwcdn.net/TBSY3/3/
![passer-s-interception-percentage-vs -winning-percentage](https://user-images.githubusercontent.com/25110547/183279629-0b60b4a5-8365-40bb-8de7-920b7f03ce61.png)
https://datawrapper.dwcdn.net/iEalG/3/

## The Data:
I used the 2021 NFL Passing statistics from Pro Football Reference as my data set.
## Cleaning the data:
I used OpenRefine to make the position category, which was missing some data, uniform.
I replaced numbers with formulas in certain fields to make sure I could reproduce the metrics included in the data.
I divided the data into several sheets to remove quarterbacks with too few pass attempts to merit consideration from the data set. The main dataset includes only players with 200+ pass attempts in the 2021 season.

## Questions to answer:
1. On average, did older or younger players have a higher passer rating?
2. Which of the four components of passer rating has the strongest correlation to QB record?
3. Do younger or older players take more sacks per dropback?
4. Which cumulative measurement for QB performance (QBR, Passer Rating, or ANY/A) has the greatest correlation with record?
5. Do volume stats or rate stats have a greater correlation with record?

## Question 1: On average, did older or younger players have a higher passer rating?
1. I found the median age of the quarterbacks with 200+ pass attempts using the median tool on Google Sheets.
2. I wrote two formulas to determine the average passer rating of quarterbacks under 27, and quarterbacks 27 and younger. The C column is age and the V column is passer rating. They are =ROUND(AVERAGEIF($C$2:$C,">27",$V$2:$V),2)and =ROUND(AVERAGEIF($C$2:$C,"<=27",$V$2:$V),2)
3. My formulas found that quarterbacks 27 and younger averaged a passer rating of 87.54, considerably less than the 94.84 that quarterbacks older than 27 averaged.

## Question 2: Which of the four components of passer rating has the strongest correlation to QB record?
1. I started by using the QB Record column (formatted as Wins-Losses-Ties) and the Games Started column to calculate a win percentage stat. To do so I needed to take the number of wins, (the numbers before the first “-”), and half the ties (the last number) and divide them by a QB’s number of starts. The formula I came up with was =ROUND((LEFT($G25,FIND("-",$G25)-1)+(RIGHT($G25,1)/2))/$F25*100,1)
2. I then used the CORREL function to find the Pearson’s Correlation Coefficient for the relationship between win percentage and each of the four components of passer rating. These components are completion percentage, yards per attempt, touchdown percentage, and interception percentage.
3. My findings were that touchdown percentage has a strong correlation with an r of 0.71, completion percentage and yards per attempt had a moderate correlation with scores of 0.625 and 0.527 respectively, and interception percentage had a weaker correlation with a score of -0.312.

## Question 3: Do younger or older players take more sacks per dropback?
1. For this question I used the same median cutoff as question 1. 
2. I wrote two formulas to determine the average sack percentage of quarterbacks under 27, and quarterbacks 27 and younger. The C column is age and the AA column is passer rating. They are =ROUND(AVERAGEIF($C$2:$C,">27",$AA$2:$AA),2)and =ROUND(AVERAGEIF($C$2:$C,"<=27",$AA$2:$AA),2)
3. I found that younger quarterbacks took sacks on an average of 6.83% of their dropbacks, higher than the 6.11% of older players.

## Question 4: Which cumulative measurement for QB performance (QBR, Passer Rating, or ANY/A) has the greatest correlation with record?
1. I was able to use the same win percentage column from question 2 to answer this  question.
2. Using the same CORREL formula as question 2, I found that ESPN’s Quarterback Rating (QBR) had the closest relationship to winning percentage of any of the metric’s tested that claim to evaluate overall quarterback performance.
3. The correlation coefficient numbers for each metric area as follows: QBR: 0.831, Adjusted Net Yards per Attempt: 0.73, Passer Rating: 0.714

## Question 5: Do volume stats or rate stats have a greater correlation with record?
1. My process for this question was very similar to questions number 2 and 4. I used the CORREL tool to find the Pearson’s Coefficient between two columns for winning percentage and the notable volume stats: touchdowns, interceptions, completions, and passing yards. I then compared their correlations to the per attempt versions of these statistics, as used in question 2.
2. The r values found were as follows: touchdowns: 0.719, yards: 0.629, completions: 0.547, interceptions: 0.1.
3. This means that the rate stats were better predictors of record in the case of completions and interceptions, but the total stats were more predictive in the case of touchdowns and yardage.

