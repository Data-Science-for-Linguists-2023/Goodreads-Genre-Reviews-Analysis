## Progress Report
### Initial Entry - 2/12/23
- Created public GitHub repository to house all files related to my project
- Initialized README file, License placeholder, and .gitignore file
- Proposed detailed project plan including plans for data source and collection, analysis, and presentation of findings

### 1st Progress Report - 2/24/23
I explored the [UCSD Goodreads data](https://sites.google.com/eng.ucsd.edu/ucsdbookgraph/home#h.p_VCP_qovwtnn1), getting a better understanding of the intention of the original study for which the data was collected, as well as what kinds of files I would need given that the corpus is so comprehensive. In [Jupyter Notebook](https://github.com/Data-Science-for-Linguists-2023/Goodreads-Genre-Reviews-Analysis/blob/main/Data_Exploration.ipynb), I chose to explore the content of the first genre subset, Children’s Literature, to better understand the structure and contents of the data before trying to clean all the data. Using columns that matched across files, I merged review, book, genre and author data files  to get all the necessary information about each review into one DataFrame. I then filtered the data to include only reviews for books in English and exclue rows that had filled either the review text or rating with an empty string. Finally, I took a sample of 1000 of the remaining reviews. I repeated this process with two additional genres, Poetry and Comics/Graphic Novels, and then appended all the samples into one DataFrame. However, I did have trouble getting Jupyter Notebook to handle larger JSON files for other genres, so I wrote out the code for the remaining genres without running it (for now). 

**Data Sharing Plan:** Because the data I am using comes from the UCSD corpus which explicitly states that the data is only for academic use and not to be redistributed, I cannot share the entire data source. That being said, I will be sticking to that Fair Use guidelines that allow me to share a very small portion of the data. Because I showed the first 5 entries of the DataFrame quite frequently within my Data Exploration Jupyter Notebook, I have created a [data_samples directory](https://github.com/Data-Science-for-Linguists-2023/Goodreads-Genre-Reviews-Analysis/tree/main/data_samples) that includes the first 5 entries of all the genre subsets I've compiled so far (3 currently, but will be 8 total) as pulled directly from the UCSD data. Once I have my CSV files of the sampled reviews, I would like to include the same sized portion of that data as well given that that is the portion of the data I will be using for the analysis. 

###2nd Progress Report - 3/23/23
This month, I struggled to find a way to load my data into Jupyter Notebook given the large size of the multiple files that had to be running at once in order to merge them. After some failed experiments with various methods of memory conservation, combinations of Python scripts and Jupyter Notebook files, and using the chunksize parameter of the `.read_JSON` method, I resorted to sampling 5000 reviews from each genre's data set through command line so I would have files short enough for my computer to handle. I had to scrap my original plan to get even samples from each genre, instead processing the data from each of the genre samples using the steps from Progress Report #1. This resulted in slightly uneven samples across genres. All data processing notebooks can be found in the [data_prep folder](https://github.com/Data-Science-for-Linguists-2023/Goodreads-Genre-Reviews-Analysis/tree/main/data_prep). I then pickled the final DataFrame from each genre to then combine into a [final DataFrame]() on which I will do the rest of my analysis. To get started on the analysis, I added columns to the DataFrame for text-based features such as tokens, token count, average word length, average sentence count and length, TTR, k-band, and sentiment. 

**Data Sharing Plan:**
My plan for sharing data is very similar to my initial plan, just with some slightly adjusted numbers. The owners of the UCSD Goodreads data specified that it can be used for academic purposes but cannot be redistributed, so I will be sharing very small samples as allowed under Fair Use just to give a sense of the data. In the [data_samples folder](https://github.com/Data-Science-for-Linguists-2023/Goodreads-Genre-Reviews-Analysis/tree/main/data_samples), I created one CSV file with 5 reviews from each genre (40 total) to show the original data, as well as a sample of 5 reviews from my final aggregated DataFrame to show what the final data I am analyzing looks like. The data set has over 15 million reviews, so these data samples are a miniscule fraction of the overall data set.

**Licensing:**
I have chosen

### Citations (Per UCSD Corpus Permissions):

[Fine-Grained Spoiler Detection from Large-Scale Review Corpora](https://aclanthology.org/P19-1248) (Wan et al., ACL 2019)

Mengting Wan and Julian McAuley. 2018. Item recommendation on monotonic behavior chains. In Proceedings of the 12th ACM Conference on Recommender Systems (RecSys '18). Association for Computing Machinery, New York, NY, USA, 86–94. <https://doi.org/10.1145/3240323.3240369>

