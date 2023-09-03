# Linkedin_Profile_Analytics_Dashboard_PowerBi
To create a LinkedIn profile dashboard using Power BI and analyze your own LinkedIn data, 

Follow these steps:
    * Go to your linkedin setting and privacy.
    * Click pn "Data Privacy" i the setting menu.
    * Under the "Get copy of your data" section,click on the corresponding option.
    * Select Download large data archive.
    * Download and Extract the data.

Steps to create power Bi Dashboard:

     * Understand and import the data file according to the formate.
     
     * Load and transform the data.
     
           * I have imported Files Invitations, Connections and Messages.
          
     * Data cleaning.
          * Removed the unwanted columns in invitation and connection and messaages data.
          * Created the Date columns by using measure.
          * Changed data types.

    * Data pre - processing.
    * Data modelling.  

        Connected the relationship Connections and Dates.
        
    * Create DAX measures

         * Created Date table:
  
  Dates = 
VAR MinYear = YEAR ( MIN (Connections[Date]) )
VAR MaxYear = YEAR ( MAX (Connections[Date]) )
RETURN
ADDCOLUMNS (
    FILTER (
        CALENDARAUTO( ),
        AND (YEAR ( [Date]  ) >= MinYear, YEAR( [Date] ) <= MaxYear )
    ),
    "Year", FORMAT([Date], "yyy"),
    --“Calendar Year”, “CY” & YEAR ( [Date] ),
    "Month Name", FORMAT ( [Date], "mmm" ),
    "Month Number",  MONTH ( [Date]),
    "Weekday", FORMAT ( [Date], "dddd"),
    "Weekday number", WEEKDAY ( [Date] ),
     "Year Month", FORMAT ([Date], "mmm yy"),
    "Quater", "Q" & TRUNC ( ( MONTH ( [Date] ) -1 ) / 3 ) + 1
   )
    * create the dashboard.

This all the following steps to perform INKEDIN PROFILE ANALYTICS DASHBOARD  PowerBi dashboard.

DAX MEASURES:



