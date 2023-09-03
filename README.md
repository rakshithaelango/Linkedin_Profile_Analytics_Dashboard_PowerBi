# Linkedin_Profile_Analytics_Dashboard_PowerBi
To create a LinkedIn profile dashboard using Power BI and analyze your own LinkedIn data, 

Follow these steps:
    * Go to your linkedin setting and privacy.
    * Click pn "Data Privacy" i the setting menu.
    * Under the "Get copy of your data" section,click on the corresponding option.
    * Select Download large data archive.
    * Download and Extract the data.

Steps to create power Bi Dashboard:

* STEP 1: Understand and import the data file according to the formate.
     
* STEP 2: Load and transform the data.
  
     * I have imported Files Invitations, Connections and Messages.
          
* STEP 3: Data cleaning And Data pre - processing..
  
          * Removed the unwanted columns in invitation and connection and messaages data.
          * Created the Date columns by using measure.
          * Changed data types.

* STEP 4: Data modelling.
    
         Connected the relationship Connections and Dates.
        
* STEP 5: Create DAX measures

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

   
    * created calculations columns to measure Invitation received, invitation sent, messages received, messages sent, Total companies, Total connections.

           * INVITATION RECEIVED : Invitation Recceived = COUNTROWS(FILTER(ALL(Invitations),Invitations[Direction] = "INCOMING"))
           * INVITATION SENT : Invitation Sent = COUNTROWS(FILTER(ALL(Invitations),Invitations[Direction] = "OUTGOING"))
           * MESSAGE RECEIVED: Messages Received = CALCULATE(COUNT(messages[FROM]),NOT(messages[FROM]IN {"Rakshitha Elango"}))
           * MESSAGE SENT: Message Sent = CALCULATE(COUNTA(messages[FROM]),FILTER(messages,messages[FROM]= "Rakshitha Elango"))
           * TOTAL COMPANIES: Total Companies = DISTINCTCOUNT(Connections[Company])
           * TOTAL CONNECTIONS: Total Connections = COUNT(Connections[First Name])
            

This all the following steps to perform INKEDIN PROFILE ANALYTICS DASHBOARD  PowerBi dashboard.

DAX MEASURES:



