---
title: "CAccessToken Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATLSECURITY/CAccessToken"
  - "ATL.CAccessToken"
  - "CAccessToken"
  - "ATL::CAccessToken"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAccessToken class"
ms.assetid: bb5c5945-56a5-4083-b442-76573cee83ab
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# CAccessToken Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类是访问令牌的包装。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
class CAccessToken  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CAccessToken::~CAccessToken](../Topic/CAccessToken::~CAccessToken.md)|该析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CAccessToken::Attach](../Topic/CAccessToken::Attach.md)|调用此方法将特定访问令牌处理的所有权。|  
|[CAccessToken::CheckTokenMembership](../Topic/CAccessToken::CheckTokenMembership.md)|调用此方法来确定指定的是否应在 `CAccessToken` 对象启用。|  
|[CAccessToken::CreateImpersonationToken](../Topic/CAccessToken::CreateImpersonationToken.md)|调用此方法创建新的模拟访问令牌。|  
|[CAccessToken::CreatePrimaryToken](../Topic/CAccessToken::CreatePrimaryToken.md)|调用此方法来创建新的主令牌。|  
|[CAccessToken::CreateProcessAsUser](../Topic/CAccessToken::CreateProcessAsUser.md)|在 `CAccessToken` 对象表示的用户的安全上下文调用此方法创建新进程运行。|  
|[CAccessToken::CreateRestrictedToken](../Topic/CAccessToken::CreateRestrictedToken.md)|调用此方法将创建一个新的，有限的 `CAccessToken` 对象。|  
|[CAccessToken::Detach](../Topic/CAccessToken::Detach.md)|调用此方法取消访问令牌的所有权。|  
|[CAccessToken::DisablePrivilege](../Topic/CAccessToken::DisablePrivilege.md)|调用此方法禁用了 `CAccessToken` 对象的权限。|  
|[CAccessToken::DisablePrivileges](../Topic/CAccessToken::DisablePrivileges.md)|调用此方法禁用了 `CAccessToken` 对象的一个或多个权限。|  
|[CAccessToken::EnablePrivilege](../Topic/CAccessToken::EnablePrivilege.md)|调用此方法以在 `CAccessToken` 对象的权限。|  
|[CAccessToken::EnablePrivileges](../Topic/CAccessToken::EnablePrivileges.md)|调用此方法以在 `CAccessToken` 对象的一个或多个权限。|  
|[CAccessToken::GetDefaultDacl](../Topic/CAccessToken::GetDefaultDacl.md)|调用此方法返回 `CAccessToken` 对象的默认DACL。|  
|[CAccessToken::GetEffectiveToken](../Topic/CAccessToken::GetEffectiveToken.md)|实际调用此方法获取 `CAccessToken` 对象等于访问标记当前线程的。|  
|[CAccessToken::GetGroups](../Topic/CAccessToken::GetGroups.md)|调用此方法返回 `CAccessToken` 对象的标记组。|  
|[CAccessToken::GetHandle](../Topic/CAccessToken::GetHandle.md)|调用此方法检索句柄访问令牌。|  
|[CAccessToken::GetImpersonationLevel](../Topic/CAccessToken::GetImpersonationLevel.md)|调用此方法获取访问令牌的模拟级别。|  
|[CAccessToken::GetLogonSessionId](../Topic/CAccessToken::GetLogonSessionId.md)|调用此方法获取登录会话ID与 `CAccessToken` 对象。|  
|[CAccessToken::GetLogonSid](../Topic/CAccessToken::GetLogonSid.md)|调用此方法获取登录SID与 `CAccessToken` 对象。|  
|[CAccessToken::GetOwner](../Topic/CAccessToken::GetOwner.md)|调用此方法获取所有者与 `CAccessToken` 对象。|  
|[CAccessToken::GetPrimaryGroup](../Topic/CAccessToken::GetPrimaryGroup.md)|调用此方法获取主要组与 `CAccessToken` 对象。|  
|[CAccessToken::GetPrivileges](../Topic/CAccessToken::GetPrivileges.md)|调用此方法获取权限集与 `CAccessToken` 对象。|  
|[CAccessToken::GetProcessToken](../Topic/CAccessToken::GetProcessToken.md)|调用此方法初始化访问标记的 `CAccessToken` 从给定进程。|  
|[CAccessToken::GetProfile](../Topic/CAccessToken::GetProfile.md)|调用此方法获取指向用户配置文件的处理与 `CAccessToken` 对象。|  
|[CAccessToken::GetSource](../Topic/CAccessToken::GetSource.md)|调用此方法获取 `CAccessToken` 对象的源。|  
|[CAccessToken::GetStatistics](../Topic/CAccessToken::GetStatistics.md)|调用此方法获取信息与 `CAccessToken` 对象。|  
|[CAccessToken::GetTerminalServicesSessionId](../Topic/CAccessToken::GetTerminalServicesSessionId.md)|调用此方法获取终端服务会话ID与 `CAccessToken` 对象。|  
|[CAccessToken::GetThreadToken](../Topic/CAccessToken::GetThreadToken.md)|调用此方法初始化标记的 `CAccessToken` 从特定线程。|  
|[CAccessToken::GetTokenId](../Topic/CAccessToken::GetTokenId.md)|调用此方法获取标记ID与 `CAccessToken` 对象。|  
|[CAccessToken::GetType](../Topic/CAccessToken::GetType.md)|调用此方法获取 `CAccessToken` 对象的标记类型。|  
|[CAccessToken::GetUser](../Topic/CAccessToken::GetUser.md)|调用此方法标识用户与 `CAccessToken` 对象。|  
|[CAccessToken::HKeyCurrentUser](../Topic/CAccessToken::HKeyCurrentUser.md)|调用此方法获取指向用户配置文件的处理与 `CAccessToken` 对象。|  
|[CAccessToken::Impersonate](../Topic/CAccessToken::Impersonate.md)|调用此方法分配模拟 `CAccessToken` 到线程。|  
|[CAccessToken::ImpersonateLoggedOnUser](../Topic/CAccessToken::ImpersonateLoggedOnUser.md)|调用此方法允许调用线程模拟一个登录用户的安全上下文。|  
|[CAccessToken::IsTokenRestricted](../Topic/CAccessToken::IsTokenRestricted.md)|如果 `CAccessToken` 对象包含有限的SID，列表中调用此方法测试。|  
|[CAccessToken::LoadUserProfile](../Topic/CAccessToken::LoadUserProfile.md)|调用此方法加载用户配置文件与 `CAccessToken` 对象。|  
|[CAccessToken::LogonUser](../Topic/CAccessToken::LogonUser.md)|调用此方法来创建该用户的登录会话与特定凭据。|  
|[CAccessToken::OpenCOMClientToken](../Topic/CAccessToken::OpenCOMClientToken.md)|调用此方法从处理来自客户端的COM服务器的内部调用初始化访问标记的 `CAccessToken` 从COM客户端。|  
|[CAccessToken::OpenNamedPipeClientToken](../Topic/CAccessToken::OpenNamedPipeClientToken.md)|调用此方法从对命名管道的服务器的内部请求初始化访问标记的 `CAccessToken` 从客户端。|  
|[CAccessToken::OpenRPCClientToken](../Topic/CAccessToken::OpenRPCClientToken.md)|调用此方法从处理从RPC客户端的服务器的内部调用初始化访问标记的 `CAccessToken` 从客户端。|  
|[CAccessToken::OpenThreadToken](../Topic/CAccessToken::OpenThreadToken.md)|调用此方法将模拟级别然后初始化标记的 `CAccessToken` 从特定线程。|  
|[CAccessToken::PrivilegeCheck](../Topic/CAccessToken::PrivilegeCheck.md)|调用此方法来确定指定的权限集是否在 **CAccessToken** 对象启用。|  
|[CAccessToken::Revert](../Topic/CAccessToken::Revert.md)|调用此方法停止使用模拟标记的线程。|  
|[CAccessToken::SetDefaultDacl](../Topic/CAccessToken::SetDefaultDacl.md)|调用此方法设置 `CAccessToken` 对象的默认DACL。|  
|[CAccessToken::SetOwner](../Topic/CAccessToken::SetOwner.md)|调用此方法设置 `CAccessToken` 对象的所有者。|  
|[CAccessToken::SetPrimaryGroup](../Topic/CAccessToken::SetPrimaryGroup.md)|调用此方法设置 `CAccessToken` 对象的主要操作组。|  
  
## 备注  
 [访问令牌](http://msdn.microsoft.com/library/windows/desktop/aa374909) 是描述进程或线程的安全性上下文的对象以及分配给每个用户登录到Windows NT或Windows 2000系统上。  
  
 有关访问控制设计介绍在Windows，请参见。[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [访问控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)。  
  
## 要求  
 **Header:** atlsecurity.h  
  
## 请参阅  
 [ATLSecurity示例](../../top/visual-cpp-samples.md)   
 [Access Tokens](http://msdn.microsoft.com/library/windows/desktop/aa374909)   
 [Class Overview](../../atl/atl-class-overview.md)