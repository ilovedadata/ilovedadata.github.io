# Hi everyone 👋, I am ilovedadata, a self-taught dev into data and programming 💻.
This website is about the projects I love doing in my free time and about the things I learn while I struggle to become a better dev ✌️.
[Project 1](# project-1:-italian-superball-simulator)

## Project 1: Italian Superball simulator 💸 
`#Python` `#Numpy` `#Pandas` `#Matplotlib` `#Statistics` `#Probability` `#Random` 

#### Project description and goal
The project is about the **"Italian powerball" (superenalotto)**, a game in which 8 numbers are drawn and prizes are won depending on how many numbers you guessed right. 7 numbers make up the "standard" ticket the user buys (6 numbers + the so-called **jolly number**, allowing you to score a particular combination: the "5+1"), the eight number is the so-called **superstar number** and can be purchased at an additional 0.50$. The **goal** of this project is to create a realistic game simulator which takes into account the probabilities associated with the wins and the amount of money spent/gained. Thanks to the use of **Data science/Data analysis tools**, dataframes were created to store the drawings and interesting stats about the game were analyzed and plotted.
#### Code structure
The code is made up by 4 main sections:
* **Functions section**:

   the **dollars function** returns an amount of dollars given a number;
   
   the **binomial coefficient** function is needed to compute the probability of scoring 0 or 1 without a Superstar number (these probabilities are not provided on the official Superenalotto website);
   
   the **spent/won function** returns the amount of money a user spends and wins given the times he plays and whether he plays a Superstar number or not.

   Finally, the user is asked whether he wants to play a **superstar number** or not.
   
* **Inputs and Structures section**

   the parameters for the drawings are initialized, for example: the amount of numbers that can be drawn, the number of tickets played by the user and the number of drawings in which the user wants to play his number of tickets;
   
   two dictionaries are created to store the drawings count: the first dictionary is needed to count how many times a combination is drawn without considering the superstar number whilst the second dictionary counts the times a combination is drawn considering the superstar number. Obviously, the second dictionary will get values > 1 only when the user plays a superstar number;
   
   three dataframes are created to store different data: the first stores the probabilities and the prizes associated to a combination drawing. The bigger the prize the lower the probability of winning and... wanna hear a (not so) **crazy stat**? `19/20 times you are going to lose`. The second dataframe (in fact, there are two different dataframes that serve this purpose) is needed to store the numbers as they are drawn. The third dataframe counts the times a number is drawn as "normal" number, as a Jolly or as a Superstar.
   
* **Script section**
The script section is where the **magic** happens. Every ticket played by the user is compared to the drawn numbers. Both the user's ticket and the drawn numbers are **randomly** generated and, once they are compared, they are stored inside the dataframes created before so as to store data to generate **interesting plots** (I mean, who doesn't love plots? 📊).  

* **Plotting section**
