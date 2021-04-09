# West Nile Virus Outbreak Prediction

## Introduction

West Nile Virus is the **leading cause of mosquito-borne disease in the United States** ([source](https://www.cdc.gov/westnile/index.html])). It was first detected in the United States in 1999 and has since quickly spread around the country by the bite of an infected mosquito to humans. Illinois first identified a case on two dead crows carrying the pathogen in September 2001. By the end of 2002, Illinois had encountered more human cases than any other States in the US ([source](https://www.dph.illinois.gov/topics-services/diseases-and-conditions/west-nile-virus)). 

In about 20% of people infected by the virus, it was reported that they developed fever, headache, vomiting and rash. In less than 1% of people, it affects nervous systems and poses a 10% risk of death ([source](https://www.cdc.gov/westnile/index.html?CDC_AA_refVal=https%3A%2F%2Fwww.cdc.gov%2Fwestnile%2Ffaq%2FgenQuestions.html)). 

As there is **no human vaccine** is has progressed beyond phase II clinical trial ([source](https://web.archive.org/web/20171026111330/https://www.cdc.gov/westnile/faq/genQuestions.html), [source](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2168174)), the best way to avoid the virus is to **avoid being bitten by the mosquitos**. 

In 2004, the City of Chicago and Chicago Department of Public Health (CDPH) had established a **comprehensive surveillance and control program** to scatter mosquitos trap across the city from late spring through the fall (May to October). The mosquitos trapped then is tested for the presence of West Nile Virus. This data will then be used to help the public health department to determine the location and timing of mosquito spray to curb the adult mosquitos population ([source](https://www.kaggle.com/c/predict-west-nile-virus)).

## Dataset Overview

To begin with, it is crucial that we understand the data available to us. This enables us to have an overall picture on the way to piece the information together to obtain a coherent insight.
| Dataset                                            | Content                                                                                                                   | Source                                          | Data Available for     |
|----------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------|------------------------|
| Mosquito and Virus Spreading<br>(Training dataset) | - Date<br>- Location of trap<br>- Number of mosquito caught<br>- Mosquito species caught<br>- Presence of West Nile Virus | Chicago Department of Public Health             | 2007, 2009, 2011, 2013 |
| Weather                                            | - Date<br>- Temperature related<br>- Humidity related<br>- Wind speed<br>- Sunset/ sunrise timing                         | National Oceanic and Atmospheric Administration | 2007-2014              |
| Spray                                              | - Date<br>- Location                                                                                                      | Chicago Department of Public Health             | 2011 and 2013          |  

Training dataset provides us with the information on location and timing of mosquito and WNV presence. The weather data is believed to have a correlation to the population of mosquito which in turn will carry the virus ([source](https://www.kaggle.com/c/predict-west-nile-virus/data?select=weather.csv.zip)). Meanwhile, spraying pesticide across the city has the intention to reduce the mosquito population. We will further analyse the usage of each dataset subsequently.
