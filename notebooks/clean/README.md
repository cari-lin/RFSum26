# clean

## Purpose
This folder is where data was uploaded directly from the raw data and cleaned to be used to create features and used in predictions


## Contents
 * `clean-rides.ipynb`: This notebook clean the main trip data downloaded from the indego site. This notebook uses a for loop to upload all the raw data. From these data, datetime data was extrapolated, and 
datetime features were created. Columns with `dtype = object or string` were one-hot encoded so that they would take up less memory. Features like `trip_oneway` were created as 
booleans so that additional columns could be deleted. Trips were dropped if their duration was less than 1 minute or outside the 99th percentile. This accounted for ~4% 
of all data. Cyclical features, such as hour, day, and month, were extrapolated from the existing data. Finally, it was saved as `fdemand.csv`.
 * `clean-stations.ipynb`: This notebook uses `json requests` to scrape an html website to mine `id`, `name`, `latitude`, `longitude`, `total_docks` and `street_address`. This 
was opted for instead of using the data that indego provided so that only current stations were used for the predictions, instead of stations that were closed before data was 
collected. Minimal cleaning was used, just making sure errors were coerced and all the numerical columns were indeed numerical. Finally, this was saved as `stations.csv`.
 * `clean-weather.ipynb`: This notebook simply imports the downloaded data from the raw data folder. Columns were renamed to all lowercase. There was no variance 
in the elevation, latitude, and longitude columns, so they were dropped. This was ultimately saved as `weather.csv`.

## Inputs
* `clean-rides.ipynb`: This notebook expects 25 files, from years 2020-2026, q1 - q4. Note that as of 07/23/2026, q2, q3, and q4 were not used or downloaded.
* `clean-stations.ipynb`: This notebook expects an url, already included in the notebook. Make sure url is available before executing code.
* `clean-weather.ipynb`: This notebooks expects a raw datafile called `philly_weather.csv`, which is stored in the Google Drive, with a link located in the main `README.md`. 

## Outputs
What files or datasets they create.
