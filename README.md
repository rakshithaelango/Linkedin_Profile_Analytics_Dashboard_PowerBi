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
  
     * Imported Files Invitations, Connections and Messages.
          
* STEP 3: Data cleaning And Data pre - processing..
  
          * Removed the unwanted columns in invitation and connection and messaages data.
          * Created the Date columns by using measure.
          * Changed data types.

* STEP 4: Data modelling.
    
         Connected the relationship Connections and Dates.
        
* STEP 5: Create DAX measures

   * Created Date table:

     ![1693724273287 (1)](https://github.com/rakshithaelango/Linkedin_Profile_Analytics_Dashboard_PowerBi/assets/116090323/4e8387fb-f463-4f7f-99f4-b0b489c54555)

    * created calculations columns to measure Invitation received, invitation sent, messages received, messages sent, Total companies, Total connections.

           * INVITATION RECEIVED : Invitation Recceived = COUNTROWS(FILTER(ALL(Invitations),Invitations[Direction] = "INCOMING"))
           * INVITATION SENT : Invitation Sent = COUNTROWS(FILTER(ALL(Invitations),Invitations[Direction] = "OUTGOING"))
           * MESSAGE RECEIVED: Messages Received = CALCULATE(COUNT(messages[FROM]),NOT(messages[FROM]IN {"Rakshitha Elango"}))
           * MESSAGE SENT: Message Sent = CALCULATE(COUNTA(messages[FROM]),FILTER(messages,messages[FROM]= "Rakshitha Elango"))
           * TOTAL COMPANIES: Total Companies = DISTINCTCOUNT(Connections[Company])
           * TOTAL CONNECTIONS: Total Connections = COUNT(Connections[First Name])
            

* STEP 6: Created the Dashboard By using different visual.
  
           * CARDS: Created the cards to show Total companies, connections, messages received, sent and invitation sent.
           * FLITERS : Created the fliters to show DATE and Companies.
           * DONUT CHART: Clearly to see invitation received and sent.
           * STACKED BAR CHART: To see Connection by companies and positions.
           * AREA CHART: To see Connection by month name and Quater.
          
This all the following steps to perform LINKEDIN PROFILE ANALYTICS By using PowerBi dashboard.





