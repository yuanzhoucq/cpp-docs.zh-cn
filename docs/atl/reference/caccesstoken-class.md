---
title: CAccessToken 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAccessToken
- ATLSECURITY/ATL::CAccessToken
- ATLSECURITY/ATL::CAccessToken::Attach
- ATLSECURITY/ATL::CAccessToken::CheckTokenMembership
- ATLSECURITY/ATL::CAccessToken::CreateImpersonationToken
- ATLSECURITY/ATL::CAccessToken::CreatePrimaryToken
- ATLSECURITY/ATL::CAccessToken::CreateProcessAsUser
- ATLSECURITY/ATL::CAccessToken::CreateRestrictedToken
- ATLSECURITY/ATL::CAccessToken::Detach
- ATLSECURITY/ATL::CAccessToken::DisablePrivilege
- ATLSECURITY/ATL::CAccessToken::DisablePrivileges
- ATLSECURITY/ATL::CAccessToken::EnablePrivilege
- ATLSECURITY/ATL::CAccessToken::EnablePrivileges
- ATLSECURITY/ATL::CAccessToken::GetDefaultDacl
- ATLSECURITY/ATL::CAccessToken::GetEffectiveToken
- ATLSECURITY/ATL::CAccessToken::GetGroups
- ATLSECURITY/ATL::CAccessToken::GetHandle
- ATLSECURITY/ATL::CAccessToken::GetImpersonationLevel
- ATLSECURITY/ATL::CAccessToken::GetLogonSessionId
- ATLSECURITY/ATL::CAccessToken::GetLogonSid
- ATLSECURITY/ATL::CAccessToken::GetOwner
- ATLSECURITY/ATL::CAccessToken::GetPrimaryGroup
- ATLSECURITY/ATL::CAccessToken::GetPrivileges
- ATLSECURITY/ATL::CAccessToken::GetProcessToken
- ATLSECURITY/ATL::CAccessToken::GetProfile
- ATLSECURITY/ATL::CAccessToken::GetSource
- ATLSECURITY/ATL::CAccessToken::GetStatistics
- ATLSECURITY/ATL::CAccessToken::GetTerminalServicesSessionId
- ATLSECURITY/ATL::CAccessToken::GetThreadToken
- ATLSECURITY/ATL::CAccessToken::GetTokenId
- ATLSECURITY/ATL::CAccessToken::GetType
- ATLSECURITY/ATL::CAccessToken::GetUser
- ATLSECURITY/ATL::CAccessToken::HKeyCurrentUser
- ATLSECURITY/ATL::CAccessToken::Impersonate
- ATLSECURITY/ATL::CAccessToken::ImpersonateLoggedOnUser
- ATLSECURITY/ATL::CAccessToken::IsTokenRestricted
- ATLSECURITY/ATL::CAccessToken::LoadUserProfile
- ATLSECURITY/ATL::CAccessToken::LogonUser
- ATLSECURITY/ATL::CAccessToken::OpenCOMClientToken
- ATLSECURITY/ATL::CAccessToken::OpenNamedPipeClientToken
- ATLSECURITY/ATL::CAccessToken::OpenRPCClientToken
- ATLSECURITY/ATL::CAccessToken::OpenThreadToken
- ATLSECURITY/ATL::CAccessToken::PrivilegeCheck
- ATLSECURITY/ATL::CAccessToken::Revert
- ATLSECURITY/ATL::CAccessToken::SetDefaultDacl
- ATLSECURITY/ATL::CAccessToken::SetOwner
- ATLSECURITY/ATL::CAccessToken::SetPrimaryGroup
dev_langs:
- C++
helpviewer_keywords:
- CAccessToken class
ms.assetid: bb5c5945-56a5-4083-b442-76573cee83ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 881c86a75d9015117be4b51a8b7457bed4988fd3
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50078539"
---
# <a name="caccesstoken-class"></a>CAccessToken 类

