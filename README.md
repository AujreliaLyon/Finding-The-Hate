# Problem Statement
 - Conventional wisdom holds that some areas of the country are more hostile to minorities than others. But according to the FBI that area is not what most people expect.
 - This study attempts to determine if hate crimes against minorities have a higher correlation with local population (crimes per capita), or with geographic region.
 - The data used in this study track violence against 35 minority groups of various races, religions and sexualities; too much for the scope of this project.
 - Since the FBI reports that members of the LGBTQ community are now targeted more than any other minority group, that is where this study is focused.

*see graph in presentation at https://docs.google.com/presentation/d/1MMiMMtazIhAp9KpM___sF1qrBpwlGy7XJm07uDeiO3o/edit#slide=id.g5d1e1448a8_0_13

# jupyter notebooks - order of execution
- EDA_File_Collation.ipynb
- EDA_post_processing.ipynb
- EDA_Extract_focus_groups.ipynb
- Analysis.ipynb 

# Limitations of this Study
This Initial Analysis suffers from some issues which should be called out up front
- There are two government agencies that gather hate crime data, using very different methodologies to arrive at very different conclusions : the Federal Bureau of Investigation (FBI) and the Bureau of Justice Statistics(BJS) . 
- This study employs the FBI data but I highly recommend that a follow up study be conducted using the BJS data; somewhere between the two we will find the most accurate picture.

### Characteristics of of FBI Data Collection
Characteristics and limitations of data originating  with  the FBI Uniform Crime Reporting (UCR) program
- Voluntary, rather than mandatory, participation by police jurisdictions; there are HUGE holes in reporting regions, easily discernible on the map.
-- Number of agencies that do not participate are not easily available
--Numbers of how many “participating” agencies give questionable or no reports
-Reported an average of 7,500 hate crime victimizations year over year
 
###Characteristics of BJS Data Collection
Characteristics and limitations of data originating  with  the  Bureau of Justice Statistics, National Crime Victimization Survey (NCVS)
- Poll individuals in person, by phone, and on the web
The BJS reports that between 2004-15 as many as 60% of crimes were not reported to the police, further limiting the coverage of the FBI data
- Reported an  average of 250,000 hate crime victimizations in each year from 2004 - 2015

### Avenues of Further Research
 -  is there a correlation between the increased "coming out" of gender non-conforming and the increases in violence - regardless of any correlations with population density graphic location found above ? But I don't know of any authoritative and neutral that measure that.

 - the NATIONAL ARCHIVE OF CRIMINAL JUSTICE DATA, which gathers its data by sureveys, and is believed to capture much more data because of the anonymity in the face of a very strong fear in the LGBTQ the the police will victim shame, refuse to help, or be unable to help. Thei estimates are 200,00k acts of hatre crimes each year vs the FBI's *much* lower rates. Although for this study I have chosen to use exclusively the far more conservative FBI information but I would like to compare and contrast the much higher rates gathered by the NACJD. I suspect that somewhere between the two lies the actual Truth.



# EDA
 - The source data were transmitted in a tab seperated files, which is in and of itself not a problem except that the tabs seem to have *occasionally, but inconsistently* been added to pad out fixed fields widths so data were often shifted to the left or right.

### AGNAME Overflow
 - in 361770 out of 504360 rows, a portion of the AGNAME column was shifted into the neighboring CFIPS column, pushing all columns after it to the right.
 - Fortunately AGNAME is a text column and CFIPS is numeric which made it easily detectable.
-  code was created to check if the contents of a CFIPS cell could be converted to int data; if not it was assumed to be text and belong to the AGNAME column. The erroneous contents were appended to the AGNAME column with a seperating ",", and the cells to the right of CFIPS1 were shifted left by one cell, or area/city population with the general purpose function "EDA_File_Collation.shift_cell_contents"

### Translating FBI bias code to english description
- "./NACJD/Hate Crime Type by Code.csv" contains the code/description information. Basically this was a relational data merge.

### Retrieving city/state lat and long
- these data were retrieved from Google maps, with is a paid service. If you want to run the full process for this you will need to uncomment the section that actually does the pulls from their API, get your own account and access code, comment out the load of the previously stored data (provided so that the actual data gets would not have to be run every time.
