COVID-19-FCO – The Fact-Checking Observatory Misinformation and Fact-checks Twitter/X COVID-19 Dataset
================
Grégoire Burel and Harith Alani


# Introduction
The [Fact-checking Observatory](https://fcobservatory.org) (FCO) is a website that automatically generates human-readable weekly reports about the spread of misinformation and fact-checks on Twitter/X was created to help public organisations, journalists and authorities to understand how useful fact-checking articles are for fighting COVID-related misinformation. The COVID-19-FCO dataset contains the COVID-related FCO data used by the FCO for generating its weekly COVID-19 reports. The COVID-19-FCO dataset tracks the co-spread of misinformation and fact-check URLs over 3 years on Twitter/X and contains metadata about the fact-checkers, topics and the demographic of the accounts that spread the tracked URLs. Contrary to existing Twitter/X datasets, our dataset only references known fact-checked misinforming content and includes the corresponding spread of fact-checked content as well as additional metadata. The specificity of the COVID-19-FCO dataset allows for advanced analyses about the impact of fact-checking on the spread of misinformation on social media and helps identify the type of misinformation that can be effectively opposed with fact-checks.


# Acknowledgements
This work has received support from the European Union’s Horizon 2020 research and innovation programme under grants agreement No 101003606 (HERoS) and was supported by the European CHIST-ERA program within the CIMPLE project (grant agreement CHIST-ERA-19-XAI-003).


# Dataset Structure
The COVID-19-FCO dataset is divided into two CSV files. The first file (covid_19_fc.csv) contains information about the fact-checks and fact-checkers. The second file (covid_19_posts.csv) contains information about the URL mentions tracked on Twitter/X as well as the demographic information. Besides these two files, we also include a dataset description file in the [Markdown format](https://www.markdownguide.org) (README.md) that includes details about the fields present in the dataset.

The *covid_19_fc.csv* file is structured as follows:


 Column Label                   | Description                                                                                                                                                                                 | Example                                                                                                             
--------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------
 fact_check__date               | The date when the fact-check was published.                                                                                                                                                 | 2020-01-27                                                                                                 
 fact_check__url                | The URL of the fact-checking article.                                                                                                                                                       | https://observers.france24.com/fr/20200130-intox-chine-soupe-chauve-souris-rumeur-origine-coronavirus?check=6
 claim__url                     | The URL of the fact-checked claim. The URL is left empty if not URL was given by the fact-checker. Some URLs may be associated with a URL archiving website (e.g., https://perma.cc).       | https://perma.cc/R4J8-PVNX                                                                                   
 fact_check__topic              | One of the following topic labels: *Causes*, *Conspiracy Theory*, *Cure*, *Spread*, *Symptoms*, *Vaccine* and *Other*.                                                                      | Causes                                                                                                    
 fact_check__normalised_rating  | A normalised rating between [-1;+1] indicating if the fact-checked claim is *false* (-1), *unclear* (0) or *true* (1).                                                                      | -1                                                                                                        
 fact_checker__name             | The name of the fact-checking organisation that checked the claim.                                                                                                                          | France 24 Observers                                                                                                 
 fact_checker__country          | The country associated with the fact-checker and fact-check. If more than one country, the country names are separated by a comma.                                                          | France                                                                                                     
 fact_checker__language         | The language used in the fact-checking article. May be empty.                                                                                                                               | French                                                                                                     



The *covid_19_posts.csv* file is structured as follows:


 Column Label        | Description                                                                                                                       | Example                                                                                                
---------------------|-----------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------
 post__id            | The Twitter/X identifier of the post that shared the fact-check or claim URL.                                                     | 1258751802142388226                                                                      
 post__date          | The date when the post was created.                                                                                               | 2020-05-08 13:33:10                                                                          
 post__shared_url    | The shared fact-check or claim URL. The URL can be cross-referenced with the URLs found in the *covid_19_fc.csv* file.            | https://www.boomlive.in/fake-news/two-year-old-photo-of-namaz-peddled-as-lockdown-violation-7937
 post__likes         | The number of times the post was liked by other accounts.                                                                         | 23                                                                                           
 post__shares        | The number of times the post was re-posted (i.e., retweeted).                                                                     | 13                                                                                            
 user__followers     | The number of users following the account that shared the URL. May be empty.                                                      | 62931                                                                                        
 user__following     | The number of users followed by the account that shared the URL. May be empty.                                                    | 1181                                                                                       
 user__account_type  | The type of account as identified by Wang et Al.'s ML model (i.e., *non-org* or *is-org*). May be empty.                          | is-org                                                                                        
 user__sex           | The sex of the user as identified by Wang et Al.'s ML model (i.e., *male* or *female*). May be empty.                             | male                                                                                          
 user__age_group     | The age group of the user as identified by Wang et Al.'s ML model (i.e., *19-29*, *30-39*, *≤18*, *≥40*). May be empty.           | ≥40                                                                                      



When using the data, the user should cross-reference the *post__shared_url* field with the *fact_check__url* or *claim__url* field found in the *covid_19_fc.csv* file. 

# Availability
The dataset is indexed and associated with the following unique Digital Object Identifier (DOI): *10.5281/zenodo.10516199}*;  The original content of the post can be retrieved using the Twitter/X API and the provided post identifiers. If the original post cannot be retrieved, the metadata contained in the datasets can still be used for performing various analyses; The dataset is licensed under the [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 (CC BY-NC-SA 4.0) license](https://creativecommons.org/licenses/by-nc-sa/4.0/).

The dataset can be also downloaded from the following GitHub repository: https://github.com/evhart/fco-covid19-data
