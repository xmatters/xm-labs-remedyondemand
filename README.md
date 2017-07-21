# BMC Remedy On-Demand
Notify on-call response teams when critical incidents are reported in Remedy. With the xMatters and BMC Remedy On-Demand closed-loop integration, the on-call members of resolver teams are automatically notified via multiple communication channels. When the recipient responds, notes are added to the incident work log and specific incident actions may take place depending on the response.

# Pre-Requisites
* Version 9.1 of Remedy On-Demand
* Account in Remedy On-Demand
* xMatters account - If you don't have one, [get one](https://www.xmatters.com)!

# Files
[BMCRemedyITSMIncident.zip](BMCRemedyITSMIncident.zip) - download this Communication Plan to get started

# How it works
Remedy On-Demand triggers one of the xMatters filters as part of the integration. The filter POSTs the Remedy Incident ID to xMatters, and in turn xMatters uses a Remedy web service to obtain the incident properties and subsequently creates the xMatters Event targeted to the assigned resolver Group.

The notified resolver responds with ACCEPT - to take ownership of the incident, IGNORE - to escalate to the next resource in the on call schedule, or RESOLVE - to resolve the incident.

The closed loop integration annotates the incident work log with xMatters event status, notification delivery status, and user responses. Additionally, an ACCEPT response assigns the user to the incident and updates the incident status to In Progress. A RESOLVE response updates the incident status to Resolved.

# Installation 

## xMatters set up
### Create a REST user account

<kbd>
  <img src="media/xMRESTUser.png">
</kbd>  

### Import the Communication Plan
* Import the BMC Remedy ITSM - Incident Communication Plan (BMCRemedyITSMIncident.zip)     http://help.xmatters.com/OnDemand/xmodwelcome/communicationplanbuilder/exportcommplan.htm

### Assign permissions to the Communication Plan and Form  
* On the Communication Plans page, click the Edit drop-down menu for the BMC Remedy ITSM - IT communication plan then select Access Permissions
* Add the REST User
* On the Communication Plans page, click the Edit drop-down menu for the BMC Remedy ITSM - IT communication plan then select Forms
* Click the Mobile and Web Service drop-down menu for the Incident Alerts form
* Select Sender Permissions then add the REST User

### Configure Integration Builder Constants and Endpoints  
* On the Communication Plans page, click the Edit drop-down menu for the BMC Remedy ITSM - IT communication plan then select Integration Builder
* Click Edit Endpoints
* For the xMatters endpoint, in Assign Endpoint add the REST User then Save Changes
* For the Remedy On-Demand DEV endpoint, type the Base URL for the Remedy DEV environment then Save Changes
* For the Remedy On-Demand PROD endpoint, type the Base URL for the Remedy PROD environment then Save Changes
* For the Remedy On-Demand QA endpoint, type the Base URL for the Remedy QA environment then Save Changes
* Close Edit Endpoints  
* Click Edit Constants, then edit these constants:
   
| Constant               | Description                                                                |
|:---------------------- |:-------------------------------------------------------------------------- |
| ROD_SERVER_NAME        | Domain name of Remedy On Demand server accepting Web Service calls         |
| ROD_WS_HOSTNAME        | Remedy On Demand Middle-Tier (AR) host name that accepts Web Service calls |
| ROD_WS_PASSWORD        | Password for authorizing web service calls to Remedy On Demand             |
| ROD_WS_PROTOCOL        | Protocol to use when calling back into Remedy On Demand Web Services       |
| ROD_WS_USERNAME        | Remedy On Demand user to authenticate incoming Web Service calls           |
| XMOD_INC_FORM_WS_URL   | See below to obtain the Inbound Integration URL                            |
| XMOD_ROD_ENDPOINT_NAME | Remedy On-Demand QA or Remedy On-Demand DEV or Remedy On-Demand PROD       |

### Get the XMOD_INC_FORM_WS_URL  
* On the Communication Plans page, click the Edit drop-down menu for the BMC Remedy ITSM - IT communication plan then select Integration Builder
* Click the *1 Configured* link for Inbound Integrations
* Click the *Incident Alerts - Inbound* link
* Scroll to the **How to trigger the integration** section then click the *Copy Url* link

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
