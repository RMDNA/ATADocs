---
# required metadata

title: Troubleshooting the ATA error log | Microsoft Advanced Threat Analytics
description: Describes how you can troubleshoot common errors in ATA 
keywords:
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: d89e7aff-a6ef-48a3-ae87-6ac2e39f3bdb

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: bennyl
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Troubleshooting the ATA error log
This section details possible errors in the deployments of ATA and the steps required for troubleshooting them.
## ATA Gateway errors
|Error|Description|Resolution|
|-------------|----------|---------|
|System.DirectoryServices.Protocols.LdapException: A local error occurred|The ATA Gateway failed to authenticate against the domain controller.|1. Confirm that the domain controller’s DNS record is configured properly in the DNS server. <br>2. Verify that the time of the ATA Gateway is synchronized with the time of the domain controller.|
|System.IdentityModel.Tokens.SecurityTokenValidationException: Failed to validate certificate chain|The ATA Gateway failed to validate the certificate of the ATA Center.|1. Verify that the Root CA certificate is installed in the trusted certificate authority certificate store on the ATA Gateway. <br>2. Validate that the certificate revocation list (CRL) is available and that certificate revocation validation can be performed.|
|Microsoft.Common.ExtendedException: Failed to parse time generated|The ATA Gateway failed to parse syslog messages that were forwarded from the SIEM.|Verify that the SIEM is configured to forward the messages in one of the formats that are supported by ATA.|
|System.ServiceModel.FaultException: An error occurred when verifying security for the message.|The ATA Gateway failed to authenticate against ATA Center.|Verify that the time of the ATA Gateway is synchronized with the time of the ATA Center.|
|System.ServiceModel.EndpointNotFoundException: Could not connect to net.tcp://center.ip.addr:443/IEntityReceiver|The ATA Gateway failed to establish connection to the ATA Center.|Ensure that the network settings are correct and that the network connection between the ATA Gateway and the ATA Center is active.|
|System.DirectoryServices.Protocols.LdapException: The LDAP server is unavailable.|The ATA Gateway failed to query the domain controller using the LDAP protocol.|1.Verify that the user account used by ATA to connect to the Active Directory domain has read access to all the objects in the Active Directory tree. <br>2.Make sure that the domain controller is not hardened to prevent LDAP queries from the user account used by ATA.|
|Microsoft.Tri.Infrastructure.ContractException: Contract exception|The ATA Gateway failed to synchronize the configuration from the ATA Center.|Complete configuration of the ATA Gateway in the ATA Console.|

## ATA Console errors
|Error|Description|Resolution|
|-------------|----------|---------|
|HTTP Error 500.19 – Internal Server Error|The IIS URL Rewrite module failed to install correctly.|Uninstall and reinstall the IIS URL Rewrite module.<br>[Download the IIS URL Rewrite module](http://go.microsoft.com/fwlink/?LinkID=615137)|

## Deployment errors
|Error|Description|Resolution|
|-------------|----------|---------|
|.Net Framework 4.6.1 installation fails with error 0x800713ec|The pre-requisites for .Net Framework 4.6.1 are not installed on the server. |Before installing ATA, verify that the windows updates [KB2919442](https://www.microsoft.com/en-us/download/details.aspx?id=42135) and [KB2919355](https://support.microsoft.com/en-us/kb/2919355) are installed on the server.|

    ![ATA .NET installation error image](media/netinstallerror.png)


## See Also
- [ATA prerequisites](/advanced-threat-analytics/plan-design/ata-prerequisites)
- [ATA capacity planning](/advanced-threat-analytics/plan-design/ata-capacity-planning)
- [Configure event collection](/advanced-threat-analytics/deploy-use/configure-event-collection)
- [Configuring Windows event forwarding](/advanced-threat-analytics/deploy-use/configure-event-collection#ATA_event_WEF)
- [Check out the ATA forum!](https://social.technet.microsoft.com/Forums/security/en-US/home?forum=mata)
