---
title: Can't connect to a mailbox after it's re-enabled
description: Describes an issue that prevents users from accessing their mailboxes after they've been disabled and then re-enabled. Affects Exchange Server 2016 and 2013 environments. A resolution is provided.
ms.author: v-weizhu
author: AmandaAZ
manager: dcscontentpm
audience: ITPro
ms.topic: troubleshooting
ms.prod: exchange-server-it-pro
localization_priority: Normal
ms.custom:
- CSSTroubleshoot
search.appverid:
- MET150
appliesto:
- Exchange Server 2016 Enterprise Edition
- Exchange Server 2016 Standard Edition
- Exchange Server 2010 Enterprise
- Exchange Server 2010 Standard
- Exchange Server 2013 Enterprise
- Exchange Server 2013 Standard Edition  
---
# Can't connect to a mailbox after it's re-enabled in Exchange Server

This article helps you resolve the problem that you can't access your mailbox after the mailbox is re-enabled in a Microsoft Exchange Server environment.

_Original KB number:_ &nbsp; 3132711

After a user's mailbox is re-enabled in an Exchange Server 2016 or Exchange Server 2013 environment, the user can't access their mailbox by using one or more client protocols.

When a user account has the Exchange mailbox disabled, the following Exchange attributes aren't removed from the user object:

- `msExchAddressBookFlags`
- `msExchBypassAudit`
- `msExchPreviousRecipientTypeDetails`
- `msExchProvisioningFlags`
- `msExchRecipientSoftDeletedStatus`
- `msExchUMDtmfMap`
- `msExchWhenMailboxCreated`
- `protocolSettings`

Use the `Set-CASMailbox` cmdlet to enable the client protocol that's required for the user to connect to their mailbox. For example, to enable Outlook Anywhere for the user, run the following cmdlet:

```powershell
Set-CASMailbox Jim -MAPIBlockOutlookRpcHttp:$False
```
