# Mars-Weather
This repo contains two jupyter notebook files as well as a csv file. The two jupyter notebook files go through a Mars facts website and scrape certain information from said site. One pulls news article headlines and previews for the article. The other file scrapes rows of data pertaining to temperature on Mars and then does an analysis of the data received.

temp_avg = mars_df.groupby('month')['min_temp'].mean().reset_index().sort_values('min_temp') derived from: https://stackoverflow.com/questions/44885933/how-to-sort-bars-in-a-bar-plot-in-ascending-order

mars_df['terrestrial_date'] = pd.to_datetime(mars_df['terrestrial_date']) derived from: https://stackoverflow.com/questions/26763344/convert-pandas-column-to-datetime

def divide_chunks(l, n):
    for i in range(0, len(l), n): 
        yield l[i:i + n]    
#slice lists into smaller lists and save to new list        
data_list = list(divide_chunks(row_data, 7)) derived from: https://www.geeksforgeeks.org/break-list-chunks-size-n-python/

mars_df = pd.DataFrame(data_list, columns =["id", "terrestrial_date","sol","ls","month","min_temp","pressure"]) derived from: https://www.geeksforgeeks.org/create-a-pandas-dataframe-from-lists/#

mars_df.to_csv("mars_df.csv") derived from: https://sparkbyexamples.com/pandas/pandas-write-dataframe-to-csv-file/?expand_article=1

mars_df['terrestrial_date'] = pd.to_datetime(mars_df['terrestrial_date'])

#change columns to int64 and float64
mars_df = mars_df.astype({"sol":'int64', "ls":'int64',"month":"int64"}) 
mars_df = mars_df.astype({"min_temp":'float64', "pressure":"float64"}) derived from: https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.astype.html & https://pandas.pydata.org/docs/reference/api/pandas.to_datetime.html#pandas.to_datetime
