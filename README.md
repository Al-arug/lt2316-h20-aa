# LT2316 H20 Assignment A1

Name: ALi Aruqi

## Notes on Part 1.

The code has a path to the data if the data folder "DDIcorpus" is in the same directory as the "aa" folder and the "run" notebook.

In part one I have 4 main functions. First one med_vocab_split it opens path to the data and splits the files, it also takes all the words from all the splits to make ids. Id's can be easily seperated between train and split.

The second function is tokenization. This is a seperate function because there was initially a set of rules meant to avoid the loss of words in the tokenization process. Later I realized that this is unnecessary and kept a normal nltk tokenizer. The function has two functionalities. it could return a sentene tokenized or tokenized with character offsset. Without character offset is used in the first function and with character offset is used when creating the data frames. The character offset in the original files are dismissed. the new character offset is meant to be as update after the texts are cleaned and tokenized. 

The thirdfunction is sort. It takes files/ splits and returns three data frames. The first contains name entities only, the second returns the data-split labeled with entity id. The labeled data is meant to make it easier for get_y since the data is already being sampled. The third returned value is a data_df for each split. 

After passing all the splits to the sort function, the data_df and ner_df of each split are concatanted to make the requested ner_df and data_df

Note: The med_vocab_split can be improved by creating a sub function that save the sentences and its ids from each split and pass it to sort() function instead of spliting the data by the file. This should be more effecient as instead of looping through the xml files twice, it could be done at once, but for the next assignment. 

## Notes on Part 2.

The features are character ids, I think word embeddings would'v been more effecient because using characters for features results into so much padding, padding for the max_word_length + pading for max_word_length. Word embeddings probably has less padding since it's only the sentenes that are padded which I think gives a more valuable data. However, sine we had the freedom to chose a method of our choice I used characters as it fullfils the required task. 

## Notes on Part Bonus.

In : plot_ner_per_sample_distribution() : To measure the distribution of the ners in the sentences I count the ners that has the same sentence ids in ner_df then I check the sentence ids that are not in the Ner_df, meaning that they have 0 Ners and append a zero for the list that contain the counts. 

plot_sample_length_distribution : counts the lengths of all the sentence ids in data_df. 

plot_ner_cooccurence_venndiagram(): The method used collects all the sentence ids that has each of the entities. 

