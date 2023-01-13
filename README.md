# chicago_crime-_report
WEEK 5 PEER GRADED ASSIGNMENT (COURSERA) - Analysis of Socioeconomic Indicators ,Public Schools and Crime Data of Chicago
PROBLEM STATEMENT 1-  Find the total number of crimes recorded in the CRIME table
SOL->                 %sql select count(*) as total_no_of_crimes_recorded from crime_data
PROBLEM STATEMENT 2-  List community areas with per capita income less than 11000.
SOL->                 %sql select community_area_name,per_capita_income from census_data where per_capita_income < 11000
PROBLEM STATEMENT 3-  List all case numbers for crimes involving minors?(children are not considered minors for the purposes of crime analysis)
SOL->                 %sql select case_number,description from crime_data where description like '%MINOR%'
PROBLEM STATEMENT 4-  List all kidnapping crimes involving a child?
SOL->                 %sql select * from crime_data where PRIMARY_TYPE='KIDNAPPING' AND DESCRIPTION LIKE '%CHILD%'
PROBLEM STATEMENT 5-  What kinds of crimes were recorded at schools?
SOL->                 %sql select DISTINCT(PRIMARY_TYPE) from crime_data where LOCATION_DESCRIPTION LIKE '%SCHOOL%'
PROBLEM STATEMENT 6- List the average safety score for each type of school.
SOL->                %sql select "Elementary, Middle, or High School",avg(safety_score) as average from PUBLIC_SCHOOLS group BY "Elementary, Middle, or High School"
PROBLEM STATEMENT 7- List 5 community areas with highest % of households below poverty line
SOL->                %sql select COMMUNITY_AREA_NAME,percent_households_below_poverty FROM CENSUS_DATA order by percent_households_below_poverty desc limit 5
PROBLEM STATEMENT 8-  Which community area is most crime prone?
SOL->                 %sql SELECT community_area_number,COUNT(*) as crime_prone_area from CRIME_DATA GROUP BY community_area_number order by 2 desc limit 1
PROBLEM STATEMENT 9-  Use a sub-query to find the name of the community area with highest hardship index
SOL->                 %sql select community_area_name from census_data where hardship_index=(select max(hardship_index) from census_data)
PROBLEM STATEMENT 10- Use a sub-query to determine the Community Area Name with most number of crimes?
SOL->                 %sql SELECT community_area_name from census_data WHERE community_area_number =(SELECT community_area_number FROM CRIME_DATA \
                                                                        where community_area_number =25 limit 1)
