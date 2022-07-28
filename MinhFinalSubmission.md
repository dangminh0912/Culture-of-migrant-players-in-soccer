### Name: Minh Nguyen

### DA 245-01: Intro Cultural Analytics

### Instructor: Matthew Lavin

### May 4, 2022

<h1 align="center">The culture of migrant players in soccer</h1>

## 1. Introduction

&emsp; Soccer is one of the most favorite sports in the world and became a part of the global culture during the 1990s (Time, 2004). Some of the outstanding players were recruited by the team in another country, or simply, wanted to play in a more competitive environment to challenge themselves. The research question I want to focus on is that does the performance of the migrant or native players better when playing in England. The migrant players are the people have the nationality from a specific country except England; the native players are the people have the nationality from England.

&emsp; I will use the data from the Premier League, which is the top level of the English football league system consisting of 20 teams. The reason why Premier League an ideal soccer league to collect and analyze data is because it is a home to some of the most famous clubs, players, managers and stadiums in world soccer. The Premier League known as the most-watched league with one billion homes watching the action in 188 countries (Premier League). Here is the list of 20 teams in the season 2021-2022: Arsenal, Aston Villa, Brentford, Brighton and Hove Albion, Burnley, Chelsea, Crystal Palace, Everton, Leeds United, Leicester City, Liverpool, Manchester City, Manchester United, Newcastle United, Norwich City, Southampton, Tottenham Hotspur, Watford, West Ham United, Wolverhampton Wanderers.

&emsp; By comparing the migration to the England players from premier league teams, I will use the quantitative approach to analyze personal statistics, and evaluate the performance based on the nationality of the players. For the hypothesis, I think the performance of the native players is better than the migrant players. The native players have a better communication skills and acquaint with the environment in England more than anyone else. The outstanding number of England players in the League indicates that the communication and adaptation to the gameplay are the two most important factors to remain in an England team as an international player.

## 2. Methods and Data

&emsp; The folder "team_player.html" contains the information of all the players from the 20 teams in the season 2021-2022. I collected these data from each club’s page source in Premier League and they are all in the HTML format. On the web page, the stats of the players are updated right after the match ended, and the transfer period to change the players is updated instantly in the team’s squad. Until now, the season 2021-2022 is continuing and it will be ended after the match week 38. The data I used to analyze from each team is before the match week 36 and the Premier League does not have a play-off at the end of the regular season. Therefore, it does not make any significant impact on the training model.

&emsp; Because each of the HTML files has the information of individual players in a particular team, I want to use these variables for the analysis: Name, Position, Nationality, Appearances, Clean Sheets, Goals, and Assists. However, some of the players have the clean sheets stats but not the goals stats, and vice versa. By identifying the positions of players in each club, I realize that every position has information on the Nationality and Appearances. There is 4 distinct position in soccer: GoalKeeper, Defender, Midfielder, and Forward. The GoalKeeper has the stats of Clean Sheets; the Defender has the stats of Clean Sheets and Goals; the Midfielder and Forward both have the stats of Goals and Assists. I know that I cannot take all of these variables for the analysis because some of the positions have a much lower number of migrant players compared to the England players, thus, it will affect the training model. By determining which variables to use, I calculated the role that has the most migrant players. Depending on the analysis, Midfielder has the most international players, so the Appearances, Goals, and Assists will be taken into consideration. The independent variables I used to predict the dependent variables are Appearances, Goals, and Assists; the dependent variable for the prediction is Nationality.

