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
function for clean text 
def clean_text(Text):
    Text = re.sub('@[\w]+', "", str(Text))
    Text = re.sub(r"[^a-zA-Z]", " ", str(Text))
    Text = re.sub(r"#", " ", str(Text))
    Text = re.sub(r"rt[\s]+", " ", str(Text))
    Text = re.sub(r"http\S+", " ", str(Text))
    return Text
```
<img width="562" alt="1" src="https://user-images.githubusercontent.com/37181764/105693377-ef561680-5eff-11eb-929e-7cb78a5cc42a.PNG">

```
Sentiment Analysis: Polarity ranges from -1 (most negative) to 1 (most positive)
def polarity (cleaning_tweets):
    text = TextBlob(cleaning_tweets).sentiment.polarity
    return text
df["polarity"]=df["cleaning_tweets"].apply(polarity)
```



