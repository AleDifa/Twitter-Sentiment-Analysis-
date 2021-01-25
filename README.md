# Live Twitter Sentiment Analysis

This project take in Input Keywords/Hashtag and the number of tweet, generate analysis about Tweet-text for understand the sentiment (polarity) and the most common words in tweets.

```
Please enter keyword or hashtag to search: omega speedmaster
Please enter how many tweets to analyze: 75
```
>RT @BasileDesquiens: @JTTsteve Omega Speedmaster with a nylon nato strap really comfy! https://t.co/owfiEIfba7 <br>
#omega #speedmaster #351050 #sold to #collector in #evanston #il - more #watches #forsale at #watchvaultnyc...<br> 
@SteveSchmidtSES @POTUS If he had worn his similarly priced Omega Speedmas<br>....

```python
function for clean text, with re.sub clean all punctuation in tweets 
def clean_text(Text):
    Text = re.sub('@[\w]+', "", str(Text))
    Text = re.sub(r"[^a-zA-Z]", " ", str(Text))
    Text = re.sub(r"#", " ", str(Text))
    Text = re.sub(r"rt[\s]+", " ", str(Text))
    Text = re.sub(r"http\S+", " ", str(Text))
    return Text
```
<img width="562" alt="1" src="https://user-images.githubusercontent.com/37181764/105693377-ef561680-5eff-11eb-929e-7cb78a5cc42a.PNG">

```python
Sentiment Analysis: Polarity ranges from -1 (most negative) to 1 (most positive)
def polarity (cleaning_tweets):
    text = TextBlob(cleaning_tweets).sentiment.polarity
    return text
df["polarity"]=df["cleaning_tweets"].apply(polarity)
```
<img width="700" alt="2" src="https://user-images.githubusercontent.com/37181764/105694206-f4679580-5f00-11eb-9e58-bc07680904df.PNG">

```python
Plot scatter visualization for see the Polarity of Tweets
plt.scatter(df.polarity, df.subjectivity, color='Blue')
plt.xlabel('Polarity') 
plt.ylabel('Subjectivity') 
```
<img width="334" alt="3" src="https://user-images.githubusercontent.com/37181764/105694463-490b1080-5f01-11eb-9aa8-2163a58047d8.PNG">

```python
plot number the count of value with bar chart
df['rating'].value_counts().plot(kind = 'bar')
plt.show()
```
<img width="338" alt="4" src="https://user-images.githubusercontent.com/37181764/105695460-68566d80-5f02-11eb-9ca1-8be4df733e27.PNG">

```python
Tokenization our dataframe
df['tokenized_sents'] = df.apply(lambda row: nltk.word_tokenize(row['cleaning_tweets']), axis=1
```
<img width="555" alt="5" src="https://user-images.githubusercontent.com/37181764/105696065-1c57f880-5f03-11eb-8a82-0cae650f8697.PNG">

```python
Most common words in Horizontal bar chart
fig, ax = plt.subplots(figsize=(8, 8))
Clean_df_counts_no_urls.sort_values(by='count').plot.barh(x='words',
                      y='count',
                      ax=ax,
                      color="purple")
```
<img width="421" alt="6" src="https://user-images.githubusercontent.com/37181764/105696385-87a1ca80-5f03-11eb-8d9e-a20d4b1ca255.PNG">

```python
An n-gram is a subsequence of n (n°3 trigram) elements of a given sequence
n3_trigrams = get_top_n_gram(df['cleaning_tweets'],(3,3),20)
```

<img width="236" alt="7" src="https://user-images.githubusercontent.com/37181764/105696593-cfc0ed00-5f03-11eb-9146-041263c44279.PNG">


