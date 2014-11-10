# Watchman Deployment Research


## Deployment

- [Installing the Monitoring Client via automated deployment or command line](https://watchmanmonitoring.zendesk.com/hc/en-us/articles/202296808)

```bash
/usr/bin/defaults write /Library/MonitoringClient/ClientSettings \
ClientGroup -string "PUT_CLIENT_GROUP_HERE" && \
/usr/bin/curl -L --1 \
https://globalmacit.monitoringclient.com/downloads/MonitoringClient.pkg > \
/tmp/MonitoringClient.pkg && \
/usr/sbin/installer -target / -pkg /tmp/MonitoringClient.pkg
```

- [Watchman Agent mass deployment best practices](https://watchmanmonitoring.zendesk.com/hc/en-us/articles/202325488-Watchman-Agent-mass-deployment-best-practices) - Notes on deploying using Golden Master. Essentially unnecessary info in our environment


### Customization

- [Configuring the Monitoring Agent for mass deployment](https://watchmanmonitoring.zendesk.com/hc/en-us/articles/472802-Configuring-the-Monitoring-Agent-for-mass-deployment)
- [Configuring the editable package options before deployment](https://watchmanmonitoring.zendesk.com/hc/en-us/articles/201735653-Configuring-the-editable-package-options-before-deployment)


### Branding

- [Rebranding](https://www.watchmanmonitoring.com/custom-branding/)


## Monitoring

- [Helpful Terminal/Command Line options for the Monitoring Client](https://watchmanmonitoring.zendesk.com/hc/en-us/articles/200033678-Helpful-Terminal-Command-Line-options-for-the-Monitoring-Client)
- [Using Watchman Monitoring on Servers](https://watchmanmonitoring.zendesk.com/hc/en-us/articles/486663-Using-Watchman-Monitoring-on-Servers)
- [Daylite Client Monitoring](https://watchmanmonitoring.zendesk.com/hc/en-us/articles/556531-Daylite-Client-Monitoring)
- [Daylite Server Monitoring](https://watchmanmonitoring.zendesk.com/hc/en-us/articles/298804-Daylite-Server-Monitoring)


## Integration

- [Integration with Monkey Box for password and configuration management](https://watchmanmonitoring.zendesk.com/hc/en-us/articles/201187286-Integration-with-Monkey-Box-for-password-and-configuration-management)
- [Integrating Watchman Monitoring with Absolute Manage](https://watchmanmonitoring.zendesk.com/hc/en-us/articles/486493-Integrating-Watchman-Monitoring-with-Absolute-Manage)
- [Integration with Zendesk for ticket management](https://watchmanmonitoring.zendesk.com/hc/en-us/articles/472922-Integration-with-Zendesk-for-ticket-management)
- [LogMeIn Integration](https://watchmanmonitoring.zendesk.com/hc/en-us/articles/486583-LogMeIn-Integration)



## Removal

### To remotely remove a Watchman Monitoring Agent

1. Login to the Watchman Server and locate the client record for the agent you want to remove.
2. Click on the gear icon in the top-right corner of the page and choose **Flag for Removal**.

Once marked for removal on the Monitoring Server, the Monitoring Agent, on next check-in, will remove itself.

When the agent is successfully removed, a confirmation email will be sent and the Client Record on the server will change to indicate it's removed status (the record, at this time, may now be permanently removed).

[Source](https://watchmanmonitoring.zendesk.com/hc/en-us/articles/202325508-Remote-Removal-of-the-Watchman-Monitoring-Agent)


### To remove the Monitoring Client via Terminal.app:

Send the following command with administrative permissions:

	/Library/MonitoringClient/Utilities/RemoveClient -F

This command will prevent an email reporting the removal of the client:

	/Library/MonitoringClient/Utilities/RemoveClient -FQ

[Source](https://watchmanmonitoring.zendesk.com/hc/en-us/articles/705065-Removing-the-Monitoring-Computer)


### To remove rogue or dead systems

1. Login to the Watchman Server and locate the client record for the agent you want to remove.
2. Click on the gear icon in the top-right corner of the page and choose **Delete Record**.


##  Command Line options for the Monitoring Client

*Sourced from [the help document](https://www.watchmanmonitoring.com/terminal-commands).*

### Force the Monitoring Client to report now:

    sudo /Library/MonitoringClient/RunClient -F



### Force the Monitoring Client to check for software updates:

    sudo /Library/MonitoringClient/RunUpdater -F



### Disable the Auto-Update check:

    /usr/bin/defaults write /Library/MonitoringClient/ClientSettings Update_Enabled -bool false


### Remove the Monitoring Client from the computer:

    /Library/MonitoringClient/Utilities/RemoveClient -F

Note: The -F switch is case sensitive.


### Change the Client Group

Note: replace CLIENT_GROUP_NAME with the desired Client Group name

    /usr/bin/defaults write /Library/MonitoringClient/ClientSettings ClientGroup -string "CLIENT_GROUP_NAME"



### Change the Time Machine warning threshold

Note: replace DAYS with a number value for the desired number of days

    defaults write /Library/MonitoringClient/PluginSupport/check_time_machine_settings Days_Until_Warning -int DAYS




### Toggle Time Machine monitoring Off/On

Note: false = off, true = on

    defaults write /Library/MonitoringClient/PluginSupport/check_time_machine_settings Warning_Enabled -bool false



### Adjust Root Volume Capacity Warning

Note: default is 90%

    defaults write /Library/MonitoringClient/PluginSupport/check_root_capacity_settings Root_Warn_Level -int 90



### Disable a plugin completely

    defaults write /Library/MonitoringClient/ClientSettings.plist PluginsDisabled -array-add "check_[service-to-ignore].plugin"

Locate the actual plugin name in /Library/MonitoringClient/Plugins To disable time machine (a common request):

    defaults write /Library/MonitoringClient/ClientSettings.plist PluginsDisabled -array-add "check_time_machine.plugin"

 

### Disable CrashPlan plugin

	defaults write /Library/MonitoringClient/ClientSettings.plist PluginsDisabled -array-add "check_crashplan_client.plugin"



### Disable Carbon Copy Cloner plugin

	defaults write /Library/MonitoringClient/ClientSettings.plist PluginsDisabled -array-add "check_CCC_log.plugin"



### Enable or Disable reboot notifications:

    defaults write /Library/MonitoringClient/PluginSupport/check_reboot_time_settings -bool true

 
## Document History
Created:	24 Oct 2014  
Author:		Tobias Morrison