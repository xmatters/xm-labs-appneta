AppNeta
AppNeta Performance Manager delivers actionable insight into real-time application and network performance. Get hop-by-hop details for internal and external networks from the end-user perspective.. This xM Labs Integration allows you to connect AppNeta instance to an xMatters On Demand account to showcase the ease of passing alerts to xMatters.

https://www.appneta.com/why-appneta/

IMAGE ALT TEXT HERE


Pre-Requisites
AppNeta account
xMatters account
Files
AppNeta.zip - xMatters communication plan needed to accept data in xMatters from AppNeta.

Installation
Application (Logz.io) set up
Create a free trial at https://logz.io/ if you need an account
Once logged in, goto Alerts and click ALERT ENDPOINTS
ADD ENDPOINT, selecting a CUSTOM type
Give it a Name (xMatters is usually useful) and a Description
Add in the Integration URL from the Comm Plan's Inbound Integration
Select POST Method
Add in the following Code to the BODY (You can amend this as you see fit, but this will get you started):
{ "alert_title": "{{alert_title}}", "alert_description": "{{message}}", "alert_severity": "{{alert_severity}}", "alert_event_samples": "{{alert_event_samples}}", "text": "{{text}}" }

Save it.
Now, add an ALERT DEFINITION
Within CONDITIONS, you can specify a QUERY (if you just want to test the integration, put * here for now)
Under TRIGGER IF condition, select how you want the alert to trigger (# of events is a good starting point)
GROUP BY can be left as 'None'
CONDITION can, for testing, be set as GREATER THAN, with a THRESHOLD of 0 OVER A PERIOD of 5 Minutes
SAVE ALERT and goto DEFINITIONS to Name, Describe and set a Severity Level.
TRIGGERS will allow you to manage how often you're notified (SUPPRESS NOTIFICATIONS FOR x) and also specify the NOTIFICATIONS ENDPOINTS (use the one you setup earlier). You can also opt in your email here - it's a good way of checking that Logz.io is actually having the Alert triggered based on your setup above.
xMatters set up
Load in the LogzioElkAlert.zip Comm Plan
Review the Form's (Elk Alert from Logz.io) configuration - add a default group or user in the recipients section
Testing
To test, simply open a Terminal/Command Prompt and run the (edited) CURL file provided (You'll need to amend your CURL script to the relevant path of your MySQL log). That should upload your MySQL.log file into the KIBANA tab within Logz.io (It can take a minute or two) - keep refreshing the screen. (Not working? Did you amend the TOKEN in the CURL command with the TOKEN from your Logz.io account?)

That should then show up, trigger your alert threshold and send the info to xMatters (where you can monitor the IB Activity Stream or Reports tab to see what's happening, or not happening)

Troubleshooting
If using the curl command, verify any errors printed. the -v option will put curl into verbose mode and more information will be printed to the terminal.

If the curl command exits ok, check the Activity Stream for the Logz.io integration inbound integration and inspect for any errors.

If the activity stream does not contain errors, check to see if an event was created and check the event log for more details.
