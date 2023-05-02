# Linguistic Variation in Goodreads Reviews by Genre - Final Report

## Background

As an avid reader, I'm familiar with the variety of different genres of books available, all with their unique styles, storylines, and uses of language. Different genres appeal to different people; everyone has their personal preferences. According to a 2020 consumer behavior report on media intake, genre is the #1 most important factor for people buying books, especially among consumers from younger generations, like Gen-Z (Noorda & Berens, 2021). This suggests that people have strong preferences for the genres they like to read - there is a strong connection between the personal and the genre. Given this info, I began to wonder if the language used by readers of certain book genres would reflect the language used in the book genres themselves?

This type of investigation is related to the larger Natural Language Processing subfield of linguistic profiling, which is a field of research that focuses on identifying a characteristic of a text based on its linguistic features. This could involve tasks such as first-language identification, author identification, or, as in my case, genre identification (Mendhakar, 2022). In this project, I investigate what linguistic differences exist in the reviews of different book genres and then use those features to see if they are significant enough to identify the genre of the book being reviewed. 

## Data

My found data was from [UCSD's Book Graph corpus](https://sites.google.com/eng.ucsd.edu/ucsdbookgraph/home), which consisted of over 15 million scraped public reviews from Goodreads' website subset into 8 different genres. The corpus also included additional files with metadata on the reviewed books, their authors, and their genres. In order to handle the large amount of data, I shuffled each genre's reviews in command line and sampled 5,000 random reviews from each genre for a total of 40,000 reviews.

Once the data was loaded, I began processing the data by merging the review data with the relevant metadata for some additional background information per review. After this, the real data processing began. I started with just one genre, [Children's Literature](https://nbviewer.org/github/Data-Science-for-Linguists-2023/Goodreads-Genre-Reviews-Analysis/blob/main/Data_Exploration.ipynb#Children%27s-Literature-Data), where I experimented with different processing techniques in order to find a system that worked before applying that to the rest of the genres. Some factors I had to consider were empty reviews, langauge, and nonsense text. 

At first glance, the data appeared perfectly clean with no null values. However, further investigation proved that this was because missing values were often filled with [empty strings](https://nbviewer.org/github/Data-Science-for-Linguists-2023/Goodreads-Genre-Reviews-Analysis/blob/main/Data_Exploration.ipynb#Formatting), so I had to filter the data for reviews with no text and remove them. There were also many different [langauge codes](https://nbviewer.org/github/Data-Science-for-Linguists-2023/Goodreads-Genre-Reviews-Analysis/blob/main/Data_Exploration.ipynb#Language-Filtering), so I chose to restrict the data to only dialects of English to keep things consistent. I also noticed that some reviews looked like [nonsense](https://nbviewer.org/github/Data-Science-for-Linguists-2023/Goodreads-Genre-Reviews-Analysis/blob/main/Compiling_Data.ipynb#Nonsense-Text), like they were typed by just smashing a keyboard (unintentionally).

![Nonsense Reviews Count](/Users/ashleyfeiler/Documents/data_science/datasci_repo/Goodreads-Genre-Reviews-Analysis/images/nonsense_counts.png)

However, attempts to filter them out took too many real reviews with them, and since they made up such a small portion of the data, I kept those reviews in the data. After all processing, I was left with a final dataset of 28,274 reviews from 8 different genres. 

![Genre Review Counts](/Users/ashleyfeiler/Documents/data_science/datasci_repo/Goodreads-Genre-Reviews-Analysis/images/genre_counts.png)

## Analysis

Because I was just looking for any linguistic differences, I began my analysis by looking at any linguistic feature I could think of. This included token count and length, sentence count and length, sentiment, adjective use, and k-bands. These features can in turn be reflective of different aspects of language use. For example, higher token count and average sentence length can indicate a greater mastery of the language and, for sentence length particularly, syntactic complexity in writing. 

As shown in the graphs below, reviews of Romance books had the highest [median token count](https://nbviewer.org/github/Data-Science-for-Linguists-2023/Goodreads-Genre-Reviews-Analysis/blob/main/Data_Analysis.ipynb#Token-Count) per review followed by History/Biography books. History/Biography reviews also had the highest [median sentence length](https://nbviewer.org/github/Data-Science-for-Linguists-2023/Goodreads-Genre-Reviews-Analysis/blob/main/Data_Analysis.ipynb#Sentence-Length). This indicates that readers and reviewers of History and Biography books may write with slightly more syntactic complexity, potentially with longer clause combinations. This is interesting as out of all 8 genres, History/Biography is the only real nonfiction genre. This claim would need further investigation, but this could hint at the broader generalization that readers of nonfiction write with more syntactic complexity. 

Reviews of Children's Literature, Comics/Graphic Novels, and Poetry have some of the lowest median token counts per review. Children's Literature also has some of the shortest sentences. This could correlate to the actual length of the text being reviewed. Children's books, comics, and poems are all shorter pieces of writing whereas the other genres are likely novel-length, so the shorter reviews could just reflect a shorter original text to talk about. 

![Token Count](/Users/ashleyfeiler/Documents/data_science/datasci_repo/Goodreads-Genre-Reviews-Analysis/images/tok_count_bar.png)

![Sentence Length](/Users/ashleyfeiler/Documents/data_science/datasci_repo/Goodreads-Genre-Reviews-Analysis/images/sentence_len_per_genre.png)



Additionally, high [average word length](https://nbviewer.org/github/Data-Science-for-Linguists-2023/Goodreads-Genre-Reviews-Analysis/blob/main/Data_Analysis.ipynb#Average-Word-Length) and [average k-band](https://nbviewer.org/github/Data-Science-for-Linguists-2023/Goodreads-Genre-Reviews-Analysis/blob/main/Data_Analysis.ipynb#K-Bands) can be indicators of a larger, more advanced vocabulary. Poetry and History/Biography reviews had some of the highest average word lengths. This is more evidence for nonfiction readers having a more advanced grasp of language, and it makes sense that readers of poetry would write with longer words as poetry often includes very decorative, expressive language. Along these lines, while the average k-band was fairly consistent across all genres, Poetry reviews had a slightly higher k-band than the rest. This indicates that Poetry reviewers are using slightly less common, potentially more advanced vocabulary. 

![Word Length](/Users/ashleyfeiler/Documents/data_science/datasci_repo/Goodreads-Genre-Reviews-Analysis/images/word_len_per_genre.png)

![K-Band](/Users/ashleyfeiler/Documents/data_science/datasci_repo/Goodreads-Genre-Reviews-Analysis/images/mean_kband_per_genre.png)

Some other features I investigated were sentiment and adjective use. Children's Literature reviews were the most positive overall while Mystery/Thriller/Crime reviews were the most negative. However, since the sentiment score is based on the text itself, it's understandable that someone talking about crime would use more negative words that someone talking about a children's book despite their opinion of the book, so this should be taken with a grain of salt. 

![](/Users/ashleyfeiler/Documents/data_science/datasci_repo/Goodreads-Genre-Reviews-Analysis/images/sentiment_score.png)

In terms of median number of adjectives used, there isn't a ton of variety. I was surprised that Poetry reviews used as few as they did (only a median of 4), but again, History/Biography reviews stand out as advanced by using a higher median number of adjectives per review (along with Romance). 

![Adjective Count](/Users/ashleyfeiler/Documents/data_science/datasci_repo/Goodreads-Genre-Reviews-Analysis/images/adjs_per_genre.png)

I also chose to look at the specific adjectives used in addition to just the counts, which turned out to be very revealing. Here are some of the interesting adjectives that were some of the most significant features when I made a Multinomial Naive-Bayes classifier based on adjectives: 

**Children's Literature:** adorable, simple, sweet, young

**Comics/Graphic Novels:** short, cute, comic, graphic, bad

**Fantasy/Paranormal:** long, strong, bad

**History/Biography:** hard, true, real, historical

**Mystery/Thriller/Crime:** short, dark, bad

**Poetry:** free, long, poetic, powerful, personal, beautiful

**Romance:** sexy, sweet, hot, bad

**Young Adult:** short, happy, bad

Some patterns are that Children's Literature, Comics/Graphic Novels, and Young Adult books are all described as short, which is interesting as many of those books are geared more towards younger audiences and therefore may genuinely be shorter. On the other hand, Poetry and Fantasy/Paranormal books are described as long. Poetry reviews use some interesting adjectives such as "free, " "powerful", and "personal", whereas other genres have a few adjectives that are very genre-specific ("historical", "comic", "sexy"). Finally, the only three genres without "bad" as a significant adjective were Children's Literature, History/Biography, and Poetry. 

![Clustering](/Users/ashleyfeiler/Documents/data_science/datasci_repo/Goodreads-Genre-Reviews-Analysis/images/clustering.png)

## Conclusions

Overall, it is clear that there are some linguistic differences between the reviews written for books of different genres, although they aren't wildly different enough to be 100% clear all the time. Based on both descriptive statistics and machine learning models, there appeared to be a few genres in particular that used a more distinctive vocabulary or had more distinctive linguistic features: Poetry, Children's Literature, and History/Biography. Poetry-related vocabulary was identified in clustering and in a high average word length and k-band. Children's Literature was characterized by short, positive reviews, and History/Biography reviews seemed to show an overall advanced grasp of language through both syntax and vocabulary. 

## Setbacks and Reflections

My biggest struggle throughout this project was simply getting the data to load. My original plan was to supplement my found data by scraping Goodreads for an additional few genres, but my computer simply didn't have the capacity to load this massive dataset. I experimented with different methods of loading this data such as using separate Jupyter Notebook files, using pandas' load_json chunksize parameter, and manually deleting objects and calling garbage collection, but nothing worked. I resorted to using command line to take samples of the reviews, which were small enough sample for my computer to handle. Given all of this, I ended up not adding any new scraped data as processing the existing data was already a huge task.

After moving on to analysis, I started with a very broad question about linguistic differences between reviewers, so I looked at every single linguistic element I could think of. However, once I began digging in to the data, I began to get a sense for what features might be more meaningful than others and focused a bit more on those, such as investingating specifically adjectives since it seemed likely that people would describe different genres differently. Originally I used NLTK's POS tagger to identify adjectives, but eventually switched to spaCy for a slightly more advanced tool. While these hurdles did require a lot of problem-solving to overcome, these struggles were some of my best learning opportunities. 

## References

[Fine-Grained Spoiler Detection from Large-Scale Review Corpora](https://aclanthology.org/P19-1248) (Wan et al., ACL 2019)

Hutto, C.J. & Gilbert, E.E. (2014). VADER: A parsimonious rule-based model for sentiment analysis of social media text. Eighth International Conference on Weblogs and Social Media (ICWSM-14). Ann Arbor, MI, June 2014.

Mendhakar, A. (2022). Linguistic profiling of text genres: An exploration of fictional vs. non-fictional texts. *Information*, *13*(8), 357. https://doi.org/10.3390/info13080357

Mengting Wan and Julian McAuley. (2018). Item recommendation on monotonic behavior chains. In Proceedings of the 12th ACM Conference on Recommender Systems (RecSys '18). Association for Computing Machinery, New York, NY, USA, 86–94. https://doi.org/10.1145/3240323.3240369

Noorda, R., & Berens, K. I. (2021). *Immersive media and books 2020: Consumer behavior and experience with multiple media forms.* Panorama Project. https://drive.google.com/drive/folders/10DlCPSvcVnHEIcAsD7pJJRc_Tsf3Fodu
