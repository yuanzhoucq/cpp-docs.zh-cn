---
title: 安全标识符全局函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlsecurity/ATL::Sids::AccountOps
- atlsecurity/ATL::Sids::Admins
- atlsecurity/ATL::Sids::AnonymousLogon
- atlsecurity/ATL::Sids::AuthenticatedUser
- atlsecurity/ATL::Sids::BackupOps
- atlsecurity/ATL::Sids::Batch
- atlsecurity/ATL::Sids::CreatorGroup
- atlsecurity/ATL::Sids::CreatorGroupServer
- atlsecurity/ATL::Sids::CreatorOwner
- atlsecurity/ATL::Sids::CreatorOwnerServer
- atlsecurity/ATL::Sids::Dialup
- atlsecurity/ATL::Sids::Guests
- atlsecurity/ATL::Sids::Interactive
- atlsecurity/ATL::Sids::Local
- atlsecurity/ATL::Sids::Network
- atlsecurity/ATL::Sids::NetworkService
- atlsecurity/ATL::Sids::Null
- atlsecurity/ATL::Sids::PowerUsers
- atlsecurity/ATL::Sids::PrintOps
- atlsecurity/ATL::Sids::Proxy
- atlsecurity/ATL::Sids::RasServers
- atlsecurity/ATL::Sids::Replicator
- atlsecurity/ATL::Sids::RestrictedCode
- atlsecurity/ATL::Sids::Self
- atlsecurity/ATL::Sids::ServerLogon
- atlsecurity/ATL::Sids::Service
- atlsecurity/ATL::Sids::System
- atlsecurity/ATL::Sids::SystemOps
- atlsecurity/ATL::Sids::TerminalServer
- atlsecurity/ATL::Sids::Users
- atlsecurity/ATL::Sids::World
dev_langs:
- C++
helpviewer_keywords:
- security IDs [C++]
- SIDs [C++], returning SID objects
ms.assetid: 85404dcb-c59b-4535-ab3d-66cfa37e87de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4bcafdeecdc0091039e9bb4008aab4e85f6a34aa
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50064962"
---
# <a name="security-identifier-global-functions"></a>安全标识符全局函数

这些函数将返回通用的已知 SID 的对象。

> [!IMPORTANT]
>  下表中列出的函数不能在 Windows 运行时中执行的应用程序中使用。

