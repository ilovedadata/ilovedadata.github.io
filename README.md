# Hi everyone 👋, I am ilovedadata, I am a developer and I LOVE diving into data and programming 💻.
This website is about some of the projects that I completed and the skills that I learnt in my **neverending** journey to become a better dev✌️.

# Index

[Project 1](# project-1:-italian-superball-simulator)

[Project 2](# project-2:-funky-stats-about-naruto)

[Project 2](# project-3:-house-terminal-inventory-system)

## Project 1: Italian Superball simulator 💸 
`#Python` `#DataScience` `#DataAnalysis` `#Numpy` `#Pandas` `#Matplotlib` `#Statistics` `#Probability` `#Random` 

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
- `The data regarding probabiities and prizes come from the official superenalotto website at https://www.superenalotto.it/quanto-si-vince/calcolo-probabilita` 
## 

## Project 2: Funky Stats about Naruto 🦊 
`#Python` `#DataScience` `#DataAnalysis` `#Numpy` `#Pandas` `#Matplotlib` `#Statistics` `#HTML` `#ReverseEngineering` `#BeautifulSoup`
 `#Japanese` 

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
    ![TopFlop10](https://github.com/ilovedadata/ilovedadata.github.io/assets/106730909/3b0249ab-ed51-46ef-b1e1-0c0b821932fc)
    
    **6. What is the most present word in Naruto plots? Exclude English stopwords and punctuation signs**
    
    A tricky question to answer: in order to do so, the plots of the episodes were scraped from https://en.wikipedia.org/wiki/Naruto in a similar fashion to what was done before for extracting information about the characters and dubbers in each episode. The dataframe is structured as follows:
  
   | Index | Plot | 
   | ------------- | ------------- | 
   | 0 |	Naruto Uzumaki is a twelve-year-old ninja livi... | 
   | 1 |	While Naruto gets into an argument with Hiruze... |
   | ... | ... | 
   | 219 | The battle concludes with Gaara killing Seimei... | 
    
    Once stored, the plots have then been splitted into list of strings, from which English stopwords and punctuation signs have been excluded. In the end, plotting the results meant obtaining the following plot:
    ![words in plots](https://github.com/ilovedadata/ilovedadata.github.io/assets/106730909/331c5728-66ea-4fef-8bd2-2dc0ffcd1358)
    Unsurprisingly, 4 out of the top 5 words are first names of the Anime main characters, namely Naruto, Sasuke, Lee, Sakura. The first non-first-name words that are found are team, ninja, attack, battle and fight which, once again, makes sense: the anime is about the ninja world, ninjas are organized in teams and fights are pretty much central throughout the whole anime.

#### Possible future developments
The code and the structures that were used to analyze the data about the Anime can be easily adapted to perform other analyses of this kind. For instance, one could go on and analyze the episodes for Naruto Shippuden and Boruto, which are both sequels to Naruto the anime. In fact, I already stored information about the characters and the dubbers of these two Animes in two dataframes (structured as the one that is found in the Episodes scraping section) and, in the future, I might come back to expand the analysis that I performed on the first anime to both Shippuden and Boruto.

#### Sources
- `The data about the characters and their dubbers in each episode comes from the Naruto fandom website https://naruto.fandom.com/wiki/List_of_Animated_Media` 
- `The kanji stroke counts are found at https://en.wikipedia.org/wiki/List_of_j%C5%8Dy%C5%8D_kanji`
- `The plots of the episodes of the anime are at https://en.wikipedia.org/wiki/Naruto`

## 

## Project 3: House terminal inventory system 🏠
`#Python` `#DataScience` `#DataAnalysis` `#Numpy` `#Pandas` `#Fallout` `#Random` 
 
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
![FalloutTerminal](https://github.com/ilovedadata/ilovedadata.github.io/assets/106730909/3d9c1c99-4075-45ac-9761-4225fe331013)

#### Possible future developments
A possible future development might be deploying this script as an app for my mobile, so as to be able to run it from a more comfortable "access point": I am still lazy and turning on my PC takes some effort (:smile:)
