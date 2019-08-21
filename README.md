# Problem Statement
 - Conventional wisdom holds that some areas of the country are more hostile to minorities than others. But according to the FBI that area is not what most people expect.
 - This study attempts to determine if hate crimes against minorities have a higher correlation with local population (crimes per capita), or with geographic region.
 - The data used in this study track violence against 35 minority groups of various races, religions and sexualities; too much for the scope of this project.
 - Since the FBI reports that members of the LGBTQ community are now targeted more than any other minority group, that is where this study is focused.

 ### Considerations
 - ratio of population by region
 - ratio of population of cities to number of hate crimes. Do the number of hate crimes grow with the population

##### data needs

##### problems
 - agencies where certain minority status is not considered/reported
 - areas where agencies do not participate in the hate crimes data collection at all.
 
### Avenues of Further Research
 -  is there a correlation between the increased "coming out" of gender nonconfming and the increases in violence - regardless of any correlations with population dnesity or  above graphic location found above ? But I don't know of any authoritative sources nd neutral that measure that.

 - the NATIONAL ARCHIVE OF CRIMINAL JUSTICE DATA, which gathers its data by sureveys, and is believed to capture much more data because of the anonymity in the face of a very strong fear in the LGBTQ the the police will victim shame, refuse to help, or be unable to help. Thei estimates are 200,00k acts of hatre crimes each year vs the FBI's *much* lower rates. Although for this study I have chosen to use exclusively the far more conservative FBI information but I would like to compare and contrast the much higher rates gathered by the NACJD. I suspect that somewhere between the two lies the actual Truth.





# Process
## EDA
 - These data were transmitted in a tab seperated file, which is in and of itself not a problem except that the tabs seem to have been added to pad out fixed fields widths so data were often shifted to the left or right.

### AGNAME Overflow
 - in 361770 out of 504360 rows, a portion of the AGNAME column was shifted into the neighboring CFIPS column, pushing all columns after it to the right.
 - Fortunately AGNAME is a text column and CFIPS is numeric
-  function <name> was created to check if the contents of a CFIPS cell could be converted to int data; if not it was assumed to be text and belong to the AGNAME column. The erroneous contents were appended to the AGNAME column with a seperating ",", and the cells to the right of CFIPS1 were shifted left ny one cell.ation, or area/city population

