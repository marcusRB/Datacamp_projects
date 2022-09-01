# Project 01 - Exploring the NYC Airbnb Market

Project Description

In this project, you will apply your data importing and cleaning skills to uncover insights about the Airbnb market in New York City.

You will import data from multiple file types and combine them to answer questions about the Airbnb market in New York. You will also use your string cleaning and date manipulation skills to extract accurate information from the datasets. The packages and tools used here are utilized by data scientists everyday since so much of the world's data is stored in unconventional formats and is not clean or analysis-ready.


## Task 1: Importing the data

    * Load "datasets/airbnb_price.csv", saving the resulting DataFrame to prices.
    
    * Load "datasets/airbnb_room_type.xlsx" using pd.ExcelFile(), saving as xls.
    
    * Use xls.parse() to select the first sheet from xls, saving the resulting DataFrame to room_types.
    
    * Use pd.read_csv(), passing an appropriate value to the sep argument, to import "datasets/airbnb_last_review.tsv" and save as reviews.

## Task 2: Cleaning the price column

    * Update the "price" column of the prices DataFrame, removing whitespace and string characters trailing the numeric values using str.replace().
    
    * Update the "price" column to numeric dtype using pd.to_numeric().
    
    * Print descriptive statistics for the "price" column of the prices DataFrame.

## Task 3: Calculating average price

    * Create a boolean mask for all rows in the "price" column with a value of $0, saving as free_listings.
    
    * Use .loc[~filter] to update the prices DataFrame, subsetting for all listings that are not in the free_listings filter.
    
    * Calculate the mean for prices["price"], using round() to round to the nearest 2 decimal places.
    
    * Print avg_price.


##Task 4: Comparing costs to the private rental market

    * Add a new column, price_per_month, to the prices DataFrame, assuming a year consists of 365 days.
    
    * Calculate the average price of the price_per_month column and store as a new variable, average_price_per_month.
    
    * Assert that this calculation is correct by applying the same method to avg_price
    
    * Print the difference, in dollars, for the average cost of an Airbnb listing versus the private market.

Task 5: Cleaning the room type column

    * Change all values in the room_type column to lowercase.
    
    * Convert the room_type column to category dtype.
    
    * Store the count of values for room_type as room_frequencies.
    
    * Print room_frequencies.

Task 6: What timeframe are we working with?

    * Use the pd.to_datetime() method to change the dtype of the reviews["last_review"] to datetime.
    
    * Use the .min() method to find the oldest review date, storing as first_reviewed.
    
    * Use the .max() method the most recent review date, storing as last_reviewed.
    
    * Print first_reviewed and last_reviewed.

Task 7: Joining the DataFrames.

    * Use an outer merge on prices with the room_types DataFrames, merging on "listing_id", and assigning the resulting DataFrame to rooms_and_prices.
    
    * Use an outer merge on rooms_and_prices with reviews, again matching on "listing_id" saving as airbnb_merged.
    
    * Remove missing observations from airbnb_merged using df.dropna(inplace=True) to leave a clean DataFrame.
    
    * Check for duplicate values in airbnb_merged by chaining the df.duplicated() method with .sum().

Task 8: Analyzing listing prices by NYC borough

    * Create a new column in airbnb_merged called borough by using the str.partition() method on airbnb_merged["nbhood_full"] and indexing the first value using [0].
    
    * Group airbnb_merged by borough and calculate summary statistics (sum, mean, median, and count).
    
    * Update the boroughs DataFrame by passing a value to the round() method to round all values to the nearest 2 decimal places, and chain a method to sort values by the "mean" in descending order.
    
    * Print boroughs.

Task 9: Price range by borough

    * Create label_names, a list of labels to apply to price boundaries: "Budget", "Average", "Expensive", and "Extravagant".
    
    * Create ranges, a list of price boundaries containing the values 0, 69, 175, 350, and np.inf.
    
    * Create a new column, price_range, in the airbnb_merged DataFrame, passing label_names and ranges to the labels and bins keyword arguments to the pd.cut() function respectively.
    
    * Group the airbnb_merged DataFrame by borough and price_range and calculate the count for each label, storing as prices_by_borough.
