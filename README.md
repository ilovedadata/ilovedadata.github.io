# Hi everyone 👋, I am ilovedadata, I am a developer and I LOVE diving into data and programming 💻.
This website is about some of the projects that I completed and the skills that I learnt in my **neverending** journey to become a better dev✌️.
[Project 1](# project-1:-italian-superball-simulator)

## Project 1: Italian Superball simulator 💸 
`#Python` `#Numpy` `#Pandas` `#Matplotlib` `#Statistics` `#Probability` `#Random` 

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

![Figure_1](https://user-images.githubusercontent.com/106730909/216787470-9213e1fb-1553-4c15-9671-846cd141eb38.png)

   As a design choice, combinations from "2" upwards are shown, even though, when playing superstar, the user can win scoring just 1 or 0. Nonetheless, when computing the amount of money won by the user, such combinations (0+superstar, 1+superstar) are taken into account. Furthermore (and since it took me quite a bit of time it's only fair I state it 👀) a custom labelling process has been implemented in order to label the histogram plot on the left exactly above each and every histogram column, respecting the color palette. For what concerns the plot on the left, it will be useful to draw some conclusions. The plot on the right shows that no clear patterns are present in the drawing of numbers (which is random!), something that has been confirmed during the different simulations I performed.

#### Conclusion

In order to draw some conclusions, let us analyze the plot on the left. This plot represents the "average" situation I found when playing with this simulator: a **lot** of times the user wins minor prizes (such as 2 or 3), rarely he scores a "4" (it happened to me at most 3 times during a simulation whilst playing the same amount of schedine we played in this simulation: needless to say, even scoring 3 "4" is not enough to cover the tickets expenses). In addition, in my experience the user never scored a 5 or a 6 and he/she never gained money: the amount of money spent on tickets has always been higher than the one gained through prizes. This becomes even more impressive when you consider the following: the plots above have been computed for a non-realistic (at least, I hope) situation: `a user that plays 70 tickets 3 times a week for a year, spending almost 17000$ in tickets, losing 12000$. What is even more crazy is that this user has been lucky: according to statistics, the times the user won (approx 0.06%) are higher than the ones he should have (approx 0.05%)`. 
This shows how unrealistic the expectation of winning big (or even winning small!) at the lottery is!

#### Possible future developments
The structures and scripts used in this project can possibly be used in the future to simulate other kinds of gamble games/casino games. One such application could be creating a simulator for the "true" Powerball (i.e. the American one) or the roulette game.

#### Sources
`The data regarding probabiities and prizes come from the official superenalotto website at https://www.superenalotto.it/quanto-si-vince/calcolo-probabilita`


## Project 2: Funky Stats about Naruto :cyclone: 🦊 
`#Python` `#DataScience` `#DataAnalysis` `#Numpy` `#Pandas` `#Matplotlib` `#Statistics` `#Naruto` `#BeautifulSoup #Japanese` 

#### Project description and goal
The project is about the **"Italian powerball" (superenalotto)**, a game in which 8 numbers are drawn and prizes are won depending on how many numbers you guessed right. 7 numbers make up the "standard" ticket the user buys (6 numbers + the so-called **jolly number**, allowing you to score a particular combination: the "5+1"), the eighth number is the so-called **superstar number** and can be purchased at an additional 0.50$. The **goal** of this project is to create a realistic game simulator which takes into account the probabilities associated with the wins and the amount of money spent/gained. Thanks to the use of **Data science/Data analysis tools**, dataframes were created to store the drawings and interesting stats about the game were analyzed and plotted, in order to answer a simple question: `can I win big at the lottery?`

#### Code structure


#### Conclusion


#### Possible future developments


#### Sources
`The data regarding probabiities and prizes come from the official superenalotto website at https://www.superenalotto.it/quanto-si-vince/calcolo-probabilita`
