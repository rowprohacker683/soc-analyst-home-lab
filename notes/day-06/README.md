##Another day of explore splunk real weblogs and database throught this command 
##Create a table where columns will be action, Jsessionid, status and it will return all the products which were successfully processed and action=purchase.
index=test sourcetype="access_combined_wcookie" action=purchase status=200 | table action JSESSIONID, status

##Write a query to search, which returns all web application events that include a purchase action and visualize the products statistics with the help of Splunk
index=test sourcetype="access_combined_wcookie" action=purchase status=200 | stats count by productId

##Session IDs are called "UserSessions" in the marketing data. Rename JSESSIONID so that your report matches the marketing data
index=test sourcetype="access_combined_wcookie" action=purchase| dedup JSESSIONID | table JSESSIONID | rename JSESSIONID as usersessions

##Remove the duplicate Usersessions

##Use the top command to find the best-selling productIds for all time.
index=test sourcetype="access_combined_wcookie" action=purchase| top limit=3 productId

##Use a command to find worst selling procductIDs
