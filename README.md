# Azure-SOC
# Building a SOC + Honeynet in Azure (Live Traffic)
![Cloud Honeynet / SOC](https://i.imgur.com/ZWxe03e.jpg)

## Introduction

In this project, I built a mini honeynet in Azure and ingested log sources from various resources into a Log Analytics workspace, which was then used by Microsoft Sentinel to build attack maps, trigger alerts, and create incidents. I measured a few security metrics in the insecure environment for 24 hours, applied some security controls to harden the environment, measure metrics for another 24 hours, then showed the results below. The metrics I will show are:

- SecurityEvent (Windows Event Logs)
- Syslog (Linux Event Logs)
- SecurityAlert (Log Analytics Alerts Triggered)
- SecurityIncident (Incidents created by Sentinel)
- AzureNetworkAnalytics_CL (Malicious Flows allowed into our honeynet)

## Architecture Before Hardening / Security Controls
![Architecture Diagram](https://i.imgur.com/aBDwnKb.jpg)

## Architecture After Hardening / Security Controls
![Architecture Diagram](https://i.imgur.com/YQNa9Pp.jpg)

The architecture of the mini honeynet in Azure consists of the following components:

- Virtual Network (VNet)
- Network Security Group (NSG)
- Virtual Machines (2 windows, 1 linux)
- Log Analytics Workspace
- Azure Key Vault
- Azure Storage Account
- Microsoft Sentinel

For the "BEFORE" metrics, all resources were originally deployed, exposed to the internet. The Virtual Machines had both their Network Security Groups and built-in firewalls wide open, and all other resources are deployed with public endpoints visible to the Internet; aka, no use for Private Endpoints.

For the "AFTER" metrics, Network Security Groups were hardened by blocking ALL traffic with the exception of my admin workstation, and all other resources were protected by their built-in firewalls as well as Private Endpoint

## Attack Maps Before Hardening / Security Controls
![image](https://github.com/MatthewMecham32/Azure-SOC/assets/70896344/0195c6bd-263b-4830-94ca-203ef18bede1)<br>
![image](https://github.com/MatthewMecham32/Azure-SOC/assets/70896344/9c71ac02-b0be-4425-b777-5481e1bf19ba)<br>
![image](https://github.com/MatthewMecham32/Azure-SOC/assets/70896344/a34a1f74-f691-41a9-abef-06b09ae7fd36)<br>




## Metrics Before Hardening / Security Controls

The following table shows the metrics we measured in our insecure environment for 24 hours:
Start Time 07/02/2024 10:54AM
Stop Time 07/03/2024 11:55 AM

| Metric                   | Count
| ------------------------ | -----
| SecurityEvent            | 19373
| Syslog                   | 517
| SecurityAlert            | 4
| SecurityIncident         | 126
| AzureNetworkAnalytics_CL | 1880

## Attack Maps After Hardening / Security Controls

<!--```All map queries actually returned no results due to no instances of malicious activity for the 24 hour period after hardening.```-->

## Metrics After Hardening / Security Controls
Will Finish After Independence Day
The following table shows the metrics we measured in our environment for another 24 hours, but after we have applied security controls:
Start Time 
Stop Time	

| Metric                   | Count
| ------------------------ | -----


## Conclusion

In this project, a mini honeynet was constructed in Microsoft Azure and log sources were integrated into a Log Analytics workspace. Microsoft Sentinel was employed to trigger alerts and create incidents based on the ingested logs. Additionally, metrics were measured in the insecure environment before security controls were applied, and then again after implementing security measures. It is noteworthy that the number of security events and incidents were drastically reduced after the security controls were applied, demonstrating their effectiveness.

It is worth noting that if the resources within the network were heavily utilized by regular users, it is likely that more security events and alerts may have been generated within the 24-hour period following the implementation of the security controls.
