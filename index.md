## How favorable are countries to the USA ? 

### PEW analysis, what does it says ? 

Pew Research Center is an American center that conducts public opinion polling to analyze the issues, attitudes, and trends shaping the world. They study a wide range of topics such as politics, immigration, ethnicity, religion, economy, and science. One of the principal subjects in these researches is U.S. global image and reputation, i.e., what people around the world like about American society and politics. In Pew's survey, random people worldwide are asked to express an opinion of the U.S. The provided choices are "Very favorable," "Somewhat favorable," "Somewhat unfavorable," "Very unfavorable," "Refused," and "Don't know." The pew research center releases the results of this study once per year.
In this work, we extract the U.S. favorability from the PEW datasets for 2015-2020, the same years that we have data in QuoteBank.  
The following figure shows the average of the U.S. favorability in different countries every year. The blank boxes represent the years that the study is not conducted in that specific country.

![PEW_Heatmap](/pew_heatmap.jpg)

As we see in this heatmap, the study covers only 52 out of 195 countries in the world. In addition, only 9 countries in this study have the results for all the years between 2015 till 2020. 

### Quotebank : what does it says ? 

The map plus does not match 

### Are the two data sources comparable

Trump and obama 

### This is an issue ? Could we improve comparability ? 

#### Sentiment analysis tool 

Until now, all the sentiment analysis has been done using the Natural Language Toolkit (NLTK) library. This is a referene for sentiment analysis, but many other tools are available, and could potentially help up improve our results. It is indeed possible that the NLTK tool does not apply well to our data and some other would better analyse the Quotebank citations. 

To verify this, a random sample of quotes was extracted and a sentiment score (-1, -0.5, 0, 0.5, 1) was assigned by humans to each quote. The different tools were then tested on the sentiment score were compared. The tools used were : NTLK, Flair, and TextBlob. The accuracies are shown below : 

| | NLTK | TextBlob | Flair | 
|-------|:-------:|-------|-------| 
|Accuracy| 54 % | 42 % | 66 % |



NLTK is thus not the most accurate tool for the data at hand, as its accuracy was of 54% compared to Flair, with 66%. This missmatch in sentiment might be a reason for the discrepencies between the PEW and Quotebank analysis. Using Flair instead could potentially be a good change. However, the FLzir accuracy is still quite low, so it will still incurr some uncertainties, albeit at a lower scale. 

#### Keyword enrichment

#### Reducing bias : Media sources

A first possible source of bias lies I the medias. Indeed, even if attempting (or not) to be impartial on the subjects treated, articles are still written by humans and carry thus some point of view and the question treated. For this reason, it is possible that the quotes included in articles are selected to fit a narrative, discarding the quotes going in a opposing direction, incurring bias in the quotation corpus that is Quotebank. 

The same phenomenon could also occur at the media level. Media have clear political, social, or geopolitical views which can also lead to a selection process of quotations. Therefore, when applying sentiment analysis on quotes from these sources, the sentiment could be intensified and lead to bias in our analysis.
Identifying media with such behaviour is thus important as eliminating them could provide better data for the project. It could make the analysis go from “how favourable are countries to the US as seen by medias?“ to “how favourable are countries to the US” .

A media bias could be regarding the target of the sources : the US1. Some medias could keep only positive or negative quotes about the USA making their sentiment score reach more extreme values. One could assume that if this is not the case, positive and negative sentiment could approximatively even out, leading to a median score in the vicinity of 0. 

The median sentiment and distribution of the 30 most common medias are plotted below : 

![Mean sent](/mean_sent.PNG)

We can see that most of them indeed have a media score in the vicinity of 0, going from about -0.1 to 0.3. There is however one media that seems to stand out, with a much higher sentiment score beyond  0.4. This media is Einnews and it thus seems to have a different perception of sentiment towards the US. 
This distinction is further made statistically significant with a mean p-value of 1.25*10^-16 when doing a t-test between its distribution and the distribution of all the other medias. This is further enhanced by the p-value heatmap shown below. Einnews is indeed the only media with no p-values above 0.05 for any of the other medias. It is true that some other medias seem to have low link to the others, but they still have a p-value over 0.05 with at least one other media. 

![Heatmap_pval](/pval.PNG)

 It is thus clear that the quotation sentiment from Einnews does not come from the same distribution as the others, and looking at its higher median sentiment, it seems that it infers a positive bias towards the USA. Filtering this media out could therefore lead to improved results and a dataset more comparable to the PEW data. 


### Reducing bias : Speaker importance

### Is it better now ? 

Trump vs Obame v2

### Good, now, what do we learn from quotebank on US favorability across the world ? 

New sentiment 

Political vs cultural

Most common topics

<iframe src="final_map.html" style="width: 1000px;  height: 400px; border: 0px"></iframe>
