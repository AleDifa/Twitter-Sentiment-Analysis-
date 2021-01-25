# Live Twitter Sentiment Analysis

This project take in Input Keywords/Hashtag and the number of tweet, generate analysis about Tweet-text for understand the sentiment (polarity) and the most common words in tweets.

```
Please enter keyword or hashtag to search: omega speedmaster
Please enter how many tweets to analyze: 75
```
>RT @BasileDesquiens: @JTTsteve Omega Speedmaster with a nylon nato strap really comfy! https://t.co/owfiEIfba7 <br>
#omega #speedmaster #351050 #sold to #collector in #evanston #il - more #watches #forsale at #watchvaultnyc...<br> 
@SteveSchmidtSES @POTUS If he had worn his similarly priced Omega Speedmas<br>....

```
df["cleaning_tweets"]=df["Tweets"].apply(clean_text)
df.head(5)
```
<img width="562" alt="1" src="https://user-images.githubusercontent.com/37181764/105693377-ef561680-5eff-11eb-929e-7cb78a5cc42a.PNG">
