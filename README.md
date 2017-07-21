# BMC Remedy On-Demand
Notify on-call response teams when critical incidents are reported in Remedy. With the xMatters and BMC Remedy On-Demand closed-loop integration, the on-call members of resolver teams are automatically notified via multiple communication channels. When the recipient responds, notes are added to the incident work log and specific incident actions may take place depending on the response.

# Pre-Requisites
* Version 9.1 of Remedy On-Demand
* Account in Remedy On-Demand
* xMatters account - If you don't have one, [get one](https://www.xmatters.com)!

# Files
* [BMCRemedyITSMIncident.zip](BMCRemedyITSMIncident.zip) - This is an example comm plan to help get started.

# How it works
Remedy On-Demand triggers one of the xMatters filters as part of the integration. The filter POSTs the Remedy Incident ID to xMatters, and in turn xMatters uses a Remedy web service to obtain the incident properties and subsequently creates the xMatters Event targeted to the assigned resolver Group.

The notified resolver responds with ACCEPT - to take ownership of the incident, IGNORE - to escalate to the next resource in the on call schedule, or RESOLVE - to resolve the incident.

The closed loop integration annotates the incident work log with xMatters event status, notification delivery status, and user responses. Additionally, an ACCEPT response assigns the user to the incident and updates the incident status to In Progress. A RESOLVE response updates the incident status to Resolved.

# Installation 

## xMatters set up
1. Create a REST user account
2. http://help.xmatters.com/OnDemand/xmodwelcome/communicationplanbuilder/exportcommplan.htm)
2. Add this code to some place on what page:
   ```
   var items = [];
   items.push( { "stuff": "value"} );
   console.log( 'Do stuff' );
   ```


## Remedy On-Demand set up
Any specific steps for setting up the target application? The more precise you can be, the better!

Images are encouraged. Adding them is as easy as:
```
<kbd>
  <img src="media/cat-tax.png" width="200" height="400">
</kbd>
```

<kbd>
  <img src="media/cat-tax.png" width="200" height="400">
</kbd>


# Testing
Be specific. What should happen to make sure this code works? What would a user expect to see? 

# Troubleshooting
Optional section for how to troubleshoot. Especially anything in the source application that an xMatters developer might not know about, or specific areas in xMatters to look for details - like the Activity Stream? 
