# AppNeta
AppNeta Performance Manager delivers actionable insight into real-time application and network performance. Get hop-by-hop details for internal and external networks from the end-user perspective.. This xM Labs Integration allows you to connect AppNeta instance to an xMatters On Demand account to showcase the ease of passing alerts to xMatters.

https://www.appneta.com/why-appneta/

<kbd>
<a href="https://support.xmatters.com/hc/en-us/community/topics">
   <img src="https://github.com/xmatters/xMatters-Labs/raw/master/media/disclaimer.png">
</a>
</kbd>

# How it works:
1. AppNeta detects anomolies in application and networking monitoring.
2. Events are triggered in AppNeta
3. The APM event integration is configured to detect one or all of the following types of events:

- Sequencer events - These are notifications that APM lost or reestablished connectivity with a monitoring point.
- Service quality events - These are notifications that an alert condition was violated or cleared.
- Web application events - These are notifications that a web path alert profile was violated or cleared
- Network change events - These are notifications that alert you to changes in the sequence of networks (BGP Autonomous Systems) on the path between a source and a target.

4. xMatters triggers are setup through a HTTP POST via the Observer API. It sends the content of the event as a JSON payload into xMatters inbound integration

5. End-users recieve the alert and can respond to it by acknowledge or escalate. 
5a: Acknowledge: terminates the xMatters event
5b: Escalate: escalates to the next person on call

# Pre-Requisites:
* AppNeta account
* xMatters account

# Files
1. [AppNeta.zip](AppNeta.zip) - xMatters workflow needed to accept data in xMatters from AppNeta.

# Installation:

## Application (AppNeta) set up:
1. Follow steps 1-9 on this website: https://docs.appneta.com/event-integration.html#configure-apm-event-integration

Example:

```
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
```

## xMatters set up:
1. Load in the AppNeta.zip Comm Plan
2. Review the Form's configuration - add a default group or user in the recipients section

# Testing:
1. Setup the Observer API for Sequencer events
2. Take a host down to test if Sequencer event triggers the HTTP POST to xMatters
3. Verify you recieve the alert and respond (terminates xMatters events)

# Troubleshooting:
- Please use our community site at: support.xmatters.com for more assistance.
- We do not provide support for this integration via support tickets.