![Data Table](https://github.com/HumanitiesAnalytics/individual-research-project-final-dangminh0912/blob/1c3a4f21328d07006c7ec648d0e51308b29fd2e0/Images/Data%20Table.png)

&emsp; Because each of the files is in the HTML format, I have to use the Web-scraping method and convert from the HTML to the DataFrame. Before I have the DataFrame, I need to convert it from HTML to a list of lists. The BreautifulSoup library is an ideal library for conversion. It accesses my folder and finds all of the attributes and values related to the variables that I was looking for to analyze. These attributes are name, position, and playerCountry. The other common attribute is label, which contains the value of my independent variables. Therefore, I have to use the text method from the BeautifulSoup library to find all the text that is similar to the name of independent variables. For each value I got from the attributes, I appended it to the list that is corresponded to a player. Finally, the list of lists has a length equal to the number of players in the league because each element in the list is the information of a player. Then, I converted the list of lists to the DataFrame; the function that did all of the processes is called “convertFile”.The column of the DataFrame includes the Name, Position, Nationality, Appearances, Clean Sheets, Goals, and Assists; the row includes all of the players in the league.

&emsp; To answer the research question: “Does the performance of the migrant or native players better when playing in England? ”, the performance depends on the Appearances, Goals, and Assists in the season 2021-2022. The Clean Sheets will not be used because this variable depends a lot on the performance of the team rather than the individual player. I trained the logistic regression model to predict if the player is from England or not. I used the logistic regression model because the independent variables are discrete; the dependent variable is binary. I separated into 3 different train-test sets using sklearn train_test_split. All of the train-test sets have the training sets with a size of 75% and test sets with a size of 25%. However, the X_train, X_test, y_train, y_test all have a one-dimensional array, so I have to use the np_arr function to convert it from a one-dimensional array to a two-dimensional array. This function converts X_train, X_test, y_train, y_test from series to NumPy array (using NumPy library), and eventually reshapes them. From the Sklearn LogisticRegression library, I can fit the model based on the training sets and get the score based on the test sets. Then, I plotted the logistic regression model using the seaborn library for better visualization. Each train-test set will have a corresponding visualization.

&emsp; The next method I utilized to answer the research question is by using the PMI (Pointwise Mutual Information). The PMI allows me to measure the association between the number of international players with England players. The higher PMI means they have a high association and vice versa. By knowing the relationship between the two countries (PMI), I can evaluate the communication and adaptability of the migrant players while playing soccer in England. The PMI(x,y) such that x is a country other than England and y is England is calculated based on this formula:

![PMI Formula](https://github.com/HumanitiesAnalytics/individual-research-project-final-dangminh0912/blob/student/Images/PMI%20Formula.png)

Source: (Eran Raviv, 2020)

To be more specific, p(x,y) is the probability of a team that has both x and y (co-occurrence); p(x) is the probability that the players are from country x; p(y) is the probability that the players are from England.

## 3. Results

&emsp; To understand how the the performance of migrant players different from the England players, I utilize the logistic regression model to predict the nationality . At the beginning, I hypothesized that the performance of the native players is better than the migrant players. The number of match that the players participate (appearances) has a huge impact on the nation they are from. I separate the logistic regression model into 3 parts. The first one used the Appearances as the independent variable to predict the Nationality (dependent variable). The model yielded 65% accuracy, which is not a high accuracy.

![Appearances](https://github.com/HumanitiesAnalytics/individual-research-project-final-dangminh0912/blob/e9c1859bd68cfd0cb0ac4ba8064f57c7f2d4dc13/Images/Appearances.png)

&emsp; Looking at the regression plot, the line is not the S-Curve. In my perspective, the sample size is too small to predict dependent variable. The more “Appearances” indicates the lower Y-values, which is the higher number of matches participated demonstrate the higher probability that it is the migrant players.

&emsp; The second model used the Goals as the independent variable to predict the Nationality (dependent variable). The model yielded 62% accuracy, which is not a high accuracy. It is lower than the Appearances because only 3 positions (Defender, Midfielder, Forward) are considered to train the model.

![Goals](https://github.com/HumanitiesAnalytics/individual-research-project-final-dangminh0912/blob/e9c1859bd68cfd0cb0ac4ba8064f57c7f2d4dc13/Images/Goals.png)

&emsp; Looking at the regression plot, the line is not the S-Curve. In my perspective, the sample size is too small to predict dependent variable. The more “Goals” indicates the lower Y-values, which is the higher goals demonstrate the higher probability that it is the migrant players.

&emsp; The third model used the Assists as the independent variable to predict the Nationality (dependent variable). The model yielded 58% accuracy, which is not a high accuracy. It is even lower than the Appearances and Goals because only 2 positions (Midfielder, Forward) are considered to train the model.

![Assists](https://github.com/HumanitiesAnalytics/individual-research-project-final-dangminh0912/blob/e9c1859bd68cfd0cb0ac4ba8064f57c7f2d4dc13/Images/Assists.png)

&emsp; Looking at the regression plot, the line is not the S-Curve. In my perspective, the sample size is too small to predict dependent variable. The more “Assists” indicates the lower Y-values, which is the higher assists demonstrate the higher probability that it is the migrant players. Overall, the higher stats (Appearances, Goals, Assists) indicate the higher probability that it is the migrant players. The smaller the sample size, the lower the accuracy of the model yielded. PMI allows me to measure the association between the number of international players with England players. Based on the graph all of the countries, except for Portugal, has the positive PMI. It means that a team has co-occuring in a frequency higher than individual country. The top 5 countries have the highest PMI are Mexico, Slovakia, Cote D’lvoire, Serbia, and Tunisia. Since they had a high relationship with England, they have a better communication and adaptability than other countries while playing in Premier League.

![PMI Stats](https://github.com/HumanitiesAnalytics/individual-research-project-final-dangminh0912/blob/student/Images/PMI%20stats.png)

## 4. Discussion

&emsp; For the research question, I want to know if the performance of the migrant or native players is better when playing in England. Then, I hypothesized that the performance of the native players is better than the migrant players because they have better communication skills and acquaint with the environment in England. By using the logistical regression to predict the country, all of the independent variables that have been utilized to demonstrate the ability to play in the Premier League of migrant players exceeded my expectation. Although the model yielded a normal accuracy (from 58%-65%), the regression plot showed that the higher the independent variable, the higher probability that it is the migrant players. However, the logistic regression plot seemed to be linear, and I think it was due to the sample size. With only 654 samples, the plot indicated that these variables are continuous.

&emsp; At first, I tried to use linear regression to predict the number of goals/assists based on the appearances, but the model generated only 32% of accuracy. By changing the method and focusing on predicting the country, the model improves significantly. If I collected the data from the previous season to analyze, the accuracy of the model can be much better. The sample size will be larger and the visualization will be more correct. Looking back to the research question and the logistic regression, I can tell that the performance of the migrant is better than the England players when playing in England.

&emsp; In the PMI table, the top 5 countries have the highest PMI are Mexico, Slovakia, Cote D’lvoire, Serbia, and Tunisia; the countries with the lowest PMI are Ecuador, Brazil, Denmark, Nigeria, and Portugal. However, by counting the number of players in Mexico and Portugal (Highest PMI and Lowest PMI), Portugals have much more players than Mexico. Therefore, the country with a higher PMI does not mean the number of players in that country who played in the Premier League is more than the country with a lower PMI. Because Mexico or any top PMI country has a higher co-occurring frequency, they tend to play in the same team. Therefore, they will not be hindered in communicating, and easier to adapt to the environment while playing in England. In conclusion, the more associations a country has with England, the better they communicate and adapt to the environment, thus, the performance can be improved significantly.

## 5. References

Premier League Clubs â Fixtures, Results, Stats & Profiles. (n.d.). Premier League. https://www.premierleague.com/clubs

Križaj, J., Leskošek, B., Vodičar, J., & Topič, M. D. (2016). Soccer Players Cultural Capital and Its Impact on Migration. Journal of Human Kinetics, 54(1), 195–206. https://doi.org/10.1515/hukin-2016-0052

Premier League Competition Format & History | Premier League. (n.d.). Premier League. https://www.premierleague.com/premier-league-explained#:%7E:text=The%20league%20takes%20place%20between,winning%20the%20Premier%20League%20title.

Understanding Pointwise Mutual Information. (2020, January 26). Eran Raviv. https://eranraviv.com/understanding-pointwise-mutual-information-in-statistics/
