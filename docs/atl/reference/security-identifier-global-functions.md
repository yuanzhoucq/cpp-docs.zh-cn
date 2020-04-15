---
title: 安全标识符全局函数
ms.date: 11/04/2016
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
helpviewer_keywords:
- security IDs [C++]
- SIDs [C++], returning SID objects
ms.assetid: 85404dcb-c59b-4535-ab3d-66cfa37e87de
ms.openlocfilehash: 83326c13de7585806ab841f728f587f1131b5e8d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325992"
---
# <a name="security-identifier-global-functions"></a>安全标识符全局函数

这些函数返回常见的已知 SID 对象。

> [!IMPORTANT]
> 下表中列出的函数不能在 Windows 运行时中执行的应用程序中使用。

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
|[希德：：世界](#world)|返回 SECURITY_WORLD_RID SID。|

### <a name="requirements"></a>要求

**标题：** atlsecurity.h

## <a name="sidsaccountops"></a><a name="accountops"></a>Sids：：帐户

返回 DOMAIN_ALIAS_RID_ACCOUNT_OPS SID。

```
CSid AccountOps() throw(...);
```

## <a name="sidsadmins"></a><a name="admins"></a>Sids：：管理员

返回 DOMAIN_ALIAS_RID_ADMINS SID。

```
CSid Admins() throw(...);
```

## <a name="sidsanonymouslogon"></a><a name="anonymouslogon"></a>Sids：：匿名登录

返回 SECURITY_ANONYMOUS_LOGON_RID SID。

```
CSid AnonymousLogon() throw(...);
```

## <a name="sidsauthenticateduser"></a><a name="authenticateduser"></a>Sids：：经过身份验证的用户

返回 SECURITY_AUTHENTICATED_USER_RID SID。

```
CSid AuthenticatedUser() throw(...);
```

## <a name="sidsbackupops"></a><a name="backupops"></a>Sids：：备份操作

返回 DOMAIN_ALIAS_RID_BACKUP_OPS SID。

```
CSid BackupOps() throw(...);
```

## <a name="sidsbatch"></a><a name="batch"></a>Sids：：批次

返回 SECURITY_BATCH_RID SID。

```
CSid Batch() throw(...);
```

## <a name="sidscreatorgroup"></a><a name="creatorgroup"></a>Sids：：创造者组

返回 SECURITY_CREATOR_GROUP_RID SID。

```
CSid CreatorGroup() throw(...);
```

## <a name="sidscreatorgroupserver"></a><a name="creatorgroupserver"></a>Sids：：创造者群服务器

返回 SECURITY_CREATOR_GROUP_SERVER_RID SID。

```
CSid CreatorGroupServer() throw(...);
```

## <a name="sidscreatorowner"></a><a name="creatorowner"></a>Sids：：创造者所有者

返回 SECURITY_CREATOR_OWNER_RID SID。

```
CSid CreatorOwner() throw(...);
```

## <a name="sidscreatorownerserver"></a><a name="creatorownerserver"></a>Sids：：创造者所有者服务器

返回 SECURITY_CREATOR_OWNER_SERVER_RID SID。

```
CSid CreatorOwnerServer() throw(...);
```

## <a name="sidsdialup"></a><a name="dialup"></a>希德：:D亚里普

返回 SECURITY_DIALUP_RID SID。

```
CSid Dialup() throw(...);
```

## <a name="sidsguests"></a><a name="guests"></a>希德：：客人

返回 DOMAIN_ALIAS_RID_GUESTS SID。

```
CSid Guests() throw(...);
```

## <a name="sidsinteractive"></a><a name="interactive"></a>Sids：：互动

返回 SECURITY_INTERACTIVE_RID SID。

```
CSid Interactive() throw(...);
```

## <a name="sidslocal"></a><a name="local"></a>Sids：：本地

返回 SECURITY_LOCAL_RID SID。

```
CSid Local() throw(...);
```

## <a name="sidsnetwork"></a><a name="network"></a>Sids：：网络

返回 SECURITY_NETWORK_RID SID。

```
CSid Network() throw(...);
```

## <a name="sidsnetworkservice"></a><a name="networkservice"></a>Sids：：网络服务

返回 SECURITY_NETWORK_SERVICE_RID SID。

```
CSid NetworkService() throw(...);
```

### <a name="remarks"></a>备注

使用网络服务使 NT AUTHORITY_网络服务用户能够读取 CPerfMon 安全对象。 网络服务向 ATLServer 代码添加了一个安全属性，该代码将允许 DLL 在 Windows XP 家庭版、Windows XP 专业版、Windows Server 2003 和更大的操作系统上的网络服务帐户下登录。

在 Perfmon MMC 中使用 ATLServer CPerfMon 类创建自定义日志计数器时，在查看日志文件时可能不会显示这些计数器，尽管它们将在实时视图中正确显示。 CPerfMon 自定义性能计数器在 Windows XP 主版、Windows XP 专业版、Windows Server 2003（或更高版）操作系统上的"性能日志和警报"服务 （smlogsvc.exe） 下没有运行所需的权限。 此服务在"NT AUTHORITY_网络服务"帐户下运行。

## <a name="sidsnull"></a><a name="null"></a>Sids：：空

返回 SECURITY_NULL_RID SID。

```
CSid Null() throw(...);
```

## <a name="sidsprew2kaccess"></a><a name="prew2kaccess"></a>Sids：:PreW2KAccess

返回 DOMAIN_ALIAS_RID_PREW2KCOMPACCESS SID。

```
CSid PreW2KAccess() throw(...);
```

## <a name="sidspowerusers"></a><a name="powerusers"></a>Sids：:P用户

返回 DOMAIN_ALIAS_RID_POWER_USERS SID。

```
CSid PowerUsers() throw(...);
```

## <a name="sidsprintops"></a><a name="printops"></a>希德：:P林图普斯

返回 DOMAIN_ALIAS_RID_PRINT_OPS SID。

```
CSid PrintOps() throw(...);
```

## <a name="sidsproxy"></a><a name="proxy"></a>希德：:P罗西

返回 SECURITY_PROXY_RID SID。

```
CSid Proxy() throw(...);
```

## <a name="sidsrasservers"></a><a name="rasservers"></a>Sids：：拉塞塞

返回 DOMAIN_ALIAS_RID_RAS_SERVERS SID。

```
CSid RasServers() throw(...);
```

## <a name="sidsreplicator"></a><a name="replicator"></a>Sids：：复制器

返回 DOMAIN_ALIAS_RID_REPLICATOR SID。

```
CSid Replicator() throw(...);
```

## <a name="sidsrestrictedcode"></a><a name="restrictedcode"></a>Sids：：受限代码

返回 SECURITY_RESTRICTED_CODE_RID SID。

```
CSid RestrictedCode() throw(...);
```

## <a name="sidsself"></a><a name="self"></a>希德：：自我

返回 SECURITY_PRINCIPAL_SELF_RID SID。

```
CSid Self() throw(...);
```

## <a name="sidsserverlogon"></a><a name="serverlogon"></a>Sids：：服务器日志

返回 SECURITY_SERVER_LOGON_RID SID。

```
CSid ServerLogon() throw(...);
```

## <a name="sidsservice"></a><a name="service"></a>希德：：服务

返回 SECURITY_SERVICE_RID SID。

```
CSid Service() throw(...);
```

## <a name="sidssystem"></a><a name="system"></a>Sids：：系统

返回 SECURITY_LOCAL_SYSTEM_RID SID。

```
CSid System() throw(...);
```

## <a name="sidssystemops"></a><a name="systemops"></a>Sids：：系统操作

返回 DOMAIN_ALIAS_RID_SYSTEM_OPS SID。

```
CSid SystemOps() throw(...);
```

## <a name="sidsterminalserver"></a><a name="terminalserver"></a>Sids：：终端服务器

返回 SECURITY_TERMINAL_SERVER_RID SID。

```
CSid TerminalServer() throw(...);
```

## <a name="sidsusers"></a><a name="users"></a>Sids：用户

返回 DOMAIN_ALIAS_RID_USERS SID。

```
CSid Users() throw(...);
```

## <a name="sidsworld"></a><a name="world"></a>希德：：世界

返回 SECURITY_WORLD_RID SID。

```
CSid World() throw(...);
```

## <a name="see-also"></a>另请参阅

[函数](../../atl/reference/atl-functions.md)