|||
|-|-|
|[Sids::AccountOps](#accountops)|返回 DOMAIN_ALIAS_RID_ACCOUNT_OPS SID。|
|[Sids::Admins](#admins)|返回 DOMAIN_ALIAS_RID_ADMINS SID。|
|[Sids::AnonymousLogon](#anonymouslogon)|返回 SECURITY_ANONYMOUS_LOGON_RID SID。|
|[Sids::AuthenticatedUser](#authenticateduser)|返回 SECURITY_AUTHENTICATED_USER_RID SID。|
|[Sids::BackupOps](#backupops)|返回 DOMAIN_ALIAS_RID_BACKUP_OPS SID。|
|[Sids::Batch](#batch)|返回 SECURITY_BATCH_RID SID。|
|[Sids::CreatorGroup](#creatorgroup)|返回 SECURITY_CREATOR_GROUP_RID SID。|
|[Sids::CreatorGroupServer](#creatorgroupserver)|返回 SECURITY_CREATOR_GROUP_SERVER_RID SID。|
|[Sids::CreatorOwner](#creatorowner)|返回 SECURITY_CREATOR_OWNER_RID SID。|
|[Sids::CreatorOwnerServer](#creatorownerserver)|返回 SECURITY_CREATOR_OWNER_SERVER_RID SID。|
|[Sids::Dialup](#dialup)|返回 SECURITY_DIALUP_RID SID。|
|[Sids::Guests](#guests)|返回 DOMAIN_ALIAS_RID_GUESTS SID。|
|[Sids::Interactive](#interactive)|返回 SECURITY_INTERACTIVE_RID SID。|
|[Sids::Local](#local)|返回 SECURITY_LOCAL_RID SID。|
|[Sids::Network](#network)|返回 SECURITY_NETWORK_RID SID。|
|[Sids::NetworkService](#networkservice)|返回 SECURITY_NETWORK_SERVICE_RID SID。|
|[Sids::Null](#null)|返回 SECURITY_NULL_RID SID。|
|[Sids::PreW2KAccess](#prew2kaccess)|返回 DOMAIN_ALIAS_RID_PREW2KCOMPACCESS SID。|
|[Sids::PowerUsers](#powerusers)|返回 DOMAIN_ALIAS_RID_POWER_USERS SID。|
|[Sids::PrintOps](#printops)|返回 DOMAIN_ALIAS_RID_PRINT_OPS SID。|
|[Sids::Proxy](#proxy)|返回 SECURITY_PROXY_RID SID。|
|[Sids::RasServers](#rasservers)|返回 DOMAIN_ALIAS_RID_RAS_SERVERS SID。|
|[Sids::Replicator](#replicator)|返回 DOMAIN_ALIAS_RID_REPLICATOR SID。|
|[Sids::RestrictedCode](#restrictedcode)|返回 SECURITY_RESTRICTED_CODE_RID SID。|
|[Sids::Self](#self)|返回 SECURITY_PRINCIPAL_SELF_RID SID。|
|[Sids::ServerLogon](#serverlogon)|返回 SECURITY_SERVER_LOGON_RID SID。|
|[Sids::Service](#service)|返回 SECURITY_SERVICE_RID SID。|
|[Sids::System](#system)|返回 SECURITY_LOCAL_SYSTEM_RID SID。|
|[Sids::SystemOps](#systemops)|返回 DOMAIN_ALIAS_RID_SYSTEM_OPS SID。|
|[Sids::TerminalServer](#terminalserver)|返回 SECURITY_TERMINAL_SERVER_RID SID。|
|[Sids::Users](#users)|返回 DOMAIN_ALIAS_RID_USERS SID。|
|[Sids::World](#world)|返回 SECURITY_WORLD_RID SID。|

### <a name="requirements"></a>要求

**标头：** atlsecurity.h

##  <a name="accountops"></a>  Sids::AccountOps

返回 DOMAIN_ALIAS_RID_ACCOUNT_OPS SID。

```
CSid AccountOps() throw(...);
```

##  <a name="admins"></a>  Sids::Admins

返回 DOMAIN_ALIAS_RID_ADMINS SID。

```
CSid Admins() throw(...);
```

##  <a name="anonymouslogon"></a>  Sids::AnonymousLogon

返回 SECURITY_ANONYMOUS_LOGON_RID SID。

```
CSid AnonymousLogon() throw(...);
```

##  <a name="authenticateduser"></a>  Sids::AuthenticatedUser

返回 SECURITY_AUTHENTICATED_USER_RID SID。

```
CSid AuthenticatedUser() throw(...);
```

##  <a name="backupops"></a>  Sids::BackupOps

返回 DOMAIN_ALIAS_RID_BACKUP_OPS SID。

```
CSid BackupOps() throw(...);
```

##  <a name="batch"></a>  Sids::Batch

返回 SECURITY_BATCH_RID SID。

```
CSid Batch() throw(...);
```

##  <a name="creatorgroup"></a>  Sids::CreatorGroup

返回 SECURITY_CREATOR_GROUP_RID SID。

```
CSid CreatorGroup() throw(...);
```

##  <a name="creatorgroupserver"></a>  Sids::CreatorGroupServer

返回 SECURITY_CREATOR_GROUP_SERVER_RID SID。

```
CSid CreatorGroupServer() throw(...);
```

##  <a name="creatorowner"></a>  Sids::CreatorOwner

返回 SECURITY_CREATOR_OWNER_RID SID。

```
CSid CreatorOwner() throw(...);
```

##  <a name="creatorownerserver"></a>  Sids::CreatorOwnerServer

返回 SECURITY_CREATOR_OWNER_SERVER_RID SID。

```
CSid CreatorOwnerServer() throw(...);
```

##  <a name="dialup"></a>  Sids::Dialup

返回 SECURITY_DIALUP_RID SID。

```
CSid Dialup() throw(...);
```

##  <a name="guests"></a>  Sids::Guests

返回 DOMAIN_ALIAS_RID_GUESTS SID。

```
CSid Guests() throw(...);
```

##  <a name="interactive"></a>  Sids::Interactive

返回 SECURITY_INTERACTIVE_RID SID。

```
CSid Interactive() throw(...);
```

##  <a name="local"></a>  Sids::Local

返回 SECURITY_LOCAL_RID SID。

```
CSid Local() throw(...);
```

##  <a name="network"></a>  Sids::Network

返回 SECURITY_NETWORK_RID SID。

```
CSid Network() throw(...);
```

##  <a name="networkservice"></a>  Sids::NetworkService

返回 SECURITY_NETWORK_SERVICE_RID SID。

```
CSid NetworkService() throw(...);
```

### <a name="remarks"></a>备注

使用 NetworkService 启用 NT AUTHORITY\NetworkService 用户读取 CPerfMon 安全对象。 NetworkService 将 SecurityAttribute 添加到 atl Server 代码，这将允许在 Windows XP Home Edition、 Windows XP Professional、 Windows Server 2003 和更高版本操作系统的 NetworkService 帐户下的登录名的 DLL。

在自定义日志计数器创建 Perfmon MMC 中的 atl Server CPerfMon 类后，计数器可能不会显示，尽管会正确显示实时视图中查看日志文件时。 CPerfMon 自定义性能计数器没有在"性能日志和警报"服务 (smlogsvc.exe) 上运行 Windows XP 家庭版、 Windows XP Professional、 Windows Server 2003 （或更高版本） 操作系统的必要权限。 "NT AUTHORITY\NetworkService"帐户下运行该服务。

##  <a name="null"></a>  Sids::Null

返回 SECURITY_NULL_RID SID。

```
CSid Null() throw(...);
```

##  <a name="prew2kaccess"></a>  Sids::PreW2KAccess

返回 DOMAIN_ALIAS_RID_PREW2KCOMPACCESS SID。

```
CSid PreW2KAccess() throw(...);
```

##  <a name="powerusers"></a>  Sids::PowerUsers

返回 DOMAIN_ALIAS_RID_POWER_USERS SID。

```
CSid PowerUsers() throw(...);
```

##  <a name="printops"></a>  Sids::PrintOps

返回 DOMAIN_ALIAS_RID_PRINT_OPS SID。

```
CSid PrintOps() throw(...);
```

##  <a name="proxy"></a>  Sids::Proxy

返回 SECURITY_PROXY_RID SID。

```
CSid Proxy() throw(...);
```

##  <a name="rasservers"></a>  Sids::RasServers

返回 DOMAIN_ALIAS_RID_RAS_SERVERS SID。

```
CSid RasServers() throw(...);
```

##  <a name="replicator"></a>  Sids::Replicator

返回 DOMAIN_ALIAS_RID_REPLICATOR SID。

```
CSid Replicator() throw(...);
```

##  <a name="restrictedcode"></a>  Sids::RestrictedCode

返回 SECURITY_RESTRICTED_CODE_RID SID。

```
CSid RestrictedCode() throw(...);
```

##  <a name="self"></a>  Sids::Self

返回 SECURITY_PRINCIPAL_SELF_RID SID。

```
CSid Self() throw(...);
```

##  <a name="serverlogon"></a>  Sids::ServerLogon

返回 SECURITY_SERVER_LOGON_RID SID。

```
CSid ServerLogon() throw(...);
```

##  <a name="service"></a>  Sids::Service

返回 SECURITY_SERVICE_RID SID。

```
CSid Service() throw(...);
```

##  <a name="system"></a>  Sids::System

返回 SECURITY_LOCAL_SYSTEM_RID SID。

```
CSid System() throw(...);
```

##  <a name="systemops"></a>  Sids::SystemOps

返回 DOMAIN_ALIAS_RID_SYSTEM_OPS SID。

```
CSid SystemOps() throw(...);
```

##  <a name="terminalserver"></a>  Sids::TerminalServer

返回 SECURITY_TERMINAL_SERVER_RID SID。

```
CSid TerminalServer() throw(...);
```

##  <a name="users"></a>  Sids::Users

返回 DOMAIN_ALIAS_RID_USERS SID。

```
CSid Users() throw(...);
```

##  <a name="world"></a>  Sids::World

返回 SECURITY_WORLD_RID SID。

```
CSid World() throw(...);
```

## <a name="see-also"></a>请参阅

[函数](../../atl/reference/atl-functions.md)
