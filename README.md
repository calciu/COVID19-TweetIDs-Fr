# COVID19-TweetIDs-Fr

For the associated research paper see (will follow ...)

This repository contains an ongoing collection of tweets IDs containing French language tweets extracted from a bigger dataset (available at https://github.com/echen102/COVID-19-TweetIDs).

To comply with Twitter’s [Terms of Service] (https://developer.twitter.com/en/developer-terms/agreement-and-policy), we are only publicly releasing the Tweet IDs of the collected Tweets. The data is released for non-commercial research use. 

Additionally we release annotations of this corpus using sentiment and emotions mesurement instruments. This allows researchers to evaluate the capability of these tools to capture variations of émotions expressed by people.

## Data Organization
### Tweet Sentiment and Emotion Annotations Files
Sentiment and Emotion Annotations files (in .csv format) are available in the CovidAnnot folder. Their names have the following pattern method_month_chunk.csv (method is nrc,lsd or emoji). 


#### nrc1-5fr.csv, nrc6fr.csv, ...
Nrc files contain ten columns: the first eight represent emotions frequencies and the last two sentiments frequencies per tweet

| anger | anticipation | disgust | fear | joy | sadness | surprise | trust | negative | positive |
| ----: | -----------: | ------: | ---: | --: | ------: | -------: | ----: | -------: | -------: |
|     0 |            0 |       0 |    0 |   0 |       0 |        0 |     0 |        0 |        0 |
|     0 |            0 |       0 |    1 |   0 |       0 |        1 |     0 |        3 |        0 |
|     1 |            1 |       0 |    2 |   1 |       1 |        1 |     4 |        2 |        2 |
|     0 |            1 |       0 |    2 |   0 |       1 |        0 |     0 |        1 |        0 |

#### lsd1-5fr.csv, lsd6fr.csv ..
Lsd files contain four columns negative and positive sentiment frequency, number of words and identification number of the tweets
    
| Neg\_lsdfr | Pos\_lsdfr | nb | id |
| ---------: | ---------: | -: | -: |
|          0 |          0 |  1 |  1 |
|          0 |          0 | 20 |  2 |
|          0 |          1 | 38 |  3 |
|          1 |          1 | 26 |  4 |


#### emoji1-5fr.csv, emoji6fr.csv, ...
Emoji files contain five columns. The first is a list of emojis separated by ";", the second indicates the number of emojis per tweet. The other three indicate the minimum, average and maximum sentiment score (on a scale from -1 to 1) 


| emoji  | nemoji | min\_sentsc | mean\_sentsc | max\_sentsc |
| :----- | -----: | ----------: | -----------: | ----------: |
| ;      |      0 |          NA |           NA |          NA |
| 😂;😂;😂; |      3 |       0.221 |       0.2210 |       0.221 |
| 📷;     |      1 |       0.430 |       0.4300 |       0.430 |
| 😆;😅;🤣; |      3 |       0.178 |       0.2935 |       0.409 |

#### helper files to associate annotations to tweets and their text (ids, date & twtype)
There are also three kinds of hepler files that allow for associations between not publishable tweets contents and annotations. They are headless one column .csv files and their prefix ids, date and twtype indicate the additional information they contain.
  - ids*.csv files contain the unique tweet identitiers that might be associated to each annotation.
  - date*.csv files contain the parsed date of each tweet corresponding to each annotation.
  - twtypoe*.csv files contain the type of each tweet corresponding to each annotation (original, quote, reply and retweet)

### Tweet IDs files 

The Tweet-IDs that help recover (hydrate) all collected datasets are organized as follows:
* Tweet-ID files are stored in one folder called CovidIds.
<<<<<<< HEAD
* The file names have the following pattern: a prefix “coronavirus-tweet-id" followed by "-yyyy-mmfr-ids(_chunk).txt” where yyyy is the year (2020), mm is the month (O1 for january etc). Occasionnally there might be chunk numbers if the original monthly files have to be split into chunks if they exceed the 25 Mb github limit.
=======
* The file names have the following pattern: a prefix “coronavirus-tweet-id" followed by "-yyyy-mmfr-ids(_chunk).txt” where yyyy is 2020, mm is the month (O1 for january etc), optionnally there might be chunk numbers if the original monthly files have to be split into chunks if they exceed the 25 Mb github limit.
>>>>>>> c478fb3306b9813000387e9e02fac028547e3c78

## Notes About the Data
A few notes about this data: 
* We will be continuously maintaining this database for the foreseeable future, and will be uploading new data on a weekly basis.  
* We will keep a running summary of basic statistics as we upload data in each new release. 
* Consider using tools such as the [Hydrator](https://github.com/DocNow/hydrator) and [Twarc](https://github.com/DocNow/twarc) to rehydrate the Tweet IDs. Instructions for both are in the next section. 
* Hydrating may take a while, and Tweets may have been deleted since our initial collection. If that is the case, unfortunately you will not be able to get the deleted Tweets from querying Twitter's API.

## How to Hydrate

### Hydrating using [Hydrator](https://github.com/DocNow/hydrator) (GUI)
Navigate to the [Hydrator github repository](https://github.com/DocNow/hydrator) and follow the instructions for installation in their README. As there are a lot of separate Tweet ID files in this repository, it might be advisable to first merge files from timeframes of interest into a larger file before hydrating the Tweets through the GUI. 

### Hydrating using [Twarc](https://github.com/DocNow/twarc) (CLI)
Many thanks to Ed Summers ([edsu](https://github.com/edsu)) for writing this script that uses [Twarc](https://github.com/DocNow/twarc) to hydrate all Tweet-IDs stored (in their corresponding folders). 

First install Twarc and tqdm
```
pip3 install twarc
pip3 install tqdm
```

Configure Twarc with your Twitter API tokens (note you must [apply](https://developer.twitter.com/en/apply-for-access) for a Twitter developer account first in order to obtain the needed tokens). You can also configure the API tokens in the script, if unable to configure through CLI. 
```
twarc configure
```

Run the script. The hydrated Tweets will be stored in the same folder as the Tweet-ID file, and is saved as a compressed jsonl file
```
python3 hydrate.py
```

## Data Usage Agreement
This dataset is licensed under the Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International Public License ([CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/)). By using this dataset, you agree to abide by the stipulations in the license, remain in compliance with Twitter’s [Terms of Service](https://developer.twitter.com/en/developer-terms/agreement-and-policy), and cite the following manuscript: 

Sophie Balech, Christophe Benavent, and Mihai Calciu (2020), The First French COVID19 Lockdown Twitter Dataset, arXiv:2005.05075 [cs.SI]

<<<<<<< HEAD
## Statistics Summary (v0.1 11 Months up to November 31 2020)
Number of Tweets in French : ** 16,404,102 **
=======
## Statistics Summary (v0.2 55 Lockdown days up to May 11 2020)
Number of Tweets in French: **  16,404,102 **
>>>>>>> c478fb3306b9813000387e9e02fac028547e3c78

| Month | No. tweets | % total tweets |
| -------: | --------: |---------: |
| 1| 61918| 0,38% |
| 2| 560829| 3,42% |
| 3| 756954| 4,61% |
| 4| 520674| 3,17% |
| 5| 354232| 2,16% |
| 6| 943056| 5,75% |
| 7| 1025250| 6,25% |
| 8| 1357073| 8,27% |
| 9| 3286953| 20,04% |
| 10| 4080225| 24,87% |
| 11| 3456930| 21,07% |

# Inquiries 
If you have technical questions about the data collection, please contact Mihai Calciu at **mihai.calciu[at]univ-lille[dot]fr**.

If you have any further questions about this dataset please contact Christophe Benavent at **christophe.benavent[at]gmail[dot]com**.