此类是访问令牌的包装器。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
class CAccessToken
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CAccessToken::~CAccessToken](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CAccessToken::Attach](#attach)|调用此方法以获取给定的访问令牌的句柄的所有权。|
|[CAccessToken::CheckTokenMembership](#checktokenmembership)|调用此方法以确定是否在启用了指定的 SID`CAccessToken`对象。|
|[CAccessToken::CreateImpersonationToken](#createimpersonationtoken)|调用此方法以创建新的模拟访问令牌。|
|[CAccessToken::CreatePrimaryToken](#createprimarytoken)|调用此方法以创建新的主令牌。|
|[CAccessToken::CreateProcessAsUser](#createprocessasuser)|调用此方法以创建新的进程所表示的用户的安全上下文中运行`CAccessToken`对象。|
|[CAccessToken::CreateRestrictedToken](#createrestrictedtoken)|调用此方法以创建一个新受限`CAccessToken`对象。|
|[CAccessToken::Detach](#detach)|调用此方法，若要吊销的访问令牌的所有权。|
|[CAccessToken::DisablePrivilege](#disableprivilege)|调用此方法以禁用在特权`CAccessToken`对象。|
|[CAccessToken::DisablePrivileges](#disableprivileges)|调用此方法以禁用中的一个或多个权限`CAccessToken`对象。|
|[CAccessToken::EnablePrivilege](#enableprivilege)|调用此方法以启用中的特权`CAccessToken`对象。|
|[CAccessToken::EnablePrivileges](#enableprivileges)|调用此方法以启用中的一个或多个权限`CAccessToken`对象。|
|[CAccessToken::GetDefaultDacl](#getdefaultdacl)|调用此方法以返回`CAccessToken`对象的默认 DACL。|
|[CAccessToken::GetEffectiveToken](#geteffectivetoken)|调用此方法以获取`CAccessToken`对象等于当前线程对有效的访问令牌。|
|[CAccessToken::GetGroups](#getgroups)|调用此方法以返回`CAccessToken`对象的令牌组。|
|[CAccessToken::GetHandle](#gethandle)|调用此方法来检索访问令牌的句柄。|
|[CAccessToken::GetImpersonationLevel](#getimpersonationlevel)|调用此方法以从访问令牌获取的模拟级别。|
|[CAccessToken::GetLogonSessionId](#getlogonsessionid)|调用此方法以获取与关联的登录会话 ID`CAccessToken`对象。|
|[CAccessToken::GetLogonSid](#getlogonsid)|调用此方法以获取与关联的登录 SID`CAccessToken`对象。|
|[CAccessToken::GetOwner](#getowner)|调用此方法以获取与关联的所有者`CAccessToken`对象。|
|[CAccessToken::GetPrimaryGroup](#getprimarygroup)|调用此方法以获取与关联的主组`CAccessToken`对象。|
|[CAccessToken::GetPrivileges](#getprivileges)|调用此方法以获取与关联的权限`CAccessToken`对象。|
|[CAccessToken::GetProcessToken](#getprocesstoken)|调用此方法可使用给定进程中的访问令牌初始化 `CAccessToken`。|
|[CAccessToken::GetProfile](#getprofile)|调用此方法以获取指向关联的用户配置文件的句柄`CAccessToken`对象。|
|[CAccessToken::GetSource](#getsource)|调用此方法以获取的源`CAccessToken`对象。|
|[CAccessToken::GetStatistics](#getstatistics)|调用此方法以获取与关联信息`CAccessToken`对象。|
|[CAccessToken::GetTerminalServicesSessionId](#getterminalservicessessionid)|调用此方法以获取与关联的终端服务会话 ID`CAccessToken`对象。|
|[CAccessToken::GetThreadToken](#getthreadtoken)|调用此方法来初始化`CAccessToken`使用给定的线程中的令牌。|
|[CAccessToken::GetTokenId](#gettokenid)|调用此方法以获取与关联的标记 ID`CAccessToken`对象。|
|[CAccessToken::GetType](#gettype)|调用此方法以获取的令牌类型。`CAccessToken`对象。|
|[CAccessToken::GetUser](#getuser)|调用此方法来确定与关联的用户`CAccessToken`对象。|
|[CAccessToken::HKeyCurrentUser](#hkeycurrentuser)|调用此方法以获取指向关联的用户配置文件的句柄`CAccessToken`对象。|
|[CAccessToken::Impersonate](#impersonate)|调用此方法来分配内存模拟`CAccessToken`给线程。|
|[CAccessToken::ImpersonateLoggedOnUser](#impersonateloggedonuser)|调用此方法以允许调用线程模拟登录的用户的安全上下文。|
|[CAccessToken::IsTokenRestricted](#istokenrestricted)|调用此方法来测试如果`CAccessToken`对象包含一组受限 Sid。|
|[CAccessToken::LoadUserProfile](#loaduserprofile)|调用此方法以加载用户配置文件与相关联`CAccessToken`对象。|
|[CAccessToken::LogonUser](#logonuser)|调用此方法以创建与给定的凭据关联的用户的登录会话。|
|[CAccessToken::OpenCOMClientToken](#opencomclienttoken)|中调用此方法从 COM 服务器处理来自客户端执行调用以初始化`CAccessToken`从 COM 客户端的访问令牌。|
|[CAccessToken::OpenNamedPipeClientToken](#opennamedpipeclienttoken)|中调用此方法从服务器获取请求通过命名管道来初始化`CAccessToken`从客户端的访问令牌。|
|[CAccessToken::OpenRPCClientToken](#openrpcclienttoken)|中调用此方法从服务器来处理从 RPC 客户端执行调用以初始化`CAccessToken`从客户端的访问令牌。|
|[CAccessToken::OpenThreadToken](#openthreadtoken)|调用此方法以设置模拟级别，然后初始化`CAccessToken`使用给定的线程中的令牌。|
|[CAccessToken::PrivilegeCheck](#privilegecheck)|调用此方法以确定是否在中启用指定的一组特权`CAccessToken`对象。|
|[CAccessToken::Revert](#revert)|调用此方法以停止使用模拟标记的线程。|
|[CAccessToken::SetDefaultDacl](#setdefaultdacl)|调用此方法可设置默认的 DACL`CAccessToken`对象。|
|[CAccessToken::SetOwner](#setowner)|调用此方法以设置其所有者的`CAccessToken`对象。|
|[CAccessToken::SetPrimaryGroup](#setprimarygroup)|调用此方法以设置的主要组`CAccessToken`对象。|

## <a name="remarks"></a>备注

[访问令牌](/windows/desktop/SecAuthZ/access-tokens)是一个对象，用于描述进程或线程的安全上下文并分配给每个用户登录到 Windows 系统。

有关 Windows 中的访问控制模型的简介，请参阅[访问控制](/windows/desktop/SecAuthZ/access-control)Windows SDK 中。

## <a name="requirements"></a>要求

**标头：** atlsecurity.h

##  <a name="attach"></a>  CAccessToken::Attach

调用此方法以获取给定的访问令牌的句柄的所有权。

```
void Attach(HANDLE hToken) throw();
```

### <a name="parameters"></a>参数

*hToken*<br/>
句柄的访问令牌。

### <a name="remarks"></a>备注

在调试版本中，如果出现断言错误`CAccessToken`对象已具有访问令牌的所有权。

##  <a name="dtor"></a>  CAccessToken::~CAccessToken

析构函数。

```
virtual ~CAccessToken() throw();
```

### <a name="remarks"></a>备注

释放所有已分配的资源。

##  <a name="checktokenmembership"></a>  CAccessToken::CheckTokenMembership

调用此方法以确定是否在启用了指定的 SID`CAccessToken`对象。

```
bool CheckTokenMembership(
    const CSid& rSid,
    bool* pbIsMember) const throw(...);
```

### <a name="parameters"></a>参数

*rSid*<br/>
引用[CSid 类](../../atl/reference/csid-class.md)对象。

*pbIsMember*<br/>
指向一个变量来接收检查的结果。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

`CheckTokenMembership`方法检查是否存在的用户和组 Sid 的访问令牌中的 SID。 如果 SID 存在并且具有 SE_GROUP_ENABLED 属性*pbIsMember*是设置为 TRUE; 否则为它设置为 FALSE。

在调试版本中，如果出现断言错误*pbIsMember*不是有效的指针。

> [!NOTE]
>  `CAccessToken`对象必须是一个模拟标记和不主标记。

##  <a name="createimpersonationtoken"></a>  CAccessToken::CreateImpersonationToken

调用此方法以创建模拟访问令牌。

```
bool CreateImpersonationToken(
    CAccessToken* pImp,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) const throw(...);
```

### <a name="parameters"></a>参数

*pImp*<br/>
指向新`CAccessToken`对象。

*sil*<br/>
指定[SECURITY_IMPERSONATION_LEVEL](/windows/desktop/api/winnt/ne-winnt-_security_impersonation_level)枚举类型，提供新的令牌模拟级别。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

`CreateImpersonationToken` 调用[DuplicateToken](https://msdn.microsoft.com/library/windows/desktop/aa446616)以创建新的模拟令牌。

##  <a name="createprimarytoken"></a>  CAccessToken::CreatePrimaryToken

调用此方法以创建新的主令牌。

```
bool CreatePrimaryToken(
    CAccessToken* pPri,
    DWORD dwDesiredAccess = MAXIMUM_ALLOWED,
    const CSecurityAttributes* pTokenAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>参数

*pPri*<br/>
指向新`CAccessToken`对象。

*dwDesiredAccess*<br/>
指定新的令牌的请求的访问权限。 默认情况下，MAXIMUM_ALLOWED，请求有效的调用方的所有访问权限。 请参阅[的访问权限和访问掩码](/windows/desktop/SecAuthZ/access-rights-and-access-masks)的多个打开的访问权限。

*pTokenAttributes*<br/>
指向[SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560)结构，它指定新的令牌的安全描述符，并确定是否子进程可以继承标记。 如果*pTokenAttributes*为 NULL，该令牌获取的默认安全描述符，不能继承句柄。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

`CreatePrimaryToken` 调用[DuplicateTokenEx](https://msdn.microsoft.com/library/windows/desktop/aa446617)若要创建新的主令牌。

##  <a name="createprocessasuser"></a>  CAccessToken::CreateProcessAsUser

调用此方法以创建新的进程所表示的用户的安全上下文中运行`CAccessToken`对象。

```
bool CreateProcessAsUser(
    LPCTSTR pApplicationName,
    LPTSTR pCommandLine,
    LPPROCESS_INFORMATION pProcessInformation,
    LPSTARTUPINFO pStartupInfo,
    DWORD dwCreationFlags = NORMAL_PRIORITY_CLASS,
    bool bLoadProfile = false,
    const CSecurityAttributes* pProcessAttributes = NULL,
    const CSecurityAttributes* pThreadAttributes = NULL,
    bool bInherit = false,
    LPCTSTR pCurrentDirectory = NULL) throw();
```

### <a name="parameters"></a>参数

*pApplicationName*<br/>
指向一个以 null 结尾的字符串，指定要执行的模块。 此参数不能为 NULL。

*pCommandLine*<br/>
指向一个以 null 结尾的字符串，指定要执行的命令行。

*pProcessInformation*<br/>
指向[PROCESS_INFORMATION](/windows/desktop/api/processthreadsapi/ns-processthreadsapi-_process_information)接收有关新进程的标识信息的结构。

*pStartupInfo*<br/>
指向[STARTUPINFO](/windows/desktop/api/processthreadsapi/ns-processthreadsapi-_startupinfoa)结构，它指定新的进程的主窗口应如何显示。

*dwCreationFlags*<br/>
指定用于控制优先级类和过程的创建的其他标志。 请参阅 Win32 函数[CreateProcessAsUser](https://msdn.microsoft.com/library/windows/desktop/ms682429)标志的列表。

*bLoadProfile*<br/>
如果为 TRUE，加载用户的配置文件[LoadUserProfile](/windows/desktop/api/userenv/nf-userenv-loaduserprofilea)。

*pProcessAttributes*<br/>
指向[SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560)结构，它指定新的进程的安全描述符，并确定是否子进程可以继承返回的句柄。 如果*pProcessAttributes*为 NULL，该过程获取的默认安全描述符，不能继承句柄。

*pThreadAttributes*<br/>
指向[SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560)结构，它指定新线程的安全描述符，并确定是否子进程可以继承返回的句柄。 如果*pThreadAttributes*为 NULL，该线程将获取的默认安全描述符，不能继承句柄。

*bInherit*<br/>
指示新进程是否继承自调用进程句柄。 如果为 TRUE，由新进程继承调用进程中的每个可继承打开句柄。 继承句柄具有相同的值和访问权限的原始句柄。

*pCurrentDirectory*<br/>
指向一个以 null 结尾的字符串，指定当前驱动器和目录的新进程。 字符串必须包含一个驱动器号的完整路径。 如果此参数为 NULL，新进程将与调用进程具有相同的当前驱动器和目录。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

`CreateProcessAsUser` 使用`CreateProcessAsUser`Win32 函数来创建新的进程所表示的用户的安全上下文中运行`CAccessToken`对象。 请参阅的说明[CreateProcessAsUser](https://msdn.microsoft.com/library/windows/desktop/ms682429)函数所需的参数的完整讨论。

此方法才能成功， `CAccessToken` （除非它是受限制的令牌），对象必须保留 AssignPrimaryToken 和 IncreaseQuota 特权。

##  <a name="createrestrictedtoken"></a>  CAccessToken::CreateRestrictedToken

调用此方法以创建一个新受限`CAccessToken`对象。

```
bool CreateRestrictedToken(
    CAccessToken* pRestrictedToken,
    const CTokenGroups& SidsToDisable,
    const CTokenGroups& SidsToRestrict,
    const CTokenPrivileges& PrivilegesToDelete = CTokenPrivileges()) const throw(...);
```

### <a name="parameters"></a>参数

*pRestrictedToken*<br/>
将新的、 受限`CAccessToken`对象。

*SidsToDisable*<br/>
一个`CTokenGroups`对象，它指定仅拒绝 Sid。

*SidsToRestrict*<br/>
一个`CTokenGroups`对象，它指定的限制 Sid。

*PrivilegesToDelete*<br/>
一个`CTokenPrivileges`对象，它在受限令牌中指定要删除的特权。 默认值创建一个空的对象。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

`CreateRestrictedToken` 使用[CreateRestrictedToken](https://msdn.microsoft.com/library/windows/desktop/aa446583) Win32 函数来创建一个新`CAccessToken`具有限制的对象。

> [!IMPORTANT]
>  使用时`CreateRestrictedToken`，确保满足以下： 现有令牌是否有效 （且不由用户输入） 和*SidsToDisable*并*PrivilegesToDelete*同时有效 （且不由用户输入）。 如果该方法返回 FALSE，则拒绝功能。

##  <a name="detach"></a>  CAccessToken::Detach

调用此方法，若要吊销的访问令牌的所有权。

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>返回值

返回的句柄`CAccessToken`已分离的。

### <a name="remarks"></a>备注

此方法撤消`CAccessToken`的访问令牌的所有权。

##  <a name="disableprivilege"></a>  CAccessToken::DisablePrivilege

调用此方法以禁用在特权`CAccessToken`对象。

```
bool DisablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>参数

*pszPrivilege*<br/>
包含在中禁用的特权的字符串指针`CAccessToken`对象。

*pPreviousState*<br/>
指向`CTokenPrivileges`对象，它将包含以前的状态的特权。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

##  <a name="disableprivileges"></a>  CAccessToken::DisablePrivileges

调用此方法以禁用中的一个或多个权限`CAccessToken`对象。

```
bool DisablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>参数

*rPrivileges*<br/>
指向包含要在中禁用的特权的字符串数组`CAccessToken`对象。

*pPreviousState*<br/>
指向`CTokenPrivileges`对象，它将包含以前的状态的特权。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

##  <a name="enableprivilege"></a>  CAccessToken::EnablePrivilege

调用此方法以启用中的特权`CAccessToken`对象。

```
bool EnablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>参数

*pszPrivilege*<br/>
包含在中启用的特权的字符串指针`CAccessToken`对象。

*pPreviousState*<br/>
指向`CTokenPrivileges`对象，它将包含以前的状态的特权。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

##  <a name="enableprivileges"></a>  CAccessToken::EnablePrivileges

调用此方法以启用中的一个或多个权限`CAccessToken`对象。

```
bool EnablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>参数

*rPrivileges*<br/>
指向包含要在中启用的特权的字符串数组`CAccessToken`对象。

*pPreviousState*<br/>
指向`CTokenPrivileges`对象，它将包含以前的状态的特权。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

##  <a name="getdefaultdacl"></a>  CAccessToken::GetDefaultDacl

调用此方法以返回`CAccessToken`对象的默认 DACL。

```
bool GetDefaultDacl(CDacl* pDacl) const throw(...);
```

### <a name="parameters"></a>参数

*pDacl*<br/>
指向[CDacl 类](../../atl/reference/cdacl-class.md)对象以接收`CAccessToken`对象的默认 DACL。

### <a name="return-value"></a>返回值

如果默认的 DACL 具有否则已恢复，则为 FALSE，则返回 TRUE。

##  <a name="geteffectivetoken"></a>  CAccessToken::GetEffectiveToken

调用此方法以获取`CAccessToken`对象等于当前线程对有效的访问令牌。

```
bool GetEffectiveToken(DWORD dwDesiredAccess) throw();
```

### <a name="parameters"></a>参数

*dwDesiredAccess*<br/>
指定一个访问掩码，该掩码指定对访问令牌发起访问的请求类型。 这些请求的访问类型与令牌的 DACL 比较来确定同意或拒绝哪些访问。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

##  <a name="getgroups"></a>  CAccessToken::GetGroups

调用此方法以返回`CAccessToken`对象的令牌组。

```
bool GetGroups(CTokenGroups* pGroups) const throw(...);
```

### <a name="parameters"></a>参数

*pGroups*<br/>
指向[CTokenGroups 类](../../atl/reference/ctokengroups-class.md)对象以接收组信息。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

##  <a name="gethandle"></a>  CAccessToken::GetHandle

调用此方法来检索访问令牌的句柄。

```
HANDLE GetHandle() const throw();
```

### <a name="return-value"></a>返回值

返回的句柄`CAccessToken`对象的访问令牌。

##  <a name="getimpersonationlevel"></a>  CAccessToken::GetImpersonationLevel

调用此方法以从访问令牌获取的模拟级别。

```
bool GetImpersonationLevel(
    SECURITY_IMPERSONATION_LEVEL* pImpersonationLevel) const throw(...);
```

### <a name="parameters"></a>参数

*pImpersonationLevel*<br/>
指向[SECURITY_IMPERSONATION_LEVEL](/windows/desktop/api/winnt/ne-winnt-_security_impersonation_level)将接收模拟级别信息的枚举类型。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

##  <a name="getlogonsessionid"></a>  CAccessToken::GetLogonSessionId

调用此方法以获取与关联的登录会话 ID`CAccessToken`对象。

```
bool GetLogonSessionId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>参数

*pluid*<br/>
指向[LUID](/windows/desktop/api/winnt/ns-winnt-_luid)中有哪些将接收登录会话的 id。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

在调试版本中，如果出现断言错误*pluid*是无效的值。

##  <a name="getlogonsid"></a>  CAccessToken::GetLogonSid

调用此方法以获取与关联的登录 SID`CAccessToken`对象。

```
bool GetLogonSid(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>参数

*pSid*<br/>
指向[CSid 类](../../atl/reference/csid-class.md)对象。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

在调试版本中，如果出现断言错误*pSid*是无效的值。

##  <a name="getowner"></a>  CAccessToken::GetOwner

调用此方法以获取与关联的所有者`CAccessToken`对象。

```
bool GetOwner(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>参数

*pSid*<br/>
指向[CSid 类](../../atl/reference/csid-class.md)对象。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

默认情况下，在此访问令牌有效期间创建的任何对象上设置所有者。

##  <a name="getprimarygroup"></a>  CAccessToken::GetPrimaryGroup

调用此方法以获取与关联的主组`CAccessToken`对象。

```
bool GetPrimaryGroup(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>参数

*pSid*<br/>
指向[CSid 类](../../atl/reference/csid-class.md)对象。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

默认情况下，在此访问令牌有效期间创建的任何对象上设置组。

##  <a name="getprivileges"></a>  CAccessToken::GetPrivileges

调用此方法以获取与关联的权限`CAccessToken`对象。

```
bool GetPrivileges(CTokenPrivileges* pPrivileges) const throw(...);
```

### <a name="parameters"></a>参数

*pPrivileges*<br/>
指向[CTokenPrivileges 类](../../atl/reference/ctokenprivileges-class.md)对象以接收权限。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

##  <a name="getprocesstoken"></a>  CAccessToken::GetProcessToken

调用此方法可使用给定进程中的访问令牌初始化 `CAccessToken`。

```
bool GetProcessToken(DWORD dwDesiredAccess, HANDLE hProcess = NULL) throw();
```

### <a name="parameters"></a>参数

*dwDesiredAccess*<br/>
指定一个访问掩码，该掩码指定对访问令牌发起访问的请求类型。 这些请求的访问类型与令牌的 DACL 比较来确定同意或拒绝哪些访问。

*hProcess*<br/>
用于访问令牌已打开的进程的句柄。 如果使用默认值为 NULL，则使用当前进程。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

调用[OpenProcessToken](https://msdn.microsoft.com/library/aa379295) Win32 函数。

##  <a name="getprofile"></a>  CAccessToken::GetProfile

调用此方法以获取指向关联的用户配置文件的句柄`CAccessToken`对象。

```
HANDLE GetProfile() const throw();
```

### <a name="return-value"></a>返回值

返回指向用户配置文件，则为 NULL，如果没有配置文件存在的句柄。

##  <a name="getsource"></a>  CAccessToken::GetSource

调用此方法以获取的源`CAccessToken`对象。

```
bool GetSource(TOKEN_SOURCE* pSource) const throw(...);
```

### <a name="parameters"></a>参数

*pSource*<br/>
指向[TOKEN_SOURCE](/windows/desktop/api/winnt/ns-winnt-_token_source)结构。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

##  <a name="getstatistics"></a>  CAccessToken::GetStatistics

调用此方法以获取与关联信息`CAccessToken`对象。

```
bool GetStatistics(TOKEN_STATISTICS* pStatistics) const throw(...);
```

### <a name="parameters"></a>参数

*pStatistics*<br/>
指向[TOKEN_STATISTICS](/windows/desktop/api/winnt/ns-winnt-_token_statistics)结构。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

##  <a name="getterminalservicessessionid"></a>  CAccessToken::GetTerminalServicesSessionId

调用此方法以获取与关联的终端服务会话 ID`CAccessToken`对象。

```
bool GetTerminalServicesSessionId(DWORD* pdwSessionId) const throw(...);
```

### <a name="parameters"></a>参数

*pdwSessionId*<br/>
终端服务会话 id。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

##  <a name="getthreadtoken"></a>  CAccessToken::GetThreadToken

调用此方法来初始化`CAccessToken`使用给定的线程中的令牌。

```
bool GetThreadToken(
    DWORD dwDesiredAccess,
    HANDLE hThread = NULL,
    bool bOpenAsSelf = true) throw();
```

### <a name="parameters"></a>参数

*dwDesiredAccess*<br/>
指定一个访问掩码，该掩码指定对访问令牌发起访问的请求类型。 这些请求的访问类型与令牌的 DACL 比较来确定同意或拒绝哪些访问。

*hThread*<br/>
句柄的访问令牌已打开的线程。

*bOpenAsSelf*<br/>
指示是否针对线程调用的安全上下文进行访问检查`GetThreadToken`方法或对调用线程的过程的安全上下文。

如果此参数为 FALSE，为调用线程使用的安全上下文执行访问检查。 如果线程正在模拟客户端，此安全上下文可为客户端进程。 此参数为 TRUE，则为调用线程使用该过程的安全上下文进行访问检查。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

##  <a name="gettokenid"></a>  CAccessToken::GetTokenId

调用此方法以获取与关联的标记 ID`CAccessToken`对象。

```
bool GetTokenId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>参数

*pluid*<br/>
指向[LUID](/windows/desktop/api/winnt/ns-winnt-_luid)中有哪些将接收令牌的 id。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

##  <a name="gettype"></a>  CAccessToken::GetType

调用此方法以获取的令牌类型。`CAccessToken`对象。

```
bool GetType(TOKEN_TYPE* pType) const throw(...);
```

### <a name="parameters"></a>参数

*pType*<br/>
地址[TOKEN_TYPE](/windows/desktop/api/winnt/ne-winnt-_token_type)的成功后，收到的令牌的类型的变量。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

TOKEN_TYPE 枚举类型包含区分主令牌和模拟标记的值。

##  <a name="getuser"></a>  CAccessToken::GetUser

调用此方法来确定与关联的用户`CAccessToken`对象。

```
bool GetUser(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>参数

*pSid*<br/>
指向[CSid 类](../../atl/reference/csid-class.md)对象。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

##  <a name="hkeycurrentuser"></a>  CAccessToken::HKeyCurrentUser

调用此方法以获取指向关联的用户配置文件的句柄`CAccessToken`对象。

```
HKEY HKeyCurrentUser() const throw();
```

### <a name="return-value"></a>返回值

返回指向用户配置文件，则为 NULL，如果没有配置文件存在的句柄。

##  <a name="impersonate"></a>  CAccessToken::Impersonate

调用此方法来分配内存模拟`CAccessToken`给线程。

```
bool Impersonate(HANDLE hThread = NULL) const throw(...);
```

### <a name="parameters"></a>参数

*hThread*<br/>
若要将分配到的模拟标记的线程的句柄。 必须使用 TOKEN_IMPERSONATE 的访问权限打开此句柄。 如果*hThread*为 NULL，该方法会导致线程停止使用的模拟令牌。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

在调试版本中，如果出现断言错误`CAccessToken`不具有对令牌的有效指针。

[CAutoRevertImpersonation 类](../../atl/reference/cautorevertimpersonation-class.md)可用于自动还原模拟的访问令牌。

##  <a name="impersonateloggedonuser"></a>  CAccessToken::ImpersonateLoggedOnUser

调用此方法以允许调用线程模拟登录的用户的安全上下文。

```
bool ImpersonateLoggedOnUser() const throw(...);
```

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

> [!IMPORTANT]
>  如果出于任何原因，对模拟函数的调用失败，未模拟该客户端和客户端请求执行调用进程的安全上下文中。 如果进程正在运行高特权帐户，或作为管理组的成员，用户可能能够执行的操作，系统将否则允许他或她。 因此，此函数的返回值始终应进行确认。

##  <a name="istokenrestricted"></a>  CAccessToken::IsTokenRestricted

调用此方法来测试如果`CAccessToken`对象包含一组受限 Sid。

```
bool IsTokenRestricted() const throw();
```

### <a name="return-value"></a>返回值

如果该对象包含一系列限制 Sid，FALSE，如果不有任何限制 Sid 或如果方法失败，返回 TRUE。

##  <a name="loaduserprofile"></a>  CAccessToken::LoadUserProfile

调用此方法以加载用户配置文件与相关联`CAccessToken`对象。

```
bool LoadUserProfile() throw(...);
```

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

在调试版本中，如果出现断言错误`CAccessToken`不包含有效的令牌，或者如果用户配置文件已存在。

##  <a name="logonuser"></a>  CAccessToken::LogonUser

调用此方法以创建与给定的凭据关联的用户的登录会话。

```
bool LogonUser(
    LPCTSTR pszUserName,
    LPCTSTR pszDomain,
    LPCTSTR pszPassword,
    DWORD dwLogonType = LOGON32_LOGON_INTERACTIVE,
    DWORD dwLogonProvider = LOGON32_PROVIDER_DEFAULT) throw();
```

### <a name="parameters"></a>参数

*pszUserName*<br/>
指定用户名称的以 null 结尾的字符串指针。 这是用于登录到的用户帐户的名称。

*pszDomain*<br/>
指定的域或其帐户数据库中包含的服务器名称的以 null 结尾的字符串指针*pszUserName*帐户。

*pszPassword*<br/>
指定指定的用户帐户的明文密码的以 null 结尾的字符串指针*pszUserName*。

*dwLogonType*<br/>
指定要执行的登录操作的类型。 请参阅[LogonUser](/windows/desktop/api/winbase/nf-winbase-logonusera)的更多详细信息。

*dwLogonProvider*<br/>
指定登录提供程序。 请参阅[LogonUser](/windows/desktop/api/winbase/nf-winbase-logonusera)的更多详细信息。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

从登录令牌生成将与关联的访问`CAccessToken`。 此方法才能成功，`CAccessToken`对象必须保留 SE_TCB_NAME 权限，识别持有者作为基的受信任计算机的一部分。 请参阅[LogonUser](/windows/desktop/api/winbase/nf-winbase-logonusera)详细了解所需的特权。

##  <a name="opencomclienttoken"></a>  CAccessToken::OpenCOMClientToken

中调用此方法从 COM 服务器处理来自客户端执行调用以初始化`CAccessToken`从 COM 客户端的访问令牌。

```
bool OpenCOMClientToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>参数

*dwDesiredAccess*<br/>
指定一个访问掩码，该掩码指定对访问令牌发起访问的请求类型。 这些请求的访问类型与令牌的 DACL 比较来确定同意或拒绝哪些访问。

*bImpersonate*<br/>
如果为 TRUE，则当前线程将模拟调用 COM 客户端，如果此调用成功完成。 如果为 FALSE，将打开访问令牌，但该线程将无权模拟令牌，此调用完成时。

*bOpenAsSelf*<br/>
指示是否针对线程调用的安全上下文进行访问检查[GetThreadToken](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getcurrentthread)方法或对调用线程的过程的安全上下文。

如果此参数为 FALSE，为调用线程使用的安全上下文执行访问检查。 如果线程正在模拟客户端，此安全上下文可为客户端进程。 此参数为 TRUE，则为调用线程使用该过程的安全上下文进行访问检查。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

[CAutoRevertImpersonation 类](../../atl/reference/cautorevertimpersonation-class.md)可用于自动还原模拟的访问令牌通过设置来创建*bImpersonate*标志为 TRUE。

##  <a name="opennamedpipeclienttoken"></a>  CAccessToken::OpenNamedPipeClientToken

中调用此方法从服务器获取请求通过命名管道来初始化`CAccessToken`从客户端的访问令牌。

```
bool OpenNamedPipeClientToken(
    HANDLE hPipe,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>参数

*hPipe*<br/>
命名管道的句柄。

*dwDesiredAccess*<br/>
指定一个访问掩码，该掩码指定对访问令牌发起访问的请求类型。 这些请求的访问类型与令牌的 DACL 比较来确定同意或拒绝哪些访问。

*bImpersonate*<br/>
如果为 TRUE，则当前线程将模拟调用管道客户端，如果此调用成功完成。 如果为 FALSE，将打开访问令牌，但该线程将无权模拟令牌，此调用完成时。

*bOpenAsSelf*<br/>
指示是否针对线程调用的安全上下文进行访问检查[GetThreadToken](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getcurrentthread)方法或对调用线程的过程的安全上下文。

如果此参数为 FALSE，为调用线程使用的安全上下文执行访问检查。 如果线程正在模拟客户端，此安全上下文可为客户端进程。 此参数为 TRUE，则为调用线程使用该过程的安全上下文进行访问检查。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

[CAutoRevertImpersonation 类](../../atl/reference/cautorevertimpersonation-class.md)可用于自动还原模拟的访问令牌通过设置来创建*bImpersonate*标志为 TRUE。

##  <a name="openrpcclienttoken"></a>  CAccessToken::OpenRPCClientToken

中调用此方法从服务器来处理从 RPC 客户端执行调用以初始化`CAccessToken`从客户端的访问令牌。

```
bool OpenRPCClientToken(
    RPC_BINDING_HANDLE BindingHandle,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>参数

*BindingHandle*<br/>
表示与客户端的绑定在服务器上的绑定句柄。

*dwDesiredAccess*<br/>
指定一个访问掩码，该掩码指定对访问令牌发起访问的请求类型。 这些请求的访问类型与令牌的 DACL 比较来确定同意或拒绝哪些访问。

*bImpersonate*<br/>
如果为 TRUE，则当前线程将模拟调用的 RPC 客户端，如果此调用成功完成。 如果为 FALSE，将打开访问令牌，但该线程将无权模拟令牌，此调用完成时。

*bOpenAsSelf*<br/>
指示是否针对线程调用的安全上下文进行访问检查[GetThreadToken](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getcurrentthread)方法或对调用线程的过程的安全上下文。

如果此参数为 FALSE，为调用线程使用的安全上下文执行访问检查。 如果线程正在模拟客户端，此安全上下文可为客户端进程。 此参数为 TRUE，则为调用线程使用该过程的安全上下文进行访问检查。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

[CAutoRevertImpersonation 类](../../atl/reference/cautorevertimpersonation-class.md)可用于自动还原模拟的访问令牌通过设置来创建*bImpersonate*标志为 TRUE。

##  <a name="openthreadtoken"></a>  CAccessToken::OpenThreadToken

调用此方法以设置模拟级别，然后初始化`CAccessToken`使用给定的线程中的令牌。

```
bool OpenThreadToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) throw(...);
```

### <a name="parameters"></a>参数

*dwDesiredAccess*<br/>
指定一个访问掩码，该掩码指定对访问令牌发起访问的请求类型。 这些请求的访问类型与令牌的 DACL 比较来确定同意或拒绝哪些访问。

*bImpersonate*<br/>
如果为 TRUE，该线程将保留在请求的模拟级别中，此方法完成后。 如果为 FALSE，该线程将恢复到其原始的模拟级别。

*bOpenAsSelf*<br/>
指示是否针对线程调用的安全上下文进行访问检查[GetThreadToken](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getcurrentthread)方法或对调用线程的过程的安全上下文。

如果此参数为 FALSE，为调用线程使用的安全上下文执行访问检查。 如果线程正在模拟客户端，此安全上下文可为客户端进程。 此参数为 TRUE，则为调用线程使用该过程的安全上下文进行访问检查。

*sil*<br/>
指定[SECURITY_IMPERSONATION_LEVEL](/windows/desktop/api/winnt/ne-winnt-_security_impersonation_level)枚举类型，用于提供令牌的模拟级别。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

`OpenThreadToken` 类似于[CAccessToken::GetThreadToken](#getthreadtoken)，但在初始化之前设置的模拟级别`CAccessToken`从线程的访问令牌。

[CAutoRevertImpersonation 类](../../atl/reference/cautorevertimpersonation-class.md)可用于自动还原模拟的访问令牌通过设置来创建*bImpersonate*标志为 TRUE。

##  <a name="privilegecheck"></a>  CAccessToken::PrivilegeCheck

调用此方法以确定是否在中启用指定的一组特权`CAccessToken`对象。

```
bool PrivilegeCheck(
    PPRIVILEGE_SET RequiredPrivileges,
    bool* pbResult) const throw();
```

### <a name="parameters"></a>参数

*RequiredPrivileges*<br/>
指向[PRIVILEGE_SET](/windows/desktop/api/winnt/ns-winnt-_privilege_set)结构。

*pbResult*<br/>
指向的值的方法设置指示是否在启用任何或所有指定的特权`CAccessToken`对象。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

当`PrivilegeCheck`返回时，`Attributes`的每个成员[LUID_AND_ATTRIBUTES](/windows/desktop/api/winnt/ns-winnt-_luid_and_attributes)结构设置为 SE_PRIVILEGE_USED_FOR_ACCESS，如果启用了相应的权限。 此方法调用[PrivilegeCheck](https://msdn.microsoft.com/library/windows/desktop/aa379304) Win32 函数。

##  <a name="revert"></a>  CAccessToken::Revert

调用此方法以停止从使用模拟标记的线程。

```
bool Revert(HANDLE hThread = NULL) const throw();
```

### <a name="parameters"></a>参数

*hThread*<br/>
若要模拟从还原的线程的句柄。 如果*hThread*为 NULL，则假定为当前线程。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

可以使用自动执行还原操作的模拟令牌[CAutoRevertImpersonation 类](../../atl/reference/cautorevertimpersonation-class.md)。

##  <a name="setdefaultdacl"></a>  CAccessToken::SetDefaultDacl

调用此方法可设置默认的 DACL`CAccessToken`对象。

```
bool SetDefaultDacl(const CDacl& rDacl) throw(...);
```

### <a name="parameters"></a>参数

*rDacl*<br/>
新的默认[CDacl 类](../../atl/reference/cdacl-class.md)信息。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

默认的 DACL 是实际上使用此访问令牌创建新对象时，默认情况下使用的 DACL。

##  <a name="setowner"></a>  CAccessToken::SetOwner

调用此方法以设置其所有者的`CAccessToken`对象。

```
bool SetOwner(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>参数

*rSid*<br/>
[CSid 类](../../atl/reference/csid-class.md)对象，其中包含所有者信息。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

所有者是在此访问令牌有效期间创建的新对象使用的默认所有者。

##  <a name="setprimarygroup"></a>  CAccessToken::SetPrimaryGroup

调用此方法以设置的主要组`CAccessToken`对象。

```
bool SetPrimaryGroup(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>参数

*rSid*<br/>
[CSid 类](../../atl/reference/csid-class.md)对象，其中包含的主要组信息。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

主要组是在此访问令牌有效期间创建的新对象的默认组。

## <a name="see-also"></a>请参阅

[ATLSecurity 示例](../../visual-cpp-samples.md)<br/>
[访问令牌](/windows/desktop/SecAuthZ/access-tokens)<br/>
[类概述](../../atl/atl-class-overview.md)
