This project has the goal to analyze immigration in the US through the databases which will be changed for the data to have a character understandable.
The data come from several sources, and the cluster of data on immigration comes from the US National Tourism and Trade Office.
The data of World Temperature come from Kaggle and as well as OpenSoft offers the US city demographic data where the user will be able to study statistic data about the population which the user can differ by race, age, region, etc.
With the databases, the information which it was obtained, will be used to create a fact table (called immigration_fact) and three tables of dimensions (called immigrant_dimension, demographic_dimension, and temperature_dimension), and Spark will be used for ETL jobs and store the outcomes in parquet.

1.immigration_fact
    •id_immigration (float): identification number
    •type (string): condition of travel, business, vacation or study
    •visatype (string): country-specific visa type code
    •port_city (string): port
    
2.immigrant_dimension
    •id_immigration (float): identification number
    •origin (string): country of origin
    •destination (string): destination country
    •code_city_destination (string): destination code
    •arrival_date (string): date of arrival in the country
    •travel (string): specification if it was arrived via land, sea, air or unknown
    •addr (string): arrival status code
    •depdate (string): end date of the trip
    •birth (float): age
    •biryear (float): Year of birth
    •gender (string): gender F/M (female/male)
    •airline (string): acronym of the airline
    •admission_number (double): admission number in the country
    
3.demographic_dimension
    •city (string): city name
    •state (string): state name
    •median_age (float): average age
    •male_population (float): number of males
    •female_population (float): number of women
    •total_population (float): total population
    •num_veterans (float): number of veterans
    •foreign_born (float): number of foreigners
    •average_hhs (float): average number of people living in a house
    •state_code (string): state code
    •race (string): race
    •count (float): count of immigrant entries to the US
    
4.temperature_dimension
    •date (timestamp): date of the moment that this temperature was obtained
    •average_temperature (float): average temperature 
    •average_temperature_uncertainty (float): temperature uncertainty
    •city (string): name of the city
    •country (string): Country of the data
    •latitude (string): latitude data
    •longitude (string): longitude data
    
Steps 

  1.There is to analyze the immigration data and change the columns for giving an outcome understandable and readable such as changing the columns of time to a format year/month/day and drop the columns that they do not give any information.
  
  2.World Temperature Data will be assessed and it will be just included the data where the column of “country” is equal to “United States” and the column of “date” will be just included the data after the century XX.
  
  3.The U.S. City Demographic Data will be assessed for the outcomes are understandable and besides, it will be shown some graphic where the users will be able to see a distribution of the U.S. population divided by race and divided by age with percentages.
  4.Finally, the tables (fact table and dimensions tables) will be created and saved the process in a parquet for downstream query, so the users will manage to consult in the future.
  
Conclusions
This project was made with Spark because it is able to process a large amount of data and it can do so fast and so easy. Spark can also work with different kinds of formats and it was something necessary in this project due here it was used format as SAS, CSV, Parquet and theses kind of format can integrate very well with S3 and Redshift.
The update of data will be each month because it is the reason more logical whether it is attended to the necessity of the table and, such the temperature data as immigration data and demographic data can be updated each month with new temperatures and new immigrants.
    •The data was increased by 100x.
    
It can migrate to Elastic Map Reduce instance on Amazon Web Side and allow it to scale as needed.
    •The data populates a dashboard that must be updated on a daily basis by 7am every day.
    
If this situation comes, it can use Airflow where will be programed and automatized the data pipeline jobs, and also it must have a retry mechanic in case something fails, the system can repeat the process.

    •The database needed to be accessed by 100+ people.
In this case, it can use Redshift to have the data stored and so many people can access the information easily.
