# AppNeta
AppNeta Performance Manager delivers actionable insight into real-time application and network performance. Get hop-by-hop details for internal and external networks from the end-user perspective.. This xM Labs Integration allows you to connect AppNeta instance to an xMatters On Demand account to showcase the ease of passing alerts to xMatters.

https://www.appneta.com/why-appneta/

# Pre-Requisites:
AppNeta account
xMatters account
Files
AppNeta.zip - xMatters communication plan needed to accept data in xMatters from AppNeta.

# Installation:
Application (AppNeta) set up
- Follow steps 1-9 on this website: https://docs.appneta.com/event-integration.html#configure-apm-event-integration

Example:
[
     {
       "url": "https://company.xmatters.com/api/integration/1/functions/797f886e-e897-4e76-98f4-4cd7b57e42d3/triggers?apiKey=e1567b9b-749c-48db-83e0-8d729a604679",
       "testEvents": false,
       "seqEvents": true,
       "sqaEvents": true,
       "webAlertEvents": false,
       "blacklisted": false
     }
   ]


# xMatters set up:
Load in the AppNeta.zip Comm Plan
Review the Form's configuration - add a default group or user in the recipients section

# Testing:
- To test it: you will start getting all EVENT alerts into xMatters. You can setup flood control rules to help control floods.

# Troubleshooting:
- Please use our community site at: support.xmatters.com for more assistance.
- We do not provide support for this integration via support tickets.
