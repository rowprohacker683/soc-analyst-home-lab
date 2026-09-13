## splunk command implement : previous session i upload 2 database one is web_application and other is linux data . I name the index as test . today i practice these in my splunk 
##Enter a search that returns all web application events that include a purchase action with a web status of 200

##Enter a search that returns all web application events that include a purchase action where product ID is WC-SH-G04

##The team is only looking for successful purchases, so change your search to only return those.
  commands: index=test sourcetype="access_combined_wcookie" action=purchase status=200 file=success.do

##The team is only looking for unsuccessful purchases, so change your search to only return those.

##Status not equal to 200 and got error (status!=200)

##You will see fields that do not matter to the team. Use the fields command to only return the action, JSESSIONID and status fields. Does your search run faster using the command?
commands : index=test sourcetype=access_combined_wcookie action=purchase status=200 file=success.do | fields action, JSESSIONID, status

##Write a query to provide a statistics of the above activity by JSESSIONID

##Find the list of clientips who have visited the URL "Buttercupgames.com" and rename the count as events.
