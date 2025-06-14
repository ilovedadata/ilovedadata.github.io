# Hi everyone 👋, I am ilovedadata, I am a developer and I LOVE diving into data and programming 💻.
This website is about some of the projects that I completed and the skills that I learnt in my **neverending** journey to become a better dev✌️. [Wanna loop through some cool plots?](#plotnr1) 

# Index
* [A powerball simulator](#italian-superball-simulator-) 
* [Funky scraped stats](#funky-stats-about-naruto-) 
* [House inventory fallout terminal](#house-terminal-inventory-system-) 
* [My take on an introduction to statistical learning](#my-take-on-an-introduction-to-statistical-learning)
* [My solutions to a (pretty challenging) 8 week SQL challenge](https://github.com/ilovedadata/8-Week-SQL-Challenge)
* I'm often studying (Hard) algorithms and data structures. Take a sneak peek at my code 👉 [here](https://github.com/ilovedadata/My-take-on-leetcode-blind-75)
* [Accelerating montecarlo simulations using neural networks](#speeding-up-montecarlo-simulations-using-neural-networks-%EF%B8%8F%EF%B8%8F%EF%B8%8F%EF%B8%8F)
* 💥NEW💥 [Rolling the dice on Wall Street: building and optimizing a portfolio simulator](#building-and-optimizing-a-portfolio-simulator-)

# Italian Superball simulator 💸 
`#Python` `#DataScience` `#DataAnalysis` `#Numpy` `#Pandas` `#Matplotlib` `#Statistics` `#Probability` `#Random`

[Index](#index) | [Next project](#funky-stats-about-naruto-) 

#### Project description and goal
The project is about the **"Italian powerball" (superenalotto)**, a game in which 8 numbers are drawn and prizes are won depending on how many numbers you guessed right. 7 numbers make up the "standard" ticket the user buys (6 numbers + the so-called **jolly number**, allowing you to score a particular combination: the "5+1"), the eighth number is the so-called **superstar number** and can be purchased at an additional 0.50$. The **goal** of this project is to create a realistic game simulator which takes into account the probabilities associated with the wins and the amount of money spent/gained. Thanks to the use of **Data science/Data analysis tools**, dataframes were created to store the drawings and interesting stats about the game were analyzed and plotted, in order to answer a simple question: `can I win big at the lottery?`

#### Code structure
The code is made up by 5 main sections:
* **Inputs Section**

   the **parameters** for the drawings are initialized, namely: the amount of numbers that can be drawn, the number of tickets played by the user and the number of drawings in which the user wants to play his number of tickets;
   
   Finally, the user is asked whether he wants to play a **superstar number** or not.

* **Functions section**:

   the **dollars function** returns an amount of dollars given a number;
   
   the **binomial coefficient** function is needed to compute the probability of scoring 0 or 1 without a Superstar number (these probabilities are not provided on the official Superenalotto website);
   
   the **spent/won function** returns the amount of money a user spends and wins given the times he plays and whether he plays a Superstar number or not.
   
   the **luck function** returns whether or not the user has been lucky when playing superenalotto.
   
* **Structures section**
 
   **two dictionaries** are created to store the drawings count: the first dictionary is needed to count how many times a combination is drawn without considering the superstar number whilst the second dictionary counts the times a combination is drawn considering the superstar number. Obviously, the second dictionary will get values > 1 only when the user plays a superstar number. These two dictionaries will be used later on to create a dataframe (a fourth one, in addition to the ones we will speak about in a few lines) that will count the times a combination was drawn as well as some probabilities about the combinations drawings. The following table represents the structure of the dataframe.
   
   | Combination | Wins_no_superstar | Wins_w_superstar | Act_Prob_no_superstar | Theo_Prob_no_superstar | Act_Prob_w_superstar | Theo_Prob_w_superstar |
   | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
   | 6   | 0 | 0 | 0 | 1,6e-9 | 0 | 1,8e-11 |
   | 5+1 | ... | ... | ... | ... | ... | ... |
   | ...   | ... | ... | ... | ... | ... | ... |
   
   **three dataframes** are created to store different data: the first stores the probabilities and the prizes associated to a combination drawing. The bigger the prize the lower the probability of winning and... wanna hear a (not so) **crazy stat**? `19/20 times you are going to lose`. 
   
   | Combination | Prize_no_superstar | Prize_w_superstar | Prob_no_superstar | Prob_w_superstar |
   | ------------- | ------------- | ------------- | ------------- | ------------- |
   | 6   | 200000000 | 202000000 | 1,6e-9 | 1,8e-11 |
   | 5+1 | 311000 | ... | ... | ... |
   | ...   | ... | ... | ... | ... |
   
   The second dataframe (in fact, there are two different dataframes that serve this purpose) is needed to store the numbers as they are drawn as well as whether you won or not. 
   
   | Drawn Numbers | Your Numbers | Drawn Jolly | Your Jolly | Drawn Superstar | Your Superstar | Won? |
   | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
   | 1,2,3,4,5,6 | 1,2,3,4,5,6 | 16 | 18 | 16 | 18 | ... |
   | ... | ... | ... | ... | ... | ... | ... |
   
   The third dataframe counts the times a number is drawn as "normal" number, as a Jolly or as a Superstar.
   
   | Numbers | Number | Jolly | Superstar |
   | ------------- | ------------- | ------------- | ------------- | 
   | 1 | 20 | 8 | 2 |
   | ... | ... | ... | ... |
   | 80 | 50 | 60 | 2 |
   
* **Script section**

   The script section is where the **magic** happens. Every ticket played by the user is compared to the drawn numbers. Both the user's ticket and the drawn numbers are **randomly** generated and, once they are compared, they are stored inside the dataframes created before so as to store data to generate **interesting plots** (I mean, who doesn't love plots?).  

* **Plotting section**

   Speaking of plots, the two histograms that follow store information about the times a user hit a combination and the frequency with which a number is drawn. As stated before, the "higher" the combination, the higher the prize won, the lower the probability that combination is drawn.
  
###### plotnr1
  
[Index](#index) | [More plots](#plotnr2) 
   ![Figure_1](https://user-images.githubusercontent.com/106730909/216787470-9213e1fb-1553-4c15-9671-846cd141eb38.png)

   As a design choice, combinations from "2" upwards are shown, even though, when playing superstar, the user can win scoring just 1 or 0. Nonetheless, when computing the amount of money won by the user, such combinations (0+superstar, 1+superstar) are taken into account. Furthermore (and since it took me quite a bit of time it's only fair I state it 👀) a custom labelling process has been implemented in order to label the histogram plot on the left exactly above each and every histogram column, respecting the color palette. For what concerns the plot on the left, it will be useful to draw some conclusions. The plot on the right shows that no clear patterns are present in the drawing of numbers (which is random!), something that has been confirmed during the different simulations I performed.

#### Conclusion

In order to draw some conclusions, let us analyze the plot on the left. This plot represents the "average" situation I found when playing with this simulator: a **lot** of times the user wins minor prizes (such as 2 or 3), rarely he scores a "4" (it happened to me at most 3 times during a simulation whilst playing the same amount of schedine we played in this simulation: needless to say, even scoring 3 "4" is not enough to cover the tickets expenses). In addition, in my experience the user never scored a 5 or a 6 and he/she never gained money: the amount of money spent on tickets has always been higher than the one gained through prizes. This becomes even more impressive when you consider the following: the plots above have been computed for a non-realistic (at least, I hope) situation: `a user that plays 70 tickets 3 times a week for a year, spending almost 17000$ in tickets, losing 12000$. What is even more crazy is that this user has been lucky: according to statistics, the times the user won (approx 0.06%) are higher than the ones he should have (approx 0.05%)`. 
This shows how unrealistic the expectation of winning big (or even winning small!) at the lottery is!

#### Possible future developments
The structures and scripts used in this project can possibly be used in the future to simulate other kinds of gamble games/casino games. One such application could be creating a simulator for the "true" Powerball (i.e. the American one) or the roulette game.

#### Sources
- `The data regarding probabiities and prizes come from the official superenalotto website at https://www.superenalotto.it/quanto-si-vince/calcolo-probabilita` 
## 

# Funky Stats about Naruto 🦊
`#Python` `#DataScience` `#DataAnalysis` `#Numpy` `#Pandas` `#Matplotlib` `#Statistics` `#HTML` `#ReverseEngineering` `#BeautifulSoup`
 `#Japanese` 

[Index](#index) | [Next project](#house-terminal-inventory-system-) 

#### Project description and goal
The project is about **Naruto**, a Japanese Anime that follows the adventure of Naruto, a young Ninja from Konoha, in his quest to become Hokage. The data for this project is about the episodes of Naruto, not including the Naruto Shippuden ones. The **goal** of this project is to practice my **web scraping, data analysis and data visualization skills** by answering the `following questions`: 
- 1 What is the highest delta episodes between first and last appearance of a given character?
- 2 What is the most present Naruto character throughout the Anime?
- 3 What is the most used japanese kanji in the japanese voice actors names?
- 4 Are there Naruto characters who have been dubbed by more than a dubber? (consider the most present 50 characters)
- 5 What is the episode with the most characters? Make a top and a flop 10!
- 6 What is the most present word in Naruto plots? Exclude English stopwords and punctuation signs

#### Code structure
* **Links scraping section**

   The idea of this section is to scrape the following webpage https://naruto.fandom.com/wiki/List_of_Animated_Media in order to create a dataframe containing the links to each and every naruto episode webpage, from which to extract the information needed to answer the questions above (the links are obtained by using beautiful soup to get the `href elements` of the HTML webpage). The dataframe is structured as follows:
  
   | Index | Naruto_Episode_link | # |
   | ------------- | ------------- | ------------- | 
   | 0 | /wiki/Enter:_Naruto_Uzumaki! | 1 |
   | ... | ... | ... |
   | 219 | /wiki/Departure_(episode) | 220 |

   It is worth noticing that Boruto and Naruto Shippuden episodes are also present at the link above: they have been stored as well in two dataframes identical to the one above, so as to be available for future developments regarding this project.

* **Episodes scraping section**

   This section makes use of reverse engineering in order to scrape the contents of the links to each and every naruto episode webpage. In order to access the webpages, it is worth noticing how the links to them are structured:
  
   _https: //naruto . fandom . com/_ **wiki/Homecoming_(episode)**

   _This is the static part_ and **this is the dynamic part**, doesn't this ring a bell? Looking at the dataframe of the link scraping section: we will need to loop through the "Naruto_Episode_link" column in order to visit each and every webpage and get the elements we are interested in, by inserting the strings we find there in the **dynamic** part of our link. 

    The data we are interested in, at this stage, is the one that is found under the "Credits" section at the webpages of the episodes. Coding a webscraper has been one of the most challenging parts of this projects, as, in fact, not all the webpages have exactly the same structure. In the end, this is the dataframe we are left with:
  
   | Index | Character | Jap_dub_eng_char	| Jap_dub_jap_char |	Eng_dub | # |
   | ------------- | ------------- | ------------- | ------------ | ------------ | ------------ | 
   | 0 |	Naruto Uzumaki | Junko Takeuchi | 竹内 順子 |	Maile Flanagan |	1 |
   | 1 |	Sasuke Uchiha | Noriaki Sugiyama | 杉山 紀彰 |	Yuri Lowenthal | 1 |
   | 2 |	Sakura Haruno | Chie Nakamura | 中村 千絵 |	Kate Higgins |	1 |
   | ... | ... | ... | ... | ... | ... |
   | n | ... | ... | ... | ... | 220 |

    This dataframe stores one row for each character present in a given episode. For instance: if Naruto Uzumaki is present in both the first and the last episode, we will find the Character "Naruto Uzumaki" both at # = 1 and at # = 220. Furthermore, each episode (#) has as much rows as the number of characters present in that specific episode.

* **Data Cleaning section**
 
    The dataframe above is the result of a data cleaning process that has been performed in two steps: first, the df has been stored in a csv file together with the "Links scraping df" from before; second, the df columns have been renamed and duplicates/useless columns have been dropped.

* **Funky stats section**
 
    In this section we answer to the questions of the project description and goal paragraph.
    
    **1.What is the highest delta episodes between first and last appearance of a given character?**
  
  ###### plotnr2
  
  [Index](#index) | [Prev plot](#plotnr1) | [More plots](#plotnr3) 
    ![MaxMinAppearance](https://user-images.githubusercontent.com/106730909/236666444-13798f95-249f-4c63-b4d7-6a5167b03cc7.png)
    Unsurprisingly, main characters such as Shikamaru, Iruka, Ino, Sakura and Naruto himself lead the chart. Surprisingly enough for me, Sasuke is not in the top spot: this is probably due to Sasuke departure from Team Kakashi. 
    
    **2.What is the most present Naruto character throughout the Anime?**
    ![MostPresentCharacter](https://user-images.githubusercontent.com/106730909/236666883-297dad82-81f0-4a8c-ac1e-0346ada4034f.png)
    As expected, Naruto is the most present character: this makes sense since the Anime is about him. Unexpectedly, Sasuke appears less than half the times Naruto does: this is probably due to the same reason why his delta episodes is lower than expected. It is worth noticing that even characters that were on the top spot of the previous plot are not appearing as much as Naruto. Take Shikamaru for instance: even though he appears in both the first and last episodes (delta = 219), he appears a approx. third of the times Naruto does throughout the Anime.
    
    **3.What is the most used japanese kanji in the japanese voice actors names?**
    
    This part has been one of the trickiest: I wanted a scatterplot to represent the count of the Japanese Kanji on the y axis, the kanji on the x axis and a third dimension as the bubble size. As the third dimension I chose the kanji strokes, not present in our df. This is why I scraped data from https://en.wikipedia.org/wiki/List_of_j%C5%8Dy%C5%8D_kanji, I created an additional dataframe and I then merged it with the df where I stored data about the Japanese dubbers name. For the sake of this exercise, the null strokes count have been filled with a mean strokes count. Note well: Matplotlib does not support japanese kanji as labels by default, this is why the x axis shows no labels: by installing the required fonts this should be easily fixable.
    ![KanjiStrokes](https://user-images.githubusercontent.com/106730909/236668428-0abea422-df5c-455c-a35f-46e5559c38b0.png)
    田	is the most present characters, it appears 53 times, it means rice paddy and it is created by 5 strokes. It is present in the top left part of the plot above.
    
    **4. Are there Naruto characters who have been dubbed by more than a dubber? (consider the most present 50 characters)?**
    
    According to my analysis, the only character that changed dubber between the 50 most present characters in the Anime is the Konoha Anbu. This makes sense since the Anbu are a group: the Konoha Anbu appearing at different times in the Anime might be a different one, thus requiring a different voice actor.
    
    **5. What is the episode with the most characters? Make a top and a flop 10!**
    
    To answer this question I used the dataframe that stores the episodes and the Pandas groupby function. The latter one is necessary in order to count the number of characters for each of the episodes. The following picture shows the top and flop 10 episodes in terms of characters count.
    ![TopFlop10](https://github.com/ilovedadata/ilovedadata.github.io/assets/106730909/cded28a0-822e-4209-9fcf-aff7331c4661)

    **6. What is the most present word in Naruto plots? Exclude English stopwords and punctuation signs**
    
    A tricky question to answer: in order to do so, the plots of the episodes were scraped from https://en.wikipedia.org/wiki/Naruto in a similar fashion to what was done before for extracting information about the characters and dubbers in each episode. The dataframe is structured as follows:
  
   | Index | Plot | 
   | ------------- | ------------- | 
   | 0 |	Naruto Uzumaki is a twelve-year-old ninja livi... | 
   | 1 |	While Naruto gets into an argument with Hiruze... |
   | ... | ... | 
   | 219 | The battle concludes with Gaara killing Seimei... | 
    
    Once stored, the plots have then been splitted into list of strings, from which English stopwords and punctuation signs have been excluded. In the end, plotting the results meant obtaining the following plot:
    ![words in plots](https://github.com/ilovedadata/ilovedadata.github.io/assets/106730909/1ade21ac-8452-42a3-bcf0-0f86ecdb228a)
Unsurprisingly, 4 out of the top 5 words are first names of the Anime main characters, namely Naruto, Sasuke, Lee, Sakura. The first non-first-name words that are found are team, ninja, attack, battle and fight which, once again, makes sense: the anime is about the ninja world, ninjas are organized in teams and fights are pretty much central throughout the whole anime.

#### Possible future developments
The code and the structures that were used to analyze the data about the Anime can be easily adapted to perform other analyses of this kind. For instance, one could go on and analyze the episodes for Naruto Shippuden and Boruto, which are both sequels to Naruto the anime. In fact, I already stored information about the characters and the dubbers of these two Animes in two dataframes (structured as the one that is found in the Episodes scraping section) and, in the future, I might come back to expand the analysis that I performed on the first anime to both Shippuden and Boruto.

#### Sources
- `The data about the characters and their dubbers in each episode comes from the Naruto fandom website https://naruto.fandom.com/wiki/List_of_Animated_Media` 
- `The kanji stroke counts are found at https://en.wikipedia.org/wiki/List_of_j%C5%8Dy%C5%8D_kanji`
- `The plots of the episodes of the anime are at https://en.wikipedia.org/wiki/Naruto`

## 

# House terminal inventory system 🏠
`#Python` `#DataScience` `#DataAnalysis` `#Numpy` `#Pandas` `#Fallout` `#Random` 

[Index](#index) | [Next project](#speeding-up-montecarlo-simulations-using-neural-networks-%EF%B8%8F%EF%B8%8F%EF%B8%8F%EF%B8%8F)

#### Project description and goal
The project is about **me and my laziness**. Since I am not good at coming up with shopping lists, the goal of this project is to create an inventory system for my house that allows me to rapidly check for the items I need to buy whenever I have the need to go to the supermarket. The **UI** of the inventory system has been optimized for using it from a terminal and, on top of that, an easter egg is present for the user to discover: once he/she enters the number 999 as an input, a fully functional **Fallout 4** terminal is run, allowing the user to try and guess a password from a given list of words. 

#### Code structure
The code is split into several functions, each having a specific goal:
* **create_a_backup**

   As its name suggests, this function is used for disaster recovering: as soon as the code starts running, a backup of the inventory is created so that, if needed, it can be reloaded. The inventory is stored as a **json** file and the handling of the json files is carried out through the **with**-**open** construct;

* **load_the_dict**.

   This functions loads the json file where the data is stored. The function takes a parameter as an input: "backup". When backup is = "yes", the backup json file is loaded (the one created by create_a_backup), otherwise the standard inventory file is loaded;

* **add_an_item**.

   This functions takes as an input the product dictionary and returns the updated one, by requiring the user to input the 4 features that, in the dictionary, define a product: name, quantity, price and category;

* **display_items_from_dict**.

   Within this functions, thanks to Pandas, the product dictionary is converted to a Pandas DataFrame. When calling this function, it is possible to provide the parameter "mode", set to "index" by default. When mode is equal to "name", the DataFrame rows are ordered by the name of the items;

* **delete_an_item**.

   When this function is called, the user is asked to provide the id of the product he wants to delete. Once the key provided, the desired element is removed from the dictionary. After the deletion of the item, the dictionary might have non-consecutive indices (actually it is almost certain: only if you delete the first or the last item the remaining ones will have consecutive indices). Because of this, within this function the dictionary is reindexed;

* **update_info**.

   This function does what its name suggests: it asks the user to provide the id (i.e. the index) of the item of which he wants to update an info of and then proceeds to do so;

* **items_to_buy**.

   This function creates a Pandas DataFrame from the product dictionary and makes use of the aggregation functions to compute the amount of money the user will have to spend to restock its inventory. Furthermore, a list of items to buy is provided to the user;

* **save_the_dict**.

   This functions saves the product dictionary as a json file.

The user can call the functions above from a menu that opens whenever he runs the script from a terminal: each function is associated to a number. For example, the menu clearly states that, whenever the user inputs 4, he can check the items to buy.

Additionally, if the user enters the correct number, which of course must remain **secret**, he can start a fully functional **fallout 4 terminal** (one of the coolest minigames I ever played in a videogame). For the non-Fallout players out there, the goal of the user in this minigame is to guess the password that is being used to keep him locked out from the terminal. To do so, he has 4 chances. The terminal script is a file of its own, which is then called by the "inventory script" when the correct input is provided.
The terminal has been implemented as follows:
* A list (actually a dictionary) of 10 random words of a given length (which can be chosen) is drawn from a bigger list (the drawn words must be of the same length); 
* To make it a "real" fallout experience, words are "wrapped" in punctuation signs (whoever played Fallout knows what I am talking about. Implementing this feature has been very tricky); 
* The words are then displayed to the user and associated to their key so that, whenever the user wants to guess the password, it is enough for him to input the number (i.e. the key) that he finds near the word;
* Whenever the user types a number corresponding to a word, the terminal prints the amount of letters that that word has in common with the password. For example, user input --> HOME, password --> COME: likeness = 3.

The following picture shows how the Fallout terminal appears to the user.

![FalloutTerminal](https://github.com/ilovedadata/ilovedadata.github.io/assets/106730909/64b06a75-5c4f-4dc7-a7a7-b08104bfe0a3)

#### Possible future developments
A possible future development might be deploying this script as an app for my mobile, so as to be able to run it from a more comfortable "access point": I am still lazy and turning on my PC takes some effort (:smile:)

##

# My take on "An Introduction to Statistical Learning" 
`#Python` `#DataScience` `#DataAnalysis` `#Numpy` `#Pandas` `#Matplotlib` `#Statistics` `#Probability` `#Scikit-Learn` `#Pytorch`

[Index](#index) | [Next project](#speeding-up-montecarlo-simulations-using-neural-networks-)

#### What's in the book?
_”An Introduction to Statistical Learning provides a broad and less technical treatment of key topics in statistical learning. This book is appropriate for anyone who wishes to use contemporary tools for data analysis.”_. The chapters cover the following topics:
- What is statistical learning?
- Regression    
- Classification
- Resampling methods
- Linear model selection and regularization
- Moving beyond linearity
- Tree-based methods
- Support vector machines
- Deep learning
- Survival analysis
- Unsupervised learning
- Multiple testing

(https://www.statlearning.com/)

#### Goal
I studied this book to accomplish two **goals**, namely:
- Revise the techniques, methods and deepen my knowledge about Statistical Learning ➡️ Accomplished in chapters 1 through 9: **theory+exercises using Numpy, Pandas, Matplotlib, Seaborn, Scikit Learn**
- Widen my knowledge about deep learning ➡️ Accomplished in chapter 10: **theory+exercises using Pytorch** 

#### Some comments about the source code
I completed the `applied exercises` of a given chapter not in a single take. This is why, in the source code, there might be repetitions (i.e.: copy paste of some lines of code, multiple imports of the same library, etc). Some additional notes:
- The “#” comment is, most often, a comment made by me
- The “‘’’” comment is, most often, copy pasted from the book or from the library I import a function from
- I completed the labs and imported most of the functions of the ISLP module in the first 4 chapters. From chapter 5 onwards I focused mainly on the exercises and on the use of **Scikit Learn**, since it is the library that is most often used in the “real world”. This is also the reason why often, when I had to choose between performing a task with ISLP or with Scikit Learn, I chose the latter way of doing it.

#### Chapter 1, 2: Introduction to Statistical Learning
##### Theory
- Trade-Off between prediction accuracy and model interpretability 
- Supervised vs Unsupervised Learning
- Regression vs Classification
- Bias-Variance trade-off
##### Exercises
- Introduction to numerical Python, Indexing, Slicing, Loading, Loops, Graphics (Skipped because already very well known 💪🏻)
- Data exploration using Pandas, Numpy: loading csvs, describing dfs, computing statistics (min, mean, max, stdev, etc)
- Data plotting using Matplotlib, Seaborn

#### Chapter 3: Linear Regression
##### Theory
- Simple and Multiple Linear Regression
- Regression Coefficients estimation through least squares
- Model and coefficients accuracy assessment (RSE, $R^2$ , t-statistic, p-values, residuals, etc)
- Encoding qualitative predictors
- Hypothesis testing
- Comparison with KNN
##### Exercises
- Linear Regression models fitting by using the ISLP, Scikit Learn packages
- Analysis of the fits and of the statistical significance of the variables through p-values, anova tests, R squared statistic, hypothesis testing, correlation, residuals etc
- Data plotting using Matplotlib, Seaborn
- Outlier, high-leverage observations analysis
##### Some cool stuff from the exercises
###### 13.f Population Regression Line vs Least Squares Line plot:
➡️ Population Regression Line equation: $Y = −1 + 0.5X + e$ ➡️ Least Squares Line equation: $Y = −0.9265 + 0.5477X$
![image](https://github.com/ilovedadata/ilovedadata.github.io/assets/106730909/f863b7f3-10e7-4e2d-812b-4b6156014ac8)
![image](https://github.com/ilovedadata/ilovedadata.github.io/assets/106730909/c2abdd47-3784-493a-b8cf-50b28ac02632)
The plot above shows the difference between the two lines present in its legend: 
- The **Population Regression Line** is the best approximation possible of the true relationship between X and y. It is not always available. 
- The **Least Squares Line** is the one that is estimated through Linear Regression Least Squares (the one whose coefficients you obtain through Scikit Learn linreg or statsmodels ols)
Overall, from the point of view of coefficients estimation, the model performs well. Furthermore, both the intercept and the slope are **statistically significant** for the regression: their **p-value** is lower than 0.05 (you reject the **null hypothesis** that the associated beta is 0).
###### 13e, g: When a polynomial model is not necessary
![image](https://github.com/ilovedadata/ilovedadata.github.io/assets/106730909/ac84a620-e446-408d-9a96-f36719d566ea)
The figure above shows the output of calling the summary function of statsmodels on two models: left ➡️ linear, right ➡️ polynomial.
Is it worth it to use a polynomial model instead of a linear one? No, and we can see it by looking at the $R^2$ coefficient: it is always the same, this mean that the explained variabilty of y by the model is always the same, even though we add more variable transformations in the polynomial one. Additionally, the p-value associated to the $X^2$ coefficient is higher than 0.05 ➡️ we fail to reject the null hypothesis its beta is = 0, i.e. the term is not statistically significant for the regression.

#### Chapter 4: Classification
##### Theory
- Logistic Regression (and why not using Linear Regression)
- Poisson Regression
- LDA with p>=1
- QDA
- Naive Bayes
- Comparison with KNN

##### Exercises
- Logistic and Poisson Regression, LDA, QDA, Naive Bayes models fitting by using Scikit Learn (train test splitting)
- Performance analysis by (among other metrics) confusion matrices
- Data plotting using Matplotlib, Seaborn
- Graphical analyses to spot the most useful variables in predicting the output label

##### Some cool stuff from the Exercises
###### 12 e, f, g, h The usual Scikit Learn workflow
![image](https://github.com/ilovedadata/ilovedadata.github.io/assets/106730909/e79a3787-2006-43b3-aad4-64f2d06f8ff3)
The pictures above refer to 4 different machine learning methods and display (part of) the usual Scikit Learn workflow, namely:
- Creating an instance of a Scikit Learn class (like KNeighborsClassifier)
- Fitting the model to the train data
- Making some predictions on the test data
- Computing some metrics

For the last point, in the code snippets I call a custom function I defined, which works as follows:
- Inputs ➡️ y_test, y_preds
- Outputs ➡️ the confusion matrix, the percentage of correctly guessed classifications on the test set (i.e. the # of instances on the diagonal of the confusion matrix divided by the total number of instances in the test set)

#### Chapter 5: Resampling methods
##### Theory
- Cross Validation (k-fold, leave-one-out)
- Validation set approach
- Bootstrap

##### Exercises
- Logistic Regression and Linear Regression models fitting after train, test, split of the data using Scikit Learn
- Models performance evaluation on the validation set or through cross validation (k-fold, LOOCV) using Scikit Learn and writing custom functions
- Statistics computation (posterior probability, mean, stdev, percentiles, etc) using Numpy, Pandas
- Computation of standard errors through Bootstrap 
- Data plotting using Matplotlib, Seaborn

##### Some cool stuff from the Exercises
###### 8 c, e, f LOOCV in Scikit Learn and comparison to the "real" model
This exercise aimed at getting which degree model performed best when **LOOCVing** on a dataset, keeping in mind that the "true" model is the one that follows:

$y = x - 2 * x^2 + rng.normal(size=100)$

Looking at the code, it is possible to see that the whole analysis was implemented through a for cycle, of which I explain briefly the details in the comments below.
![image](https://github.com/ilovedadata/ilovedadata.github.io/assets/106730909/7b3cd624-f1f2-4496-ae3f-4056adf4a091)
- Data is transformed through an instance of the PolynomialFeatures class of Scikit-Learn
- By "cross_validate" we get the results of the cross validation. In this case, we are interested in the mean_squared_error metric and, since we have several scores (one per fold), we compute its mean.
- The script above shows the trick by which it is possible to perform a LOOCV in Scikit Learn: it is enough to perform a k-fold CV, setting the k parameter (cv in the code above) to be equal to the number of rows of the features dataframe.

All in all, the model that performed better was the LOOCV performed on degree 2 data. Surprising? Nope, since the "true" model is quadratic in X.

What do the techniques we used to verify the statistical significance of parameters in the previous chapters say about this conclusion?
![image](https://github.com/ilovedadata/ilovedadata.github.io/assets/106730909/3b1d93f7-8e5d-4644-b1c4-c9f8d0e9e6b2)
Actually, they agree with the conclusions that were drawn above: the p-values associated with the 3rd and 4th degree term are > 0.05, thus the parameters are not statistically significant for the regression.

#### Chapter 6: Linear Model Selection and Regularization
##### Theory
- Subset Selection (Best Subset, Forward and Backward Stepwise selection)
- Cp, AIC, BIC, Adjusted R-squared
- Ridge, Lasso Regression
- Principal Components Regression (PCR)
- Partial Least Squares Regression (PLS)
- Regression in high dimensions

##### Exercises
- Best, Forward Stepwise, Backward Stepwise Subset selection writing custom functions in Python Pandas, Numpy
- Ridge, Lasso models fitting and parameter tuning by using Scikit Learn
- PCR, PLS models fitting and parameter tuning
- Data plotting using Matplotlib, Seaborn
- Mean Squared Error, Root Mean Squared Error computation

##### Some cool stuff from the Exercises
###### 8 c, d: Forward and Backward Stepwise Selection Models
Throughout this chapter, I implemented 3 algorithms: **forward stepwise, backward stepwise and best subset selection**. 
The following example concerns the performance of two models obtained by the first two algorithms. The goal is to mimic as much as possible the following model:

$y = 1 * X + 2 * X^2 + 3 * X^3 + e$

**Forward and Backward stepwise selection** are two methods that aim at selecting the subset of features that are most related to the response and that, thus, let you create a **good** performing model. Why good and not **best**? Because they are not guaranteed to find the best performing subset of predictors, given how they select them. To do so, one should use the best subset seleciton method (see the source code for more details).

![image](https://github.com/ilovedadata/ilovedadata.github.io/assets/106730909/ab1b459a-46cf-48fa-bf93-02915486da9b)
The pictures above display the results of, respectively, **Forward and Backward stepwise selection**. In this particular application, The first algorithm performs better than the second one and we can see it from three indicators:
- **The variables chosen**: whilst the backward stepwise selection algorithm selects 6 features, missing $X^2$, which is in fact included in the original algorithm, the forward stepwise selection method selects the correct subset of features.
- **The parameters** of the forward stepwise selection model are almost the correct ones.
- Consequently, the $R^2$ of the FSS model is better than the BSS model one.

###### 10 c, d: Test and Train error of a Best Subset Selection model
![image](https://github.com/ilovedadata/ilovedadata.github.io/assets/106730909/655bfdd5-7e01-4a36-85d5-c038ea28cb72)
The picture above displays the test error and the train error of several models implemented at each iteration of a **best subset selection**. 
For any given number of features, the best performing model is selected (EX: number of features = 6 is the performance of the best model possible having 6 features in total).

#### Chapter 7: Moving Beyond Linearity
##### Theory
- Polynomial Regression
- Step Functions
- Regression Splines (Piecewise Polynomials, constraints, knots)
- Smoothing Splines
- Generalized Additive Models (GAM)

##### Exercises
- Polynomial Regression models fitting by using Scikit Learn 
- Analysis of variables importance through  ANOVA tests
- Step Function models fit by using Pandas, Scikit Learn
- Regression spline models fit using the ISLP package  
- Non-linear transformations of input variables 
- Models optimization through cross-validation
- Backfitting approach: custom function creation and analysis of the method
- Data plotting using Matplotlib, Seaborn

##### Some cool stuff from the Exercises
###### 9 b Visualizing models up to the 20th degree

###### plotnr3
  
[Index](#index) | [Prev plot](#plotnr2) | [More plots](#plotnr4) 
![image](https://github.com/ilovedadata/ilovedadata.github.io/assets/106730909/70bebcf5-e2d4-4340-b2ed-5f4e7be282f2)
The plot above shows polynomials of different degrees, as well as the data they were generated from.
In particular, the data come from the Boston dataset, and the "dis" feature was used to predict the "nox" response.
Through a for cycle, 20 different models were generated, each containing a different transformation of the input feature. All this was accomplished by using Scikit-Learn LinearRegression(), PolynomialFeatures() and by train_test_splitting the data.

###### 12 Visualizing the convergence of coefficients estimated through backfitting

###### plotnr4
  
[Index](#index) | [Prev plot](#plotnr3) | [More plots](#plotnr5) 
![image](https://github.com/ilovedadata/ilovedadata.github.io/assets/106730909/becc173e-a434-4569-a498-2204785dbbd0)
The plot shows how the coefficients estimate varied whilst iterating the backfitting procedure. In this particular case, the coefficients reached a value closed to the final one at iteration 133 (there was a total of 200 iterations).

#### Chapter 8: Tree-based methods
##### Theory
- Regression and Classification Trees
- Comparison with linear models
- Bagging, Boosting, Random Forests
- Bayesian additive Regression Trees (BART)

##### Exercises
- Classification and Regression Tree models fitting by using Scikit Learn 
- Models optimization through cross-validation
- Bagging, Boosting, Random Forest models fit and comparison to base tree models (confusion matrices, recall, etc)
- Data plotting using Matplotlib, Seaborn

##### Some cool stuff from the Exercises
###### 8 c 5-fold cross validation of a DecisionTreeRegressor()

###### plotnr5
  
[Index](#index) | [Prev plot](#plotnr4) | [More plots](#plotnr6) 
![image](https://github.com/ilovedadata/ilovedadata.github.io/assets/106730909/e61c1278-72f5-425b-9ba0-80c5f17fa3cc)
The plot visualizes the performance of a **DecisionTreeRegressor** in 100 different configurations. The two parameters whose value was tuned are the "max_depth" and the "max_features".
The y-axis diplays the **Mean Squared Error** associated with each and every parameter configuration. For each parameter configuration, the plot shows the average performance on all the folds as well as the performance on each fold.
Finally, a red dot highlights the configuration having the **lowest MSE**.

###### 12 Visualizing how Recall varies as a function of the probability threshold

###### plotnr6
  
[Index](#index) | [Prev plot](#plotnr5) | [More plots](#plotnr7) 
![image](https://github.com/ilovedadata/ilovedadata.github.io/assets/106730909/be57df87-4d13-42f7-ac4e-a0ba182db805)
The plot colors are relative to the following methods:
- Yellow ➡️ **RandomForestRegressor()** with a "max_features" parameter >= 45
- Black ➡️ **RandomForestRegressor()** with a "max_features" parameter <= 44
- Green ➡️ **Bagging Regressor**
- Red Yellow ➡️ **Logistic Regressors**
The goal of this exercise is to maximize recall. In total, 89 models were tested, and their recall was computed whilst varying the threshold according to which they made predictions ("positive" class ➡️ "Yes).
As expected, lowering the threshold means increasing the **recall** (as a low probability is enough to be classified as "Yes"). Furthermore, considering more features when looking for the best split brought better results than considering a few (yellow recalls better than black ones) and, clearly, **Logistic Regression** performs better than the tree-based models in this application.

#### Chapter 9: Support Vector Machines
##### Theory
- Maximal Margin Classifier and Hyperplane
- Support Vector Classifiers (SVC): linear boundary between classes
- Support Vector Machines (SVM): non-linear boundary between classes

##### Exercises
- SVC, SVM models fitting by using Scikit Learn 
- Logistic Regression models fitting on non-linear transformations of the predictors to compare them with SVM
- Models optimization through cross-validation and kernel variation (linear, radial, polynomial)
- Data plotting using Matplotlib, Seaborn

##### Some cool stuff from the Exercises
###### 5 e-f Visualizing the classification made by a Logistic Regression fit on polynomial data

###### plotnr7
  
[Index](#index) | [Prev plot](#plotnr6) | [More plots](#plotnr8) 
![image](https://github.com/ilovedadata/ilovedadata.github.io/assets/106730909/08bc4d39-5dbc-401d-a1fa-c649cf53a432)
The plot above shows how a **Logistic Regression** model classifies observations when fit on features transformed up to the 4th degree. The legend of the plots shows the confusion matrix and, as it is evident from the plots, while the **performance improves significantly from degree 1 to degree 2**, the same is not true for the higher degrees. As a matter of fact, the confusion matrix keeps on being equal (actually, this happens up to degree 12).

###### 7 c 5-fold cross validation of a Support Vector Machine with a radial kernel
![image](https://github.com/ilovedadata/ilovedadata.github.io/assets/106730909/6847b991-fdf3-458a-9045-78827feaffbf)
This plot logic resembles the one of Exercise 8 c from chapter 8: a **cross-validation** was performed in order to get the best performing parameters configuration for a **SVM model**. As on the previous plot, on top of the **mean performance** of the parameter configuration, the performance on each individual fold is shown.
As it is evident from the picture, the accuracy of the model is higher when the "gamma" parameter is set to "scale".

#### Chapter 10: Neural Networks
##### Theory
- Single and Multiple Layers Neural Networks
- Convolutional Neural Networks (CNN) architecture (convolution and pooling layers)
- Recurrent Neural Networks (RNN). Particular focus on time series forecasting
- Neural Network fitting (Backpropagation, Dropout Regularization) and Double Descent

##### Exercises
- Gradient Descent application on sin/cos functions 
- Neural Networks fitting and performance comparison with respect to other classification/regression models
- CNN classification of images
- Creation and fitting of linear autoregressive Neural Networks (RNN) and performance analysis as a function of model architecture and features used to train the model

##### Some cool stuff from the Exercises
###### 6 c,d Visualizing Gradient Descent

###### plotnr8

[Index](#index) | [Prev plot](#plotnr7) | [More plots](#plotnr9) 
![image](https://github.com/ilovedadata/ilovedadata.github.io/assets/106730909/78a7a6e2-ecc5-443c-bb15-5bc503d53790)
The plot above shows how **Gradient Descent** finds a local minimum of a sin function. As expected, the **local minimum** that is found by gradient descent depends on the initial **starting point**. Furthermore, it is possible to verify visually that the bigger is the slope of the function, the bigger is the step taken by the gradient descent.

###### 13 The performance of a Neural Network as a function of the neurons in its hidden units

###### plotnr9

[Index](#index) | [Prev plot](#plotnr8) | [More plots](#plotnr10) 
![image](https://github.com/ilovedadata/ilovedadata.github.io/assets/106730909/661ca54c-0632-4c3e-a86c-169adf38e8de)
This plot displays the performance of a **Neural Network** as a function of the number of the neurons in its 3 linear **hidden layers**.
The **colors** of the plot highlight the different number of neurons in each of the different (4) **architectures tested**. 
Furthermore, it is possible to observe the performance at each different **epoch** of the training loop (each "color" has **10 different BCEs**, as the training loop was performed in 10 epochs).
In addition, the **dotted lines** refer to the performance of the given model architecture when **dropout regularization** is applied.
Overall, the best performance (accuracy=0.866) was obtained for a model using 64 neurons and dropout regularization.

#### Chapter 12: Unsupervised Learning
##### Theory
- PCA
- KMeans Clustering
- Hierarchical Clustering

##### Exercises
- Demonstration of the equivalence of the use of correlation-based distance and Euclidean distance as dissimilarity measures for hierarchical clustering
- Computation of PCA Proportion of Variance Explained in different ways
- Clustering models fitting and performance analysis as a function of the preprocessing steps and of the variables the model is fitted on
- Dendrograms interpretation and analysis

##### Some cool stuff from the Exercises
###### 7 correlation-based distance and Euclidean distance as dissimilarity measures for hierarchical clustering
![image](https://github.com/ilovedadata/ilovedadata.github.io/assets/106730909/9b58f090-a671-4921-b67a-91dfc52a1fab)
The plot above shows how the two aforementioned dissimilarity measures are almost equivalent for hierarchical clustering.
To obtain the plot, all the observations have been **standardized**. The red line represents the **squared euclidean distance** between two consecutive observations, the blue line $1 - r_{ij}$, where $r_{ij}$ is the **correlation** between two consecutive observations.
P.S.: the process of manipulating the dataframe to demonstrate such a thing has been excruciating!

###### 13 b How the linkage method changes the appearance of a dendrogram

###### plotnr10

[Index](#index) | [Prev plot](#plotnr9) | [More plots](#plotnr11) 
![image](https://github.com/ilovedadata/ilovedadata.github.io/assets/106730909/81e42c5e-d614-4ce7-a560-80a3b1b367cd)
This plot displays the different ways in which the **Hierarchical Clustering** algorithm groups together the observations according to the linkage **method** used, i.e. according to how the distance between observations is computed.
In particular, the first plot shows the grouping of the samples when **linkage = "complete"**, the bottom pic displays how observations are clustered if **linkage = "average"**.

# Speeding up montecarlo simulations using Neural Networks ♠️♥️♣️♦️🧠
`#Python` `#DataScience` `#DataAnalysis` `#Numpy` `#Pandas` `#Matplotlib` `#Statistics` `#Probability` `#Random` `#Seaborn` `#Pytorch` 

[Index](#index) | [Next project](#building-and-optimizing-a-portfolio-simulator-)

#### Project description and goal
This is a project where I had a lot of fun. I used data structures to create functions simulating events, I computed the probability of complex events by random sampling and then I trained a neural network which sped up my simulations. 
Specifically, the project is about building a **poker simulator** from the ground up, without employing ready-to-use libraries, to then perform **montecarlo simulations** and, finally, speed them up using a neural network. Yeah, but what are montecarlo simulations? 
From wikipedia, they are a class of computational algorithms that rely on repeated random sampling to obtain numerical results. Basically, I will:
- Randomly generate poker hands;
- Make use of some functions that I coded in Python to determine whether a given outcome happened or not;
- Repeat the two steps above a _lot_ of times, to simulate the long-term occurrences of poker hands.
After doing so for both the 5-card and the Texas hold'em poker rules and proving that the probabilities are correct, I will go on expanding the project, by making it possible to determine the winner of a poker match, using a neural network to speed up the simulations and optimizing code to reduce the simulations time. The goal is to perform as much simulations as possible in the shortest amount of time.

#### Code structure
The code is made up by 4 main sections:
##### 5-card poker montecarlo simulator section

###### OOP and classes
The first thing you need when playing poker is a deck of cards. The first thing you need when creating a deck of cards is the idea of what a card is. This is why, first and foremost, in this section I create two classes: the card and the deck. 

* **The card class**
  The card class is very simple, it has two methods (`__init__`, `__repr__`) and its only goal is to represent a card as follows:
  `(Rank, Suit). Example: ('A', 'D') is an Ace of Diamonds.
* **The deck class**
  The deck class is more complex but, basically, it makes use of the card class to create a list of cards, given some ranks and some suits. In addition to the `__repr__` and `__init__` method, I implemented the `__getitem__`, `__len__` and `__setitem__` methods, that will all be needed when performing simulations. 
* **Bonus: The (very lucky) deck classes**
  When training my neural network (`nn`), I faced a problem: if a royal flush only happens 0.000154% of the time, how will my nn learn how to spot it? This is why I created variations of the "base" deck class to have decks where a given hand happened 100% of the time. For instance, in a StraightFlushDeck only Straight Flushes can happen. 
  
###### The "core" functions
The engine of my simulator are the several functions I coded to make it work. Some examples:
- In order to play poker, you need to draw hands from a deck. This is why I built a function that makes use of the classes created in the section above and does just that.
- Furthermore, I created several functions that are able to detect whether a given poker hand was scored. **The latter ones make use of my knowledge of data structures** (lists, hash maps, sets, etc...). An example? Let's say that, in order to detect whether the given hand contains a pair, I check for the length of some of the data structures I mentioned.
- Since I wanted to be able to determine the winner among several players, I created two additional functions that sort the ranks and the suits according to their importance for the game that is being played. The trickiest part? Solving ties, look at the following example to understand.

  `Player_1 [(A, D), (A, C), (8, S), (4, S), (10, H)];`
  
  `Player_2 [(A, H), (3, S), (2, D), (9, H), (A, S)];`
  
  `To solve ties, I made use of, once again, data structures and algorithms, as well as of some of Python functionalities, like a particular way in which Python compares sequences.`

###### The simulation
In order to perform the montecarlo simulation, I put everything together in a Python loop whose main tasks are:
- Getting input parameters such as number of players and games played.
- Simulating the (thousands of) games and determine the winner(s) of a given poker game. 
- Store everything in a pandas dataframe to compute stats and plot cool stuff.

For every simulation performed, I always checked one thing: the real probabilities of the hands (source: Wikipedia) must not differ significantly from the ones I computed through my simulation.
![Pic(1)](https://github.com/user-attachments/assets/c30d3ecd-af0e-49d4-bd42-e148be221471)

##### Texas hold'em poker montecarlo simulator section
The way I implemented the Texas hold'em simulator is very similar to how I created the 5-card poker one. 
However, similar does not mean equal and I want to stress this point: at the beginning, I thought that, with just a few changes, I could create such a simulator. In fact, this was not the case, as in Texas hold'em you care about the 5 most important cards in a 7 card hand. 
Coding such a game mechanic has been a nightmare. To sum up, the main issue was finding a way to systematycally spot the 5 most important cards, for each of the different scores that might happen (from high card to royal flush). Furthermore and for the same reason (the 5 most important cards!), solving ties in a game is more challenging in Texas hold'em than in 5-card poker. Look at the following example to understand.

  `Player_1 [(8, S), (4, S)]; Player_2 [(2, S), (6, S)]; Flop [(A, H), (9, H), (A, S)]; Turn [(A, D)]; River [(9, D)];`
  
  `Player_1 most important cards [(A, H), (9, H), (A, S), (A, D), (9, D)];`
  
  `Player_2 most important cards [(A, H), (9, H), (A, S), (A, D), (9, D)];`
  
  `Conclusion: this is a tie and this is trickier to spot that it is in 5-card poker. Why? Once again, because in Texas hold'em only the 5 highest cards matter for a given player, with 5 cards out of 7 being shared by the players.`

With this said, let's look at some cool plots. The first shows which hands, flops, turns, rivers, were the most common ones out of 3000 games played. 
![Pic(1)](https://github.com/user-attachments/assets/228b1d17-4621-4dd8-bbe3-77047cd7f5d4)

The second plot is a 3d plot on which I implemented a **custom labelling technique**. This plot shows that the higher the score, the higher the amount of times a hand wins. For instance, a high card happens a lot of times but wins a few (Times_won close to 0, Results_count close to 2000), a straight flush wins whenever it is scored (low Results_count but similar Times_won value).
![Pic(2)](https://github.com/user-attachments/assets/f9fed768-8219-4d6c-b003-84d9f6e00353)

##### Neural network simulations "acceleration"
###### Nn training
The nn I trained had one goal: it needed to perform montecarlo simulations in a quicker way. To be clear, I trained the nn to predict the poker hands and, as stated before, I made sure that a significant amount of hands was present for each of the scores I wanted the nn to predict. Specifically, more than 500k hands were generated and used as a train set. At least 20k of each of the scores were present.

For what concerns the architecture of the neural network, I used 3 linear layers, on the first two of which I applied an activation function. The loss function I used to keep track of the improvement of the nn performance throughout the optimization process is the cross entropy loss.

The following plots sum up the results I got in the optimization loop, in which I trained 5 different nn on 20 epochs. In the first plot, both the training and the validation cross entropy loss are plotted as a function of the epoch number: in the end, the 64 hidden neurons nn seems to be the best performing one.

###### plotnr11

[Index](#index) | [Prev plot](#plotnr10) | [More plots](#plotnr12) 
![Pic(7)](https://github.com/user-attachments/assets/df651fc8-6c3a-4ac8-9960-6355b4344075)

The second plot shows (left part) the hands that the models misclassified out of the 54000 in the test set. Impressively, the 64 hidden neurons model misclassifies just 11 of them. On the right part, a neat stat: the most frequently misclassified "hand" by the model. If we consider the best performing model, most of the 11 misclassified hands are straights.
![Pic(8)](https://github.com/user-attachments/assets/86236e57-69bf-43b1-981c-1978a5c70a6e)

###### Optimization and montecarlo speeding-up section
![Pic(9)](https://github.com/user-attachments/assets/decee99e-4cd4-435f-a969-e354a68f3cac)

The picture above shows the time taken by the simulations as a function of the number of hands played. 
The orange lines refer to the simulations performed by the neural network, the cyan lines to the ones performed by using the functions I wrote to detect the poker hands.
Furthermore, the upper plots refer to the time that is taken to create the df where the data about the simulations is stored, the lower plots refer to the time taken to perform the simulations. 
Consequently, to obtain the total duration of the whole process (df creation + simulation), one has to add the two lines that look the same on the upper plot and on the lower plot. 
`For instance, on the left (cyan) we can say that 100000 simulations take about 800 seconds in the non-optimized setting (mostly for the creation of the df).`

The main thing that it is possible to notice is that the "creation" part takes a lot of time compared to the evaluation one. This is why I re-wrote the code and created an optimized version of it (`_opti`), whose simulation times are represented by the dashed lines. 

Excitingly, the optimization reduced the simulation times by A LOT. This is showed by the fact that a million simulations in the optimized configuration only take a fraction of the time that was necessary to perform a tenth of them in the standard version of the code. The most evident improvement is in the nn creation plot: considering 100000 simulations, the time needed to simulate decreased from 2500 s (more than 40 minuted) to just 17 seconds.

**Yeah but in the end, was I able to speed up montecarlo simulations by using a neural network?** YES! Look at the lower part of the plot: even though for a "low" number of simulations (<= 100000) the difference is not that impactful on user experience (0.82 seconds are not that perceivably different from 0.04), if we consider a million of simulations, the montecarlo performed by the nn takes 1% of the time it takes when it is performed normally (0.63 s vs 39 s). 

It is true that creating the df for a nn-montecarlo simulation takes more than it does in a normal setting, but I think that the time savings in the simulation part of the process are astonishing nonetheless (and let me stress, once again, that the nn misclassified just 11 instances out of 54k on the test set, so it is pretty accurate). 
#### Possible future developments
As stated in the powerball project, the structures and scripts used in this project can possibly be used in the future to simulate other kinds of gamble games/casino games. Furthermore, the functions I wrote to perform "normal" montecarlo simulations might still be optimized, thus time taken to perform the simulations might decrease again. The same can be said about the df creation part of the nn simulations: optimizing data storage might decrease the overall simulation time even more!
#### Sources
- `The data regarding 5-card and Texas hold'em probabiities come from Wikipedia`

# Building and optimizing a portfolio simulator 💵🎢 
`#Python` `#DataScience` `#DataAnalysis` `#Numpy` `#Pandas` `#Polars` `#Matplotlib` `#Statistics` `#Probability` `#Random` `#Seaborn` 

[Index](#index) | 
#### Project description and goal
This project was used as an excuse to become more proficient in using Polars. In particular, I used this library to optimize as much as possible a simulation loop, so as to perform as many simulations as I could in a given amount of time. 
This idea was born whilst re-creating from the ground up an analysis by Paolo Coletti: as it often happens to me with novel ideas, I created something new and I ended up in a totally different direction from the one I thought I would. Nontheless, I hope this project will interest the reader as much as it interested me (honestly, I think this one turned out to be pretty cool!). 
P.S. Paolo's works on investments are special, check them out on his Youtube channel.

Overall, during this project I used yahoo finance to download stock prices, I computed their yields and I performed random simulations about different sized stocks portfolios, finally comparing their performance to the one of another investment strategy, namely ETF-and-chill investments. The analytical part of this project was completed by using Pandas and Numpy in addition to Polars, whilst the plots were created using Matplotlib and Seaborn. 
The basic steps of the simulation are the ones that follow:
- Determine how much money you want to invest;
- Pick a number of years you want to invest your money for;
- Pick a number of stocks you would like to have in your portfolio and randomly choose them;
- Compute the stocks returns and the ETF returns;
- Repeat the three steps above a _lot_ of times to get statistically significant data about the investments performance.

As stated before, after creating a working "version 1.0" of the simulator, I will try to optimize its performance as much as possible through the course of the following sections. In the end, after doing so for several combinations of years of investments (nr_years) and number of stocks (nr_stocks), I will analyze data and draw conclusions. The goal is, in addition to optimization, *visualizing* how returns are affected by the financial tool you choose to invest on, by by the years you invest your money for and, in the case of stocks, by the portfolio size (i.e. by the "number" of stocks you invest on). 
#### How does the simulator work?
##### Data and Simulator logic
###### Getting data
First and foremost, the simulator needs data to work with. Since we have to compare stocks vs a global ETF (the latter being represented by an MSCI world Index), we need data about the daily values of these financial tools:
* For what concerns the **ETF**, the data was obtained from Paolo's Github.
* For what concerns **stocks**, the process has been tricker. In particular, for the sake of this project, I downloaded all the tickers from the NASDAQ stock exchange and used them as an input for the yahoo finance download function. In this way, I obtained the daily values of stocks on the NASDAQ in a given time period, (which is, obviously, the same period I considered for the ETF daily values, namely start="1999-01-04", end="2024-12-31").

As I started to do in this section, I will refer to the global index daily values and returns as ETF daily values and returns since, during this project, I proved (even though I did not include it in this portfolio) that ETFs tracking a given index are unsurprisingly able to replicate its returns.
###### Simulator logic
To understand how the simulator works, let us first visualize how data is stored in the DataFrame that will be the "engine" of this project. Say "Asset" is any of the stocks/ETFs whose daily values you downloaded:

| Index | Asset Value (€) |
|-------|----------------|
| 0     | 100.00        |
| 1     | 102.50        |
| ...   | ...           |
| 1310  | 120.00        |
| 1311  | 118.00        |
| ...   | ...           |
| 2620  | 125.00        |
| 2621  | 124.50        |
| ...   | ...           |
| 3930  | 140.00        |
| 3931  | 138.50        |
| ...   | ...           |
| 5240  | 145.00        |
| 5241  | 144.00        |
| ...   | ...           |
| 6550  | 150.00        |

In order to compute the returns of the Asset over a given period of time, we need to first get its rate of return. To compute the latter, we simply divide the asset value on a given day by the value it had k days (or months, or years) before and subtract one to it, with k being the days/months/years over which we are interested in computing the rate of returns. 
```math
RateOfReturn_{kYears} = (AssetValue_{Today}/AssetValue_{kYears} - 1)
```
For instance, the following table displays the computations that a single simulation performs for a given period of time, say k=5 years. Take the 1310th row: the rate of returns is 20% because (120/100 - 1). 

How do we get these numbers though? Well, the 1310th row tells us that, on a given day happening 1310 days after the first row (AssetValue_kYears), a certain stock was traded for 120 € (AssetValue_Today). Why 1310? if k=5 years, 1310 = 5*262, with 262 being the days the stock market is opened per year. If we find nan values, it means there was no value for the asset k days/years/months before (i.e. there was no AssetValue_kYears).

| Index | Asset Value (€) | 5-Year Rate of Returns (%) | Annualized Rate (%) | Returns (€) |
| ----- | --------------- | -------------------------- | ------------------- | ----------- |
| 0     | 100.00          | NaN                        | NaN                 | NaN         |
| 1     | 102.50          | NaN                        | NaN                 | NaN         |
| ...   | ...             | ...                        | ...                 | ...         |
| 1310  | 120.00          | 20.00                      | 3.71                | 1200.00     |
| 1311  | 118.00          | 15.12                      | 2.86                | 1151.42     |
| ...   | ...             | ...                        | ...                 | ...         |
| 2620  | 125.00          | 4.17                       | 0.82                | 1041.78     |
| ...   | ...             | ...                        | ...                 | ...         |

This computation is exactly what the Pandas `pct_change()` function performs, thus this is the function powering the simulator in the Pandas section of the code determining the **k-year rate of return**.

Once we have it, we are able to compute the **annualized rate(%)**, using the following formula:
```math
annualized_{rate} = (1 + actual_{rate})^{1/k} - 1
```
When using the **k-year rate of return** as the actual rate, the formula smoothens the returns over the period we are considering, giving us the constant annual growth rate we had over the considered period of time. For instance, looking at the 1311th row, getting a return of 15.12% after 5 years means getting a 2.86% yearly return at the end of each of the five years.

Finally, to get the **Returns** (the amount of money we obtain from our investment) we use the formula for the compound interest: 
```math
M = C*(1 + annualized_{rate})^{k}
```
Where C is the amount of money we invested (1000 € in this case) and the annualized_rate is the one coming from the formula above. k represents, as in the previous formula, the amount of years we commit to invest our money for.
###### Speeding stuff up
From the computations above it is clear that, if calculating the returns is the end goal of the simulation, we can do so in one pass:

Since: 
```math
annualized_{rate} = (1 + actual_{rate})^{1/k} - 1
```
Then: 
```math
M = C*(1 + annualized_{rate})^{k} = C*(1 + (1 + actual_{rate})^{1/k} - 1)^{k}
```
So:
```math
M = C*(1 + actual_{rate})
```
This is one of the ways in which the code will be optimized: since the "^" operator is particularly expensive in terms of computation time,  finding M in the latter way helps to speed things up.
##### Simulator Pseudocode
```
1. Set the simulations constants, namely the amount you want to invest (C) and the number of simulations you want in your df for each (nr_years, nr_stocks) combination;
2. Loop through each (nr_years, nr_stocks) combination; 
3. Pick random tickers (quantity = nr_stocks) and compute the returns of the (nr_stocks) stocks and of the ETFs during the (nr_years) period;
4. Store the data in a df.
```
#### Simulation optimization
![image](https://github.com/user-attachments/assets/770cf9c1-00fa-4149-abf0-817ce08bd1cb)

When optimizing code, I came up with several different versions of the simulator, whose performances are all listed in the pic above. 
The following are the test cases that were considered:
``` python
# years_of_investments
k = [0.25,0.5,0.75,1.,2.,3.,4.,5]
# number_of_stocks
step = 2
n = range(3,14,step)
```
##### The most important part of the simulation cycle
It is important to stress that the core part of the simulation, i.e. the one determining the results and the one driving the time complexity of it, is point 3 from [Simulator Pseudocode](#simulator-pseudocode). In it, thanks at first to Pandas ufuncs and then to Polars, the yearly rate of returns of the stocks are computed for each of the rows of the df (thus, potentially, for each day between 1999-01-04" and 2024-12-31).
##### Unavoidable randomness slows down the simulation
The way the code is written, there is a part of the process that one cannot avoid from being influenced by randomness: once the rate of return is computed in point 3, the rows containing them need to be appended to the "whole" df, where you are storing the results. Unluckily, there is a catch and, to get it, let's make an example considering k = 5, n = 11:
- Your df will look like the one from the [Simulator Logic](#simulator-logic) section, except you will have more columns (one per stock you compute the returns of), thus 11;
- When you compute the rate of returns randomly picking stocks, your df will have a *lot* of empty rows because, possibly, a given stock simply did not exist before a given date. This is especially true for higher number of stocks (since the more stocks you pick the higher the probability of picking one that was born recently) and for the higher the years of investments you simulate on (since it is more likely the period on which you compute the rate of returns on will include dates on which the stocks did not exist);
- This means that, sometimes, you are not able to append any row to your df (point 4 of the [Simulator Pseudocode](#simulator-logic)) and you have to keep on looping through your data, **causing the simulation time to increase**. The condition I imposed to append a row is that the maximum number of null columns (i.e. of null returns) in the given row has to be 1 meaning that, considering 11 stocks, each of the rows of the final df will have at least 10 stocks for which it was possible to compute a return on k = 5 years.

For clarity, the performance of the simulator that is plotted in the picture from this section was tested without taking into account this randomness. As a matter of fact, the tests aimed at verifying how fast my code was at looping through the (nr_years, nr_stocks) combinations and at computing returns knowing that, the faster it was at doing so, the faster we would be able to append non-null rows to the final df.
##### Some quick notes about the Pandas code optimization 
- **ver_1.0**: its performance is not plotted because it is the very basic prototype of the portfolio simulator, unable to loop through the test cases and capable of computing returns just for a speicific (nr_years, nr_stocks) combination;
- **ver_2.0**: this version achieves what the previous could not: by dynamically creating columns, it is able to loop through the test cases;
- **ver_3.0**: in it I avoid a for loop and I use ufuncs instead to compute returns;
- **ver_4.0**: in it I introduce and modify some checks at the beginning of the code that allow me to avoid running the whole simulation once I spot an empty and soon-to-be appended df;
- **ver_4.05**: this version avoids copying dfs as much as possible and, instead, makes use of the .loc operator;  

It is worth noticing that the best Pandas version achieved a `"real life" simulation time of 85 minutes for a one million rows df.
##### Some quick notes about the Polars code optimization 
- **ver_5.0**: my first attempt at Polars-izing the pandas code. The code is not very polished but still impressively faster than the very best Pandas version. `Total "real life" simulation time: 43 minutes;
- **ver_5.1**: this version starts to make use of the lazy frames from Polars in several parts of the code. `Total "real life" simulation time: 41 minutes;
- **ver_5.105**: in it I try to keep the df lazy for as long as possible. `Total "real life" simulation time: 38 minutes;
- **ver_5.2**: in order to have a lazy df for even a longer time than in the previous version, I remove some of the checks performed at the beginning of the code that were introduced in **ver_4.0**. `Total "real life" simulation time: 32 minutes;
- **ver_5.3**: in this version I get the best of both worlds: I introduce again the checks at the beginning of the code from **ver_4.0**, whilst keeping the df lazy for as long as possible. `Total "real life" simulation time: 25 minutes.  

The fact version 5.2 is faster than 5.3 at testing the base cases but slower "in real life" is, I think, due to the fact that the performance test is not able to replicate the effect that randomness has on the simulations: by performing the checks from version 4.0 at the beginning of the code, I am able to avoid some expensive computations that occur later in the simulation cycle. Even though the checks might slow down a non-random simulation, they surely speed up a simulation in which you might randomly get a lot of null rows.

Overall, the performance improvement achieved by using Polars is impressive. From version 2.0 to 5.3, the simulation time was reduced by more than a 30x factor when performance testing. 
Furthermore, the same can be said about randomness-affected "real life" conditions: the very best Pandas code took 85 minutes while Polars took just 25 minutes to do the same operations. It is worth stressing the fact that I am in no way a Polars expert, whilst I have several years of experience using Pandas, thus I think my code in Polars is fairly more inefficient than the one written in Pandas and this makes Polars feats even more impressive.
#### Data Analysis
##### Some comments about the analysis setup
As stated before, the goal of this project is to visualize how investments are affected by the financial tool choice, by the amount of time you invest your money for and by the portfolio size. The data analysis will compare the following situations:
1. An investment on a varying amount of stocks;
2. An all-in investment on a global index (i.e. on a world ETF).

For what concerns point 1, the simulations were performed so that the initial amount invested was divided and equally weighted among the different stocks. This means that, given one invests 1000 euros on 2 stocks, 500 euros are invested in each of them. 

The latter point is important in order to interpret the simulations results: as stated [here](#unavoidable-randomness-slows-down-the-simulation), since during simulations I store rows containing at least a (nr_stocks-1) amount of stocks, thus the "bins" in the plots have to be interpreted as going from n-1 to n. For example, the nr_stocks = 11 bin contains simulations performed on rows containing 10 or 11 stock returns. 
Furthermore, when a stock is missing, the amount of money that is invested is redistributed among the other non-missing stocks. EX: if one invests 1000 euros on 11 stocks but a stock is missing returns, for the sake of the simulation I will force the investment to be equally weighted on 10 stocks (100 euros each). 
##### This analysis favors stocks
The way the simulator works, it favors stocks in 3 ways:
- First, during the simulation I analyse data "in hindsight", using the data that still exist today. This means that, since I downloaded NASDAQ stocks tickers in 1Q-2025, I only have data about stocks that still exist atm and I do not have evidence about delisted stocks, thus I cannot model the risk of investing in something that is not on the market anymore at the time of the analysis. 
  This is favoring the stocks because I can simulate returns just on the stocks that performed decently enough not to be delisted from the stock exchange;
- Second, since [unavoidable randomness slows down the simulation](#unavoidable-randomness-slows-down-the-simulation), I had to consider a range of years of investments that did not cause my simulation time to explode. As explained in [this section](#unavoidable-randomness-slows-down-the-simulation), the longer the considered period of time, the higher the probability of finding null rows, thus the need to "cap" the years of investments to 5 years. As explained by Paolo in several of his analyses, ETFs perform better on the longer time period (>=10 years), thus we are considering periods of time that are not optimal for their performance;
- As explained in the last paragraph of the previous section, I am redistributing the investment on the stocks that do not have null returns, thus I am picking stocks that existed for a longer amount of time (this is especially true for increasing values of nr_years). Consequently, it would be fair to say that these stocks belong to a better performing cluster since they existed for a longer period of time while avoiding being delisted.

With this said, let us look at some cool plots.
##### Probability stock returns > ETF returns
###### plotnr12

[Index](#index) | [Prev plot](#plotnr11) | [More plots](#plotnr13) 
![image](https://github.com/user-attachments/assets/8cd0283a-60cb-4e3f-9ec5-5e86287e324f)

As for the plots that will follow, the heatmap above was created on about 5 millions data points (i.e. df rows). Since there are 48 (nr_years, nr_stocks) combinations, about 100k data points for each of them were used in the data analysis.

The first thing that is evident is that the highest probability in any of the settings is 48%. To put it in another way, independently on the number of years and on the number of stocks considered, ETFs have more chance of producing higher returns.
Furthermore, it is possible to spot two trends on the plot:
1. The higher the number of stocks the worse the performance of the stock investment gets when compared to the ETF one;
2. From 0.25 to 3 years, especially for higher number of stocks considered, the performance of the stock investment gets worse.

Overall, the "ETF and chill" strategy seems far superior: by investing in a single financial tool you always get a higher probability of having higher returns, without being affected by the crazy volatility that characterize an investment in stocks (especially true for lower nr_stocks or nr_years values).
In my opinion, the (relatively) good performance of the stock investments for portfolio of moderate sizes (top/top-left part of the plot) are due to the higher effect of high-growth stocks/bullish market conditions on the returns. This is even truer for a shorter investment period: as time goes on, this "high-growth" effect seems to get more and more subtle, ultimately leading to bigger sized portfolios on > nr_years having a risk profile approaching the ETF one (slightly better performance in the lower-right part of the plot). This very last phenomenon might be also due to point 3 from the previous section: to sum it up, I am picking the better performing stocks, especially for higher values of nr_years.

Once again, it is worth noticing that this is not the optimal setup for the ETFs, since they perform in a better way on longer time periods. Nonetheless, they outperform stocks, which is even more impressive since I did not model [the risk of companies being delisted](#this-analysis-favors-stocks).
##### Probability of returns being negative
![image](https://github.com/user-attachments/assets/12c4eefb-5294-4337-b6ba-c64dd73dd654)
![image](https://github.com/user-attachments/assets/651a26e7-bb00-4266-a44b-baad4b8fa2aa)

The heatmaps from this section show the probability the investment returns are negative in all the simulations settings. Just to be clear, "negative" means the investment returned an amount of money < than 1000 euros, the initial investment.

First and foremost, even though the color scale on the two plots might make the probability ranges look similar, the worst values in the ETF plot are green in the stocks one, meaning that the best values in the stocks plot (deep green) are in the order of the worst ones in the ETF heatmap (deep red). This is due to the nature of the financial tools which we simulated our investment on: an ETF diversifies and reduces volatility, sort of "capping" max and min returns. A stock investment offers, potentially, higher returns, the point is that higher rewards mean higher risks, thus there is a higher probability of getting lower returns as well compared to the ETF investment.

Overall, the higher the number of years an investment is made on, the lower the probability of it "being negative" and this might be due to the same two reasons justifying the good performance of the lower-right part of [the previous heatmap](#plotnr12) (on > nr_years, the risk profile of bigger sized portfolios get similar to the ETFs one and I picked the very best stocks when simulating, especially on > nr_years). 
Interestingly, the higher the number of stocks, the worse the performance of the stock investment seems to get, possibly because equally weighing the investment on a higher number of stocks might be dampening the higher returns you get if you go all-in on a smaller number of stocks performing better.  
Finally, the ETF heatmap shows that, provided you invest on ETFs for at least 3 years, the probability of getting back less money than the one you initially invested is 3% on average: only 3 investments out of 100 get "bad" results in these settings. 
###### Visualizing the probability distributions: ETFs
![image](https://github.com/user-attachments/assets/d542fe11-701e-4dd3-8d2e-c32766241b6c)
The lineplot above displays how many simulations fall in each investment return bin. Each return bin is upper-end inclusive, meaning that finding 600 as an x-axis coordinate is equivalent to considering the (500-600] euros bin. It is worth noticing that return values might be repeated due to the way the simulations were performed.

Overall, 12% of the simulations returned an amount of money < 1000 euros, in accordance with the ETF heatmap from the previous section (where you can roughly average the probabilities you find in the heatmap, since each heatmap box is computed on roughly the same amount of simulations). 
###### Visualizing the probability distributions: stocks best and worst cases
![image](https://github.com/user-attachments/assets/87af40cd-761d-4bce-a6b1-4feff42f541a)
For better readability, the x-axis ranges from 0 (the theoretical minimum possible investment return) to the maximum amount returned by the ETF investment, even in the case of the stocks plot.

As expected, the difference with respect to the previous plot is striking: this distribution seems normal and centered around 1000, whilst previously the ETF distribution had its maximum frequency at 1100. Furthermore, the "negative" returns values have fairly higher frequencies with respect to what happened with ETFs, confirming what was observed when looking at [these heatmaps](#probability-of-returns-being-negative).


###### plotnr13

[Index](#index) | [Prev plot](#plotnr12) | [More plots](#plotnr12)
![image](https://github.com/user-attachments/assets/f1d3b9b6-0c4b-448b-ad27-db53b880a035)
Picking the best and worst cases from the [stocks heatmap](#probability-of-returns-being-negative), we can visualize and compare their distribution with respect to the one referring to the whole df (black). 
In the green best case [(9 stocks, 5 years of investments)](#probability-of-returns-being-negative), the probability distribution looks fairly more spread out than in the red worst one [(13 stocks, 2 years of investments)](#probability-of-returns-being-negative). These distributions are, as expected, respectively better and worse than the black line when visually considering the probability of returns being negative. 
Looking at the red worst curve, it is centered around 800 and most of the higher frequencies are found in the negative part of it. On the other hand, the best curve shows lower frequencies in the negative part of the chart while displaying fairly higher ones in the positive part of it.
##### ETFs vs stocks: comparing best and worst performances
![image](https://github.com/user-attachments/assets/71708693-7da4-4c51-b2cc-f22a77fa7494)

Note well: for the sake of the analysis, the best and worst returns values are not repeated.

The four scatterplots above shine a light on the difference between the financial tools we are considering and confirm, once again, what was stated in the previous sections: stocks offer higher returns, but higher returns come with higher risks.
As it is possible to see on the bottom right scatterplot (**according to which I actually became millionaire one time out of 5 millions simulations!!!**), it is true that stocks offer higher returns, but the cost we pay is a **worse worst case**: comparing worst performances of both ETFs and stocks, we see that, investing 1000 euros, we get 488 euros in the worst case when we invest in ETFs. With stocks, we can lose almost all our investment, getting back just 7 euros.
#### Possible future developments
As in the previous projects, I do think that the code I wrote to perform the simulations might still be optimized, possibly allowing me to simulate returns on higher values of nr_years and nr_stocks. 
Furthermore, I think it would be cool to integrate an investment taxation section into my code, computing the amount of taxes an investor has to pay when getting money back, allowing me to compute the "real" returns of the investment.
#### Sources
- `The data regarding ETFs (i.e. world indices) come from Paolo Coletti's Github. The data about stocks from yahoo_finance.`










