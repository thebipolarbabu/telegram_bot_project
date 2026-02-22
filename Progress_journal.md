20-2-2026
Friday

Since the last week, I have been working on this project. Last week I was able to create a telegram bot and assign basic commands, and then I moved on to the data collection stage of the project. This required the use of specialized apis which could extract news articles from the internet.

Trial 1 : Newapi
This trial worked for the most part, except that the results were not relevant and it had constraints due to a paywall.
Verdict - fail

Trial 2 : mediastack
This trial was not working well with certain sources, and the query mechanism was not good, with only a "categories" parameter. Very few articles returned
Verdict - fail

Trial 3.1 : google custom search api
This trial did not work, showing the error 403 "forbidden url" when I tried pulling data from a specified source.
Verdict - fail

Trial 3.2 : google custom search api
This trial did not work either, despite me following multiple tutorials exaxctly as shown. I realised the issue was in the search engine key created, so I created a new one. This time I tried to choose the "explore entire web" option but it was not available. I searched about it and found out that google discontinued this service as of jan 20 2026, and that I was a month late.
Verdict - fail

Trial 5.1 : Duckduckgo search engine
This was free to use and didn't even need any api credentials. I was able to easily get desired kind of results.
Drawbacks
    -Number of results vary even if you specify a max number, they vary within that range.
    -Some irrelavent articles still make it in.
    -Need to filter out websites that have a paywall.
    -Can't put multiple keywords in a list form. Need to retrieve articles seperately for each keyword in that case.
Outcome : Links, Titles, Subtitles obtained for news articles
Verdict - success

Trial 5.2 : newspaper3k package by Lucas Ou-Yang
It is an article scraping and curating tool that basically accepts a url and downloads the article as a whole into an object with different attributes like title, body, source, author, etc. It was very useful in retreiving the text from the many articles.
Precaution : just put the text retreival block in a try block. the websites with paywalls don't allow scraping. so the program stops midway and you'll need to re run from the start. placing it in a try block makes it so that the results obtained, when stored in the dataframe, will be null for the paywall websites. you can easily drop them using df.dropna.
Outcome : text from the articles obtained.
Verdict - success

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------

22-02-2026
Sunday 8:13 am
The first successful fact check

I tried to tokenize the words from the text data of news articles collected. I was figuring out how to get rid of filler words and irrelevant words. Then I got to know they are called stop words and they are built into a file in nltk so I used them to filter out relevant words.
After doing all this I realized, individual words will not have any meaning, I mean individual sentences have half the meaning left out because of lack of context. So I thought I should try tokenizing sentences.
I looked up sentence tokenizer in nltk and sure enough, it exists, so I tried with it. For some reason it wouldn't work and I couldn't understand why, so I switched to spaCy
In spaCy the installation of the package and the nlp model took a lot of time. I sat down at around 6:45 and it took me till about 7:40 to successfully install them. The reasons were pip not being up-to-date, cache being full with previous attempts to install, etc. Finally I could use them.
I tokenized the sentences and compared them to the claim.
I stored the comparision scores in a pandas series. That way I could perform operations easily.
First I tried finding which sentences match most. But after looking at the results I realized it was irrelevent because they did not make sense out of context.
Then i resorted to checking the range that mean of the similarity score falls into. If it is greater than 0.75, it is more likely to be true. Else more likely to be false. Naive logic, and a pretty high margin, so I will need to work on it.

I also still need to work on streamlining the data filtering process.

Things to work on :
- Streamline datafiltering process after extraction
- Work on a better logic to give the verdict, base it on real statistical proofs.

YAyyyyAYayayayayaayay I did it !!!!!!!!!

Next step : Integration of the basic model with the bot.