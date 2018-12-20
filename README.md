# HQ-Hotels
Joining Hotels by different suppliers

As an Online Travel Agency, HQ has to handle working with different suppliers of rooms. Different suppliers might provide the same room or room type from a given hotel. In order to aggregate offers for a same (room, hotel), we need to be able to find / maintain a mapping between hotels from different suppliers (ex: hotel 43 from supplier1 is the same to hotel 1007 from supplier 2). This pairing process have to be automated (too many hotels) and maintained by a data engineer. So working on this process will be an important aspect of this position.

The approach we followed was pretty simple.

The input data are in a file named supplier_data.csv.

After importing this file, we create a copy to avoid messing with the original dataset.

Originally, we call this variable 'dataset_copy'.

We need to find every replicated hotel name in our dataset but, before doing so, we remove certain stopwords (like 'the', 'a', 'in', ..) from the name. The best way is to create a file 'stopwords.txt', so if we want to remove (or not remove) an extra word, all we will do is add this word to our file.

The hotel name is in the 'name' column of the dataset. Then:

1 - We lowercase the hotel's names

2 - We split the hotel's names by words (on spaces)

3 - We remove the stopwords

4 - We reconcatenate the hotel's names (it makes things way easy)

5 - We sort the dataframe by name. In this way all the hotels that should be mapped come consecutively and we can solve this task in O(n) complexity. Then we simply move through our dataset, looking for repeated names and, when it happens, we put them in a mapping variable

6 - We save mapping into the a 'mapping.csv' file.
