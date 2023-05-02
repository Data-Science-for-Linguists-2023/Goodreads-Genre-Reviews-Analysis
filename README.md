# Goodreads-Genre-Reviews-Analysis
Ashley Feiler's term project for Data Science for Linguists 2023

Email: aef56@pitt.edu

Date: May 1, 2023

## What's the Story?: Linguistic Variation in Goodreads Reviews by Genre

This project examines the text of public Goodreads reviews on books from different genres (young adult, mystery, fantasy, biography, etc.) and see if the way these reviewers use language differs based on the genre they are reading/reviewing. Which genre's readers write the longest reviews? What adjectives do reviewers use most frequently for each genre? Is there a difference in sentiment in the language used when reviewing one genre vs. another? Through this project, I explore all these questions and more.

### Data

I used the data from the [UCSD Book Graph corpus](https://sites.google.com/eng.ucsd.edu/ucsdbookgraph/home) which contains public book review data scraped from Goodreads (specifically, I used their subsets of the data by genre). It includes over 15 million reviews in JSON files in addition to separate JSON files with metadata on the books, authors, and genres reviewed. In order to make the data a more manageable size, I took a 5000-review sample from each of 8 genres for 40000 total reviews in my dataset. This dataset is specified for academic use only and is not to be redistributed, so I only share small samples of this data.

### Directory

- **[final_report.md](https://github.com/Data-Science-for-Linguists-2023/Goodreads-Genre-Reviews-Analysis/blob/main/final_report.md)** - Gives an overall summary of the project, both its process and findings
- [Data_Exploration.ipynb](https://github.com/Data-Science-for-Linguists-2023/Goodreads-Genre-Reviews-Analysis/blob/main/Data_Exploration.ipynb) - Processes data from first 3/8 genres with detailed explanations
  - [data_prep/](https://github.com/Data-Science-for-Linguists-2023/Goodreads-Genre-Reviews-Analysis/tree/main/data_prep) - Contains additional Jupyter Notebooks that process data from remaining 5/8 genres

- [Compiling_Data.ipynb](https://github.com/Data-Science-for-Linguists-2023/Goodreads-Genre-Reviews-Analysis/blob/main/Compiling_Data.ipynb) - Compiles individual genre data into one dataframe and adds linguistic components
- Data_Analysis.ipynb](https://github.com/Data-Science-for-Linguists-2023/Goodreads-Genre-Reviews-Analysis/blob/main/Data_Analysis.ipynb) - Analyzes linguistic features of all genre data
- [data_samples/](https://github.com/Data-Science-for-Linguists-2023/Goodreads-Genre-Reviews-Analysis/tree/main/data_samples) - Includes small samples of original data and my final dataframe in accordance with Fair Use guidelines
- [images/](https://github.com/Data-Science-for-Linguists-2023/Goodreads-Genre-Reviews-Analysis/tree/main/images) - Contains images of plots and graphs from analysis (.png)
- [project_plan.md](https://github.com/Data-Science-for-Linguists-2023/Goodreads-Genre-Reviews-Analysis/blob/main/project_plan.md) - Describes original plan for project
- [progress_report.md](https://github.com/Data-Science-for-Linguists-2023/Goodreads-Genre-Reviews-Analysis/blob/main/progress_report.md) - Gives monthly updates on progress, including problems encountered and their solutions
- [final_presentation.pdf](https://github.com/Data-Science-for-Linguists-2023/Goodreads-Genre-Reviews-Analysis/blob/main/final_presentation.pdf) - PDF version of presentation on preliminary analysis findings
- [LICENSE.md](https://github.com/Data-Science-for-Linguists-2023/Goodreads-Genre-Reviews-Analysis/blob/main/LICENSE.md) - Provides additional details on what uses and distributions of this code are allowed

### Guestbook

Come visit my [guestbook](https://github.com/Data-Science-for-Linguists-2023/Class-Lounge/blob/main/guestbooks/ashley.md)!! I'm always grateful for feedback. 

### References

#### UCSD Data References

[Fine-Grained Spoiler Detection from Large-Scale Review Corpora](https://aclanthology.org/P19-1248) (Wan et al., ACL 2019)

Mengting Wan and Julian McAuley. 2018. Item recommendation on monotonic behavior chains. In Proceedings of the 12th ACM Conference on Recommender Systems (RecSys '18). Association for Computing Machinery, New York, NY, USA, 86–94. https://doi.org/10.1145/3240323.3240369

#### NLTK Sentiment References

Hutto, C.J. & Gilbert, E.E. (2014). VADER: A Parsimonious Rule-based Model for Sentiment Analysis of Social Media Text. Eighth International Conference on Weblogs and Social Media (ICWSM-14). Ann Arbor, MI, June 2014.
