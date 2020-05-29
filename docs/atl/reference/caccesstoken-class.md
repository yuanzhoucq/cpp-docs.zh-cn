---
title: CAccessToken 类
ms.date: 07/02/2019
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
helpviewer_keywords:
- CAccessToken class
ms.assetid: bb5c5945-56a5-4083-b442-76573cee83ab
ms.openlocfilehash: 93e7d6b3bbd26a765e49791a1122cba2a68f6565
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168470"
---
# <a name="caccesstoken-class"></a>CAccessToken 类

此类是访问令牌的包装器。

> [!IMPORTANT]
> 此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```cpp
class CAccessToken
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CAccessToken：： ~ CAccessToken](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CAccessToken：： Attach](#attach)|调用此方法以获取给定访问令牌句柄的所有权。|
|[CAccessToken：： CheckTokenMembership](#checktokenmembership)|调用此方法以确定是否在`CAccessToken`对象中启用了指定的 SID。|
|[CAccessToken：： CreateImpersonationToken](#createimpersonationtoken)|调用此方法以创建新的模拟访问令牌。|
|[CAccessToken：： CreatePrimaryToken](#createprimarytoken)|调用此方法以创建新的主令牌。|
|[CAccessToken：： CreateProcessAsUser](#createprocessasuser)|调用此方法可创建一个新进程，该进程在由`CAccessToken`对象表示的用户的安全上下文中运行。|
|[CAccessToken：： CreateRestrictedToken](#createrestrictedtoken)|调用此方法可创建一个新的受`CAccessToken`限制的对象。|
|[CAccessToken：:D etach](#detach)|调用此方法可撤消访问令牌的所有权。|
|[CAccessToken：:D isablePrivilege](#disableprivilege)|调用此方法可禁用`CAccessToken`对象中的权限。|
|[CAccessToken：:D isablePrivileges](#disableprivileges)|调用此方法可禁用对象中的`CAccessToken`一个或多个权限。|
|[CAccessToken：： EnablePrivilege](#enableprivilege)|调用此方法可在`CAccessToken`对象中启用权限。|
|[CAccessToken：： EnablePrivileges](#enableprivileges)|调用此方法以启用对象中的`CAccessToken`一个或多个权限。|
|[CAccessToken：： GetDefaultDacl](#getdefaultdacl)|调用此方法以返回`CAccessToken`对象的默认 DACL。|
|[CAccessToken：： GetEffectiveToken](#geteffectivetoken)|调用此方法可使`CAccessToken`对象等于当前线程的有效访问令牌。|
|[CAccessToken：： Ldapauthentication.getgroups](#getgroups)|调用此方法以返回`CAccessToken`对象的标记组。|
|[CAccessToken：： GetHandle](#gethandle)|调用此方法以检索访问令牌的句柄。|
|[CAccessToken：： GetImpersonationLevel](#getimpersonationlevel)|调用此方法可从访问令牌中获取模拟级别。|
|[CAccessToken：： GetLogonSessionId](#getlogonsessionid)|调用此方法以获取与`CAccessToken`对象关联的登录会话 ID。|
|[CAccessToken：： GetLogonSid](#getlogonsid)|调用此方法以获取与`CAccessToken`对象关联的登录 SID。|
|[CAccessToken：： GetOwner](#getowner)|调用此方法以获取与`CAccessToken`对象关联的所有者。|
|[CAccessToken：： GetPrimaryGroup](#getprimarygroup)|调用此方法以获取与`CAccessToken`对象关联的主要组。|
|[CAccessToken：： GetPrivileges](#getprivileges)|调用此方法以获取与`CAccessToken`对象关联的特权。|
|[CAccessToken：： GetProcessToken](#getprocesstoken)|调用此方法可使用给定进程中的访问令牌初始化 `CAccessToken`。|
|[CAccessToken：： GetProfile](#getprofile)|调用此方法可获取指向与`CAccessToken`对象关联的用户配置文件的句柄。|
|[CAccessToken：： GetSource](#getsource)|调用此方法以获取`CAccessToken`对象的源。|
|[CAccessToken：： GetStatistics](#getstatistics)|调用此方法以获取与对象关联的`CAccessToken`信息。|
|[CAccessToken：： GetTerminalServicesSessionId](#getterminalservicessessionid)|调用此方法以获取与`CAccessToken`对象关联的终端服务会话 ID。|
|[CAccessToken：： GetThreadToken](#getthreadtoken)|调用此方法可`CAccessToken`通过给定线程中的标记初始化。|
|[CAccessToken：： GetTokenId](#gettokenid)|调用此方法以获取与`CAccessToken`对象关联的标记 ID。|
|[CAccessToken：： GetType](#gettype)|调用此方法以获取`CAccessToken`对象的标记类型。|
|[CAccessToken：： GetUser](#getuser)|调用此方法可标识与`CAccessToken`对象关联的用户。|
|[CAccessToken：： HKeyCurrentUser](#hkeycurrentuser)|调用此方法可获取指向与`CAccessToken`对象关联的用户配置文件的句柄。|
|[CAccessToken：：模拟](#impersonate)|调用此方法可为线程分配`CAccessToken`模拟。|
|[CAccessToken：： ImpersonateLoggedOnUser](#impersonateloggedonuser)|调用此方法以允许调用线程模拟已登录用户的安全上下文。|
|[CAccessToken：： IsTokenRestricted](#istokenrestricted)|调用此方法可测试`CAccessToken`对象是否包含受限 sid 的列表。|
|[CAccessToken：： Processmodel.loaduserprofile](#loaduserprofile)|调用此方法可加载与`CAccessToken`对象关联的用户配置文件。|
|[CAccessToken：： LogonUser](#logonuser)|调用此方法为与给定凭据关联的用户创建登录会话。|
|[CAccessToken：： OpenCOMClientToken](#opencomclienttoken)|从处理来自客户端的调用的`CAccessToken` com 服务器中调用此方法，以通过 com 客户端的访问令牌初始化。|
|[CAccessToken：： OpenNamedPipeClientToken](#opennamedpipeclienttoken)|从对命名管道发出请求的服务器中调用此方法，以`CAccessToken`使用来自客户端的访问令牌初始化。|
|[CAccessToken：： OpenRPCClientToken](#openrpcclienttoken)|从处理来自 RPC 客户端的调用的服务器中调用此方法，以便`CAccessToken`使用客户端的访问令牌初始化。|
|[CAccessToken：： OpenThreadToken](#openthreadtoken)|调用此方法以设置模拟级别，然后`CAccessToken`用来自给定线程的标记初始化。|
|[CAccessToken：:P rivilegeCheck](#privilegecheck)|调用此方法以确定是否在`CAccessToken`对象中启用了指定的权限集。|
|[CAccessToken：： Revert](#revert)|调用此方法可停止使用模拟标记的线程。|
|[CAccessToken：： SetDefaultDacl](#setdefaultdacl)|调用此方法可设置`CAccessToken`对象的默认 DACL。|
|[CAccessToken：： SetOwner](#setowner)|调用此方法可设置`CAccessToken`对象的所有者。|
|[CAccessToken：： SetPrimaryGroup](#setprimarygroup)|调用此方法可设置`CAccessToken`对象的主要组。|

## <a name="remarks"></a>备注

[访问令牌](/windows/win32/SecAuthZ/access-tokens)是一个对象，该对象描述进程或线程的安全上下文，并分配给登录到 Windows 系统的每个用户。

有关 Windows 中的访问控制模型的简介，请参阅 Windows SDK 中的[访问控制](/windows/win32/SecAuthZ/access-control)。

## <a name="requirements"></a>要求

**标头：** atlsecurity。h

## <a name="caccesstokenattach"></a><a name="attach"></a>CAccessToken：： Attach

调用此方法以获取给定访问令牌句柄的所有权。

```cpp
void Attach(HANDLE hToken) throw();
```

### <a name="parameters"></a>参数

*hToken*<br/>
访问令牌的句柄。

### <a name="remarks"></a>备注

在调试版本中，如果`CAccessToken`对象已具有访问令牌的所有权，则会发生断言错误。

## <a name="caccesstokencaccesstoken"></a><a name="dtor"></a>CAccessToken：： ~ CAccessToken

析构函数。

```cpp
virtual ~CAccessToken() throw();
```

### <a name="remarks"></a>备注

释放所有已分配的资源。

## <a name="caccesstokenchecktokenmembership"></a><a name="checktokenmembership"></a>CAccessToken：： CheckTokenMembership

调用此方法以确定是否在`CAccessToken`对象中启用了指定的 SID。

```cpp
bool CheckTokenMembership(
    const CSid& rSid,
    bool* pbIsMember) const throw(...);
```

### <a name="parameters"></a>参数

*rSid*<br/>
对[CSid 类](../../atl/reference/csid-class.md)对象的引用。

*pbIsMember*<br/>
指向接收检查结果的变量的指针。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

`CheckTokenMembership`方法检查访问令牌的用户和组 sid 中是否存在 SID。 如果 SID 存在并且具有 SE_GROUP_ENABLED 属性， *pbIsMember*将设置为 TRUE;否则，将其设置为 FALSE。

在调试版本中，如果*pbIsMember*不是有效的指针，则将发生断言错误。

> [!NOTE]
> `CAccessToken`对象必须为模拟标记，而不是主标记。

## <a name="caccesstokencreateimpersonationtoken"></a><a name="createimpersonationtoken"></a>CAccessToken：： CreateImpersonationToken

调用此方法可创建模拟访问令牌。

```cpp
bool CreateImpersonationToken(
    CAccessToken* pImp,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) const throw(...);
```

### <a name="parameters"></a>参数

*pImp*<br/>
指向新`CAccessToken`的对象的指针。

*sil*<br/>
指定一个[SECURITY_IMPERSONATION_LEVEL](/windows/win32/api/winnt/ne-winnt-security_impersonation_level)枚举类型，该类型提供新令牌的模拟级别。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

`CreateImpersonationToken`调用[DuplicateToken](/windows/win32/api/securitybaseapi/nf-securitybaseapi-duplicatetoken)创建新的模拟令牌。

## <a name="caccesstokencreateprimarytoken"></a><a name="createprimarytoken"></a>CAccessToken：： CreatePrimaryToken

调用此方法以创建新的主令牌。

```cpp
bool CreatePrimaryToken(
    CAccessToken* pPri,
    DWORD dwDesiredAccess = MAXIMUM_ALLOWED,
    const CSecurityAttributes* pTokenAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>参数

*pPri*<br/>
指向新`CAccessToken`的对象的指针。

*dwDesiredAccess*<br/>
为新令牌指定请求的访问权限。 默认情况下，MAXIMUM_ALLOWED 会请求对调用方有效的所有访问权限。 有关访问权限的详细信息，请参阅[访问权限和访问掩码](/windows/win32/SecAuthZ/access-rights-and-access-masks)。

*pTokenAttributes*<br/>
指向[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))结构的指针，该结构指定新令牌的安全描述符，并确定子进程是否可以继承令牌。 如果*pTokenAttributes*为 NULL，则令牌将获取默认安全描述符，并且无法继承句柄。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

`CreatePrimaryToken`调用[DuplicateTokenEx](/windows/win32/api/securitybaseapi/nf-securitybaseapi-duplicatetokenex)创建新的主令牌。

## <a name="caccesstokencreateprocessasuser"></a><a name="createprocessasuser"></a>CAccessToken：： CreateProcessAsUser

调用此方法可创建一个新进程，该进程在由`CAccessToken`对象表示的用户的安全上下文中运行。

```cpp
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
指向以 null 结尾的字符串的指针，该字符串指定要执行的模块。 此参数不能为 NULL。

*pCommandLine*<br/>
指向以 null 结尾的字符串的指针，该字符串指定要执行的命令行。

*pProcessInformation*<br/>
指向[PROCESS_INFORMATION 结构](/windows/win32/api/processthreadsapi/ns-processthreadsapi-process_information)的指针，该结构接收有关新进程的标识信息。

*pStartupInfo*<br/>
指向[STARTUPINFO](/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfow)结构的指针，该结构指定新进程的主窗口应如何显示。

*dwCreationFlags*<br/>
指定用于控制优先级类和进程创建的其他标志。 有关标志列表，请参阅 Win32 函数[CreateProcessAsUser](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessasuserw) 。

*bLoadProfile*<br/>
如果为 TRUE，则将通过[processmodel.loaduserprofile](/windows/win32/api/userenv/nf-userenv-loaduserprofilew)加载用户的配置文件。

*pProcessAttributes*<br/>
指向[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))结构的指针，该结构指定新进程的安全描述符，并确定子进程是否可以继承返回的句柄。 如果*pProcessAttributes*为 NULL，则进程将获取默认的安全描述符，并且无法继承句柄。

*pThreadAttributes*<br/>
指向[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))结构的指针，该结构指定新线程的安全说明符并确定子进程是否可以继承返回的句柄。 如果*pThreadAttributes*为 NULL，则线程将获取默认的安全描述符，并且无法继承句柄。

*bInherit*<br/>
指示新进程是否从调用进程继承句柄。 如果为 TRUE，则新进程将继承调用进程中的每个可继承的开放句柄。 继承句柄与原始句柄具有相同的值和访问权限。

*pCurrentDirectory*<br/>
指向以 null 结尾的字符串的指针，该字符串指定新进程的当前驱动器和目录。 该字符串必须是包含驱动器号的完整路径。 如果此参数为 NULL，则新进程将与调用进程具有相同的当前驱动器和目录。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

`CreateProcessAsUser`使用`CreateProcessAsUser` Win32 函数来创建一个新进程，该进程在由`CAccessToken`对象表示的用户的安全上下文中运行。 有关所需参数的完整讨论，请参阅[CreateProcessAsUser](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessasuserw)函数的说明。

要使此方法成功， `CAccessToken`对象必须包含 AssignPrimaryToken （除非它是受限标记）和 IncreaseQuota 特权。

## <a name="caccesstokencreaterestrictedtoken"></a><a name="createrestrictedtoken"></a>CAccessToken：： CreateRestrictedToken

调用此方法可创建一个新的受`CAccessToken`限制的对象。

```cpp
bool CreateRestrictedToken(
    CAccessToken* pRestrictedToken,
    const CTokenGroups& SidsToDisable,
    const CTokenGroups& SidsToRestrict,
    const CTokenPrivileges& PrivilegesToDelete = CTokenPrivileges()) const throw(...);
```

### <a name="parameters"></a>参数

*pRestrictedToken*<br/>
新的受限制`CAccessToken`的对象。

*SidsToDisable*<br/>
指定`CTokenGroups`仅拒绝 sid 的对象。

*SidsToRestrict*<br/>
一个`CTokenGroups`指定限制 sid 的对象。

*PrivilegesToDelete*<br/>
一个`CTokenPrivileges`对象，该对象指定要在受限制的令牌中删除的特权。 默认值创建一个空对象。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

`CreateRestrictedToken`使用[CreateRestrictedToken](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createrestrictedtoken) Win32 函数创建新`CAccessToken`的对象，并提供限制。

> [!IMPORTANT]
> 使用`CreateRestrictedToken`时，请确保以下各项：现有标记有效（并且不是由用户输入），且*SidsToDisable*和*PrivilegesToDelete*都是有效的（用户不会输入）。 如果该方法返回 FALSE，则拒绝功能。

## <a name="caccesstokendetach"></a><a name="detach"></a>CAccessToken：:D etach

调用此方法可撤消访问令牌的所有权。

```cpp
HANDLE Detach() throw();
```

### <a name="return-value"></a>返回值

返回已分离的的`CAccessToken`句柄。

### <a name="remarks"></a>备注

此方法吊销`CAccessToken`访问令牌的所有权。

## <a name="caccesstokendisableprivilege"></a><a name="disableprivilege"></a>CAccessToken：:D isablePrivilege

调用此方法可禁用`CAccessToken`对象中的权限。

```cpp
bool DisablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>参数

*pszPrivilege*<br/>
指向字符串的指针，该字符串包含要在`CAccessToken`对象中禁用的特权。

*pPreviousState*<br/>
指向`CTokenPrivileges`对象的指针，该对象将包含特权的以前的状态。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

## <a name="caccesstokendisableprivileges"></a><a name="disableprivileges"></a>CAccessToken：:D isablePrivileges

调用此方法可禁用对象中的`CAccessToken`一个或多个权限。

```cpp
bool DisablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>参数

*rPrivileges*<br/>
一个指针，指向包含要在`CAccessToken`对象中禁用的特权的字符串数组。

*pPreviousState*<br/>
指向`CTokenPrivileges`对象的指针，该对象将包含特权的以前的状态。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

## <a name="caccesstokenenableprivilege"></a><a name="enableprivilege"></a>CAccessToken：： EnablePrivilege

调用此方法可在`CAccessToken`对象中启用权限。

```cpp
bool EnablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>参数

*pszPrivilege*<br/>
指向字符串的指针，该字符串包含要在`CAccessToken`对象中启用的特权。

*pPreviousState*<br/>
指向`CTokenPrivileges`对象的指针，该对象将包含特权的以前的状态。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

## <a name="caccesstokenenableprivileges"></a><a name="enableprivileges"></a>CAccessToken：： EnablePrivileges

调用此方法以启用对象中的`CAccessToken`一个或多个权限。

```cpp
bool EnablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>参数

*rPrivileges*<br/>
一个指针，指向包含在`CAccessToken`对象中启用的特权的字符串数组。

*pPreviousState*<br/>
指向`CTokenPrivileges`对象的指针，该对象将包含特权的以前的状态。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

## <a name="caccesstokengetdefaultdacl"></a><a name="getdefaultdacl"></a>CAccessToken：： GetDefaultDacl

调用此方法以返回`CAccessToken`对象的默认 DACL。

```cpp
bool GetDefaultDacl(CDacl* pDacl) const throw(...);
```

### <a name="parameters"></a>参数

*pDacl*<br/>
指向将接收`CAccessToken`对象的默认 DACL 的[CDacl 类](../../atl/reference/cdacl-class.md)对象的指针。

### <a name="return-value"></a>返回值

如果已恢复默认 DACL，则返回 TRUE，否则返回 FALSE。

## <a name="caccesstokengeteffectivetoken"></a><a name="geteffectivetoken"></a>CAccessToken：： GetEffectiveToken

调用此方法可使`CAccessToken`对象等于当前线程的有效访问令牌。

```cpp
bool GetEffectiveToken(DWORD dwDesiredAccess) throw();
```

### <a name="parameters"></a>参数

*dwDesiredAccess*<br/>
指定一个访问掩码，该掩码指定对访问令牌发起访问的请求类型。 这些请求的访问类型与令牌的 DACL 比较来确定同意或拒绝哪些访问。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

## <a name="caccesstokengetgroups"></a><a name="getgroups"></a>CAccessToken：： Ldapauthentication.getgroups

调用此方法以返回`CAccessToken`对象的标记组。

```cpp
bool GetGroups(CTokenGroups* pGroups) const throw(...);
```

### <a name="parameters"></a>参数

*pGroups*<br/>
指向将接收组信息的[CTokenGroups 类](../../atl/reference/ctokengroups-class.md)对象的指针。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

## <a name="caccesstokengethandle"></a><a name="gethandle"></a>CAccessToken：： GetHandle

调用此方法以检索访问令牌的句柄。

```cpp
HANDLE GetHandle() const throw();
```

### <a name="return-value"></a>返回值

返回`CAccessToken`对象的访问令牌的句柄。

## <a name="caccesstokengetimpersonationlevel"></a><a name="getimpersonationlevel"></a>CAccessToken：： GetImpersonationLevel

调用此方法可从访问令牌中获取模拟级别。

```cpp
bool GetImpersonationLevel(
    SECURITY_IMPERSONATION_LEVEL* pImpersonationLevel) const throw(...);
```

### <a name="parameters"></a>参数

*pImpersonationLevel*<br/>
指向将接收模拟级别信息的[SECURITY_IMPERSONATION_LEVEL](/windows/win32/api/winnt/ne-winnt-security_impersonation_level)枚举类型的指针。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

## <a name="caccesstokengetlogonsessionid"></a><a name="getlogonsessionid"></a>CAccessToken：： GetLogonSessionId

调用此方法以获取与`CAccessToken`对象关联的登录会话 ID。

```cpp
bool GetLogonSessionId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>参数

*pluid*<br/>
指向将接收登录会话 ID 的[LUID](/windows/win32/api/winnt/ns-winnt-luid)的指针。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

在调试版本中，如果*pluid*是无效值，则将发生断言错误。

## <a name="caccesstokengetlogonsid"></a><a name="getlogonsid"></a>CAccessToken：： GetLogonSid

调用此方法以获取与`CAccessToken`对象关联的登录 SID。

```cpp
bool GetLogonSid(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>参数

*pSid*<br/>
指向[CSid 类](../../atl/reference/csid-class.md)对象的指针。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

在调试版本中，如果*pSid*是无效值，则将发生断言错误。

## <a name="caccesstokengetowner"></a><a name="getowner"></a>CAccessToken：： GetOwner

调用此方法以获取与`CAccessToken`对象关联的所有者。

```cpp
bool GetOwner(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>参数

*pSid*<br/>
指向[CSid 类](../../atl/reference/csid-class.md)对象的指针。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

默认情况下，在此访问令牌有效的任何对象上设置所有者。

## <a name="caccesstokengetprimarygroup"></a><a name="getprimarygroup"></a>CAccessToken：： GetPrimaryGroup

调用此方法以获取与`CAccessToken`对象关联的主要组。

```cpp
bool GetPrimaryGroup(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>参数

*pSid*<br/>
指向[CSid 类](../../atl/reference/csid-class.md)对象的指针。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

默认情况下，在此访问令牌有效的任何对象上设置组。

## <a name="caccesstokengetprivileges"></a><a name="getprivileges"></a>CAccessToken：： GetPrivileges

调用此方法以获取与`CAccessToken`对象关联的特权。

```cpp
bool GetPrivileges(CTokenPrivileges* pPrivileges) const throw(...);
```

### <a name="parameters"></a>参数

*pPrivileges*<br/>
指向将接收权限的[CTokenPrivileges 类](../../atl/reference/ctokenprivileges-class.md)对象的指针。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

## <a name="caccesstokengetprocesstoken"></a><a name="getprocesstoken"></a>CAccessToken：： GetProcessToken

调用此方法可使用给定进程中的访问令牌初始化 `CAccessToken`。

```cpp
bool GetProcessToken(DWORD dwDesiredAccess, HANDLE hProcess = NULL) throw();
```

### <a name="parameters"></a>参数

*dwDesiredAccess*<br/>
指定一个访问掩码，该掩码指定对访问令牌发起访问的请求类型。 这些请求的访问类型与令牌的 DACL 比较来确定同意或拒绝哪些访问。

*hProcess*<br/>
用于访问令牌已打开的进程的句柄。 如果使用默认值 NULL，则使用当前进程。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

调用[OpenProcessToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-openprocesstoken) Win32 函数。

## <a name="caccesstokengetprofile"></a><a name="getprofile"></a>CAccessToken：： GetProfile

调用此方法可获取指向与`CAccessToken`对象关联的用户配置文件的句柄。

```cpp
HANDLE GetProfile() const throw();
```

### <a name="return-value"></a>返回值

返回一个指向用户配置文件的句柄，如果不存在任何配置文件，则返回 NULL。

## <a name="caccesstokengetsource"></a><a name="getsource"></a>CAccessToken：： GetSource

调用此方法以获取`CAccessToken`对象的源。

```cpp
bool GetSource(TOKEN_SOURCE* pSource) const throw(...);
```

### <a name="parameters"></a>参数

*pSource*<br/>
指向[TOKEN_SOURCE](/windows/win32/api/winnt/ns-winnt-token_source)结构的指针。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

## <a name="caccesstokengetstatistics"></a><a name="getstatistics"></a>CAccessToken：： GetStatistics

调用此方法以获取与对象关联的`CAccessToken`信息。

```cpp
bool GetStatistics(TOKEN_STATISTICS* pStatistics) const throw(...);
```

### <a name="parameters"></a>参数

*pStatistics*<br/>
指向[TOKEN_STATISTICS](/windows/win32/api/winnt/ns-winnt-token_statistics)结构的指针。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

## <a name="caccesstokengetterminalservicessessionid"></a><a name="getterminalservicessessionid"></a>CAccessToken：： GetTerminalServicesSessionId

调用此方法以获取与`CAccessToken`对象关联的终端服务会话 ID。

```cpp
bool GetTerminalServicesSessionId(DWORD* pdwSessionId) const throw(...);
```

### <a name="parameters"></a>参数

*pdwSessionId*<br/>
终端服务会话 ID。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

## <a name="caccesstokengetthreadtoken"></a><a name="getthreadtoken"></a>CAccessToken：： GetThreadToken

调用此方法可`CAccessToken`通过给定线程中的标记初始化。

```cpp
bool GetThreadToken(
    DWORD dwDesiredAccess,
    HANDLE hThread = NULL,
    bool bOpenAsSelf = true) throw();
```

### <a name="parameters"></a>参数

*dwDesiredAccess*<br/>
指定一个访问掩码，该掩码指定对访问令牌发起访问的请求类型。 这些请求的访问类型与令牌的 DACL 比较来确定同意或拒绝哪些访问。

*hThread*<br/>
打开其访问令牌的线程的句柄。

*bOpenAsSelf*<br/>
指示是否对调用`GetThreadToken`方法的线程的安全上下文或针对调用线程的进程的安全上下文进行访问检查。

如果此参数为 FALSE，则使用调用线程的安全上下文来执行访问检查。 如果线程正在模拟客户端，则此安全上下文可以是客户端进程的安全上下文。 如果此参数为 TRUE，则使用调用线程的进程的安全上下文执行访问检查。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

## <a name="caccesstokengettokenid"></a><a name="gettokenid"></a>CAccessToken：： GetTokenId

调用此方法以获取与`CAccessToken`对象关联的标记 ID。

```cpp
bool GetTokenId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>参数

*pluid*<br/>
指向将接收令牌 ID 的[LUID](/windows/win32/api/winnt/ns-winnt-luid)的指针。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

## <a name="caccesstokengettype"></a><a name="gettype"></a>CAccessToken：： GetType

调用此方法以获取`CAccessToken`对象的标记类型。

```cpp
bool GetType(TOKEN_TYPE* pType) const throw(...);
```

### <a name="parameters"></a>参数

*pType*<br/>
成功接收令牌类型的[TOKEN_TYPE](/windows/win32/api/winnt/ne-winnt-token_type)变量的地址。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

TOKEN_TYPE 枚举类型包含区分主令牌和模拟令牌的值。

## <a name="caccesstokengetuser"></a><a name="getuser"></a>CAccessToken：： GetUser

调用此方法可标识与`CAccessToken`对象关联的用户。

```cpp
bool GetUser(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>参数

*pSid*<br/>
指向[CSid 类](../../atl/reference/csid-class.md)对象的指针。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

## <a name="caccesstokenhkeycurrentuser"></a><a name="hkeycurrentuser"></a>CAccessToken：： HKeyCurrentUser

调用此方法可获取指向与`CAccessToken`对象关联的用户配置文件的句柄。

```cpp
HKEY HKeyCurrentUser() const throw();
```

### <a name="return-value"></a>返回值

返回一个指向用户配置文件的句柄，如果不存在任何配置文件，则返回 NULL。

## <a name="caccesstokenimpersonate"></a><a name="impersonate"></a>CAccessToken：：模拟

调用此方法可为线程分配`CAccessToken`模拟。

```cpp
bool Impersonate(HANDLE hThread = NULL) const throw(...);
```

### <a name="parameters"></a>参数

*hThread*<br/>
要向其分配模拟标记的线程的句柄。 此句柄必须已使用 TOKEN_IMPERSONATE 访问权限打开。 如果*hThread*为 NULL，则该方法将导致线程使用模拟标记停止。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

在调试版本中，如果`CAccessToken`没有指向标记的有效指针，则将发生断言错误。

[CAutoRevertImpersonation 类](../../atl/reference/cautorevertimpersonation-class.md)可用于自动还原模拟的访问令牌。

## <a name="caccesstokenimpersonateloggedonuser"></a><a name="impersonateloggedonuser"></a>CAccessToken：： ImpersonateLoggedOnUser

调用此方法以允许调用线程模拟已登录用户的安全上下文。

```cpp
bool ImpersonateLoggedOnUser() const throw(...);
```

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

> [!IMPORTANT]
> 如果对模拟函数的调用由于任何原因而失败，则不会模拟该客户端，并且会在进行调用的进程的安全上下文中发出客户端请求。 如果该进程作为高特权帐户运行，或者作为管理组的成员运行，则该用户可能会无法执行该操作。 因此，应始终确认此函数的返回值。

## <a name="caccesstokenistokenrestricted"></a><a name="istokenrestricted"></a>CAccessToken：： IsTokenRestricted

调用此方法可测试`CAccessToken`对象是否包含受限 sid 的列表。

```cpp
bool IsTokenRestricted() const throw();
```

### <a name="return-value"></a>返回值

如果对象包含限制 Sid 的列表，则返回 TRUE; 如果没有限制 Sid，则返回 FALSE; 如果该方法失败，则返回 FALSE。

## <a name="caccesstokenloaduserprofile"></a><a name="loaduserprofile"></a>CAccessToken：： Processmodel.loaduserprofile

调用此方法可加载与`CAccessToken`对象关联的用户配置文件。

```cpp
bool LoadUserProfile() throw(...);
```

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

在调试版本中，如果`CAccessToken`不包含有效的标记，或用户配置文件已存在，则将发生断言错误。

## <a name="caccesstokenlogonuser"></a><a name="logonuser"></a>CAccessToken：： LogonUser

调用此方法为与给定凭据关联的用户创建登录会话。

```cpp
bool LogonUser(
    LPCTSTR pszUserName,
    LPCTSTR pszDomain,
    LPCTSTR pszPassword,
    DWORD dwLogonType = LOGON32_LOGON_INTERACTIVE,
    DWORD dwLogonProvider = LOGON32_PROVIDER_DEFAULT) throw();
```

### <a name="parameters"></a>参数

*pszUserName*<br/>
指向以 null 结尾的字符串的指针，该字符串指定用户名。 这是要登录到的用户帐户的名称。

*pszDomain*<br/>
指向以 null 结尾的字符串的指针，该字符串指定其帐户数据库包含*pszUserName*帐户的域或服务器的名称。

*pszPassword*<br/>
指向以 null 结尾的字符串的指针，该字符串指定由*pszUserName*指定的用户帐户的明文密码。

*dwLogonType*<br/>
指定要执行的登录操作的类型。 有关更多详细信息，请参阅[LogonUser](/windows/win32/api/winbase/nf-winbase-logonuserw) 。

*dwLogonProvider*<br/>
指定登录提供程序。 有关更多详细信息，请参阅[LogonUser](/windows/win32/api/winbase/nf-winbase-logonuserw) 。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

从登录生成的访问令牌将与相关联`CAccessToken`。 要使此方法成功， `CAccessToken`对象必须拥有 SE_TCB_NAME 权限，并将持有者标识为受信任的计算机基准的一部分。 有关所需权限的详细信息，请参阅[LogonUser](/windows/win32/api/winbase/nf-winbase-logonuserw) 。

## <a name="caccesstokenopencomclienttoken"></a><a name="opencomclienttoken"></a>CAccessToken：： OpenCOMClientToken

从处理来自客户端的调用的`CAccessToken` com 服务器中调用此方法，以通过 com 客户端的访问令牌初始化。

```cpp
bool OpenCOMClientToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>参数

*dwDesiredAccess*<br/>
指定一个访问掩码，该掩码指定对访问令牌发起访问的请求类型。 这些请求的访问类型与令牌的 DACL 比较来确定同意或拒绝哪些访问。

*bImpersonate*<br/>
如果为 TRUE，则如果此调用成功完成，则当前线程将模拟调用 COM 客户端。 如果为 FALSE，则访问令牌将打开，但当此调用完成时，该线程不具有模拟令牌。

*bOpenAsSelf*<br/>
指示是否要针对调用[GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread)方法的线程的安全上下文或针对调用线程的进程的安全上下文执行访问检查。

如果此参数为 FALSE，则使用调用线程的安全上下文来执行访问检查。 如果线程正在模拟客户端，则此安全上下文可以是客户端进程的安全上下文。 如果此参数为 TRUE，则使用调用线程的进程的安全上下文执行访问检查。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

[CAutoRevertImpersonation 类](../../atl/reference/cautorevertimpersonation-class.md)可用于通过将*bImpersonate*标志设置为 TRUE 来自动恢复所创建的模拟访问令牌。

## <a name="caccesstokenopennamedpipeclienttoken"></a><a name="opennamedpipeclienttoken"></a>CAccessToken：： OpenNamedPipeClientToken

从对命名管道发出请求的服务器中调用此方法，以`CAccessToken`使用来自客户端的访问令牌初始化。

```cpp
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
如果为 TRUE，则在此调用成功完成的情况下，当前线程将模拟调用管道客户端。 如果为 FALSE，则访问令牌将打开，但当此调用完成时，该线程不具有模拟令牌。

*bOpenAsSelf*<br/>
指示是否要针对调用[GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread)方法的线程的安全上下文或针对调用线程的进程的安全上下文执行访问检查。

如果此参数为 FALSE，则使用调用线程的安全上下文来执行访问检查。 如果线程正在模拟客户端，则此安全上下文可以是客户端进程的安全上下文。 如果此参数为 TRUE，则使用调用线程的进程的安全上下文执行访问检查。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

[CAutoRevertImpersonation 类](../../atl/reference/cautorevertimpersonation-class.md)可用于通过将*bImpersonate*标志设置为 TRUE 来自动恢复所创建的模拟访问令牌。

## <a name="caccesstokenopenrpcclienttoken"></a><a name="openrpcclienttoken"></a>CAccessToken：： OpenRPCClientToken

从处理来自 RPC 客户端的调用的服务器中调用此方法，以便`CAccessToken`使用客户端的访问令牌初始化。

```cpp
bool OpenRPCClientToken(
    RPC_BINDING_HANDLE BindingHandle,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>参数

*BindingHandle*<br/>
服务器上表示与客户端的绑定的绑定句柄。

*dwDesiredAccess*<br/>
指定一个访问掩码，该掩码指定对访问令牌发起访问的请求类型。 这些请求的访问类型与令牌的 DACL 比较来确定同意或拒绝哪些访问。

*bImpersonate*<br/>
如果为 TRUE，则当此调用成功完成时，当前线程将模拟调用 RPC 客户端。 如果为 FALSE，则访问令牌将打开，但当此调用完成时，该线程不具有模拟令牌。

*bOpenAsSelf*<br/>
指示是否要针对调用[GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread)方法的线程的安全上下文或针对调用线程的进程的安全上下文执行访问检查。

如果此参数为 FALSE，则使用调用线程的安全上下文来执行访问检查。 如果线程正在模拟客户端，则此安全上下文可以是客户端进程的安全上下文。 如果此参数为 TRUE，则使用调用线程的进程的安全上下文执行访问检查。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

[CAutoRevertImpersonation 类](../../atl/reference/cautorevertimpersonation-class.md)可用于通过将*bImpersonate*标志设置为 TRUE 来自动恢复所创建的模拟访问令牌。

## <a name="caccesstokenopenthreadtoken"></a><a name="openthreadtoken"></a>CAccessToken：： OpenThreadToken

调用此方法以设置模拟级别，然后`CAccessToken`用来自给定线程的标记初始化。

```cpp
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
如果为 TRUE，则在此方法完成后，线程将保留所请求的模拟级别。 如果为 FALSE，则线程将恢复为其原始模拟级别。

*bOpenAsSelf*<br/>
指示是否要针对调用[GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread)方法的线程的安全上下文或针对调用线程的进程的安全上下文执行访问检查。

如果此参数为 FALSE，则使用调用线程的安全上下文来执行访问检查。 如果线程正在模拟客户端，则此安全上下文可以是客户端进程的安全上下文。 如果此参数为 TRUE，则使用调用线程的进程的安全上下文执行访问检查。

*sil*<br/>
指定一个[SECURITY_IMPERSONATION_LEVEL](/windows/win32/api/winnt/ne-winnt-security_impersonation_level)枚举类型，该类型提供标记的模拟级别。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

`OpenThreadToken`类似于[CAccessToken：： GetThreadToken](#getthreadtoken)，但在`CAccessToken`通过线程的访问令牌初始化之前设置模拟级别。

[CAutoRevertImpersonation 类](../../atl/reference/cautorevertimpersonation-class.md)可用于通过将*bImpersonate*标志设置为 TRUE 来自动恢复所创建的模拟访问令牌。

## <a name="caccesstokenprivilegecheck"></a><a name="privilegecheck"></a>CAccessToken：:P rivilegeCheck

调用此方法以确定是否在`CAccessToken`对象中启用了指定的权限集。

```cpp
bool PrivilegeCheck(
    PPRIVILEGE_SET RequiredPrivileges,
    bool* pbResult) const throw();
```

### <a name="parameters"></a>参数

*RequiredPrivileges*<br/>
指向[PRIVILEGE_SET](/windows/win32/api/winnt/ns-winnt-privilege_set)结构的指针。

*pbResult*<br/>
指向一个值的指针，该方法将设置，以指示是否在`CAccessToken`对象中启用了任何或所有指定的权限。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

返回`PrivilegeCheck`时，如果`Attributes`启用了相应的权限，则每个[LUID_AND_ATTRIBUTES](/windows/win32/api/winnt/ns-winnt-luid_and_attributes)结构的成员将设置为 SE_PRIVILEGE_USED_FOR_ACCESS。 此方法调用[PrivilegeCheck](/windows/win32/api/securitybaseapi/nf-securitybaseapi-privilegecheck) Win32 函数。

## <a name="caccesstokenrevert"></a><a name="revert"></a>CAccessToken：： Revert

调用此方法可阻止线程使用模拟标记。

```cpp
bool Revert(HANDLE hThread = NULL) const throw();
```

### <a name="parameters"></a>参数

*hThread*<br/>
要从模拟恢复的线程的句柄。 如果*hThread*为 NULL，则假定当前线程。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

可以通过[CAutoRevertImpersonation 类](../../atl/reference/cautorevertimpersonation-class.md)自动执行模拟令牌的重新确定。

## <a name="caccesstokensetdefaultdacl"></a><a name="setdefaultdacl"></a>CAccessToken：： SetDefaultDacl

调用此方法可设置`CAccessToken`对象的默认 DACL。

```cpp
bool SetDefaultDacl(const CDacl& rDacl) throw(...);
```

### <a name="parameters"></a>参数

*rDacl*<br/>
新的默认[CDacl 类](../../atl/reference/cdacl-class.md)信息。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

默认 DACL 是在使用此访问令牌有效创建新对象时默认使用的 DACL。

## <a name="caccesstokensetowner"></a><a name="setowner"></a>CAccessToken：： SetOwner

调用此方法可设置`CAccessToken`对象的所有者。

```cpp
bool SetOwner(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>参数

*rSid*<br/>
包含所有者信息的[CSid 类](../../atl/reference/csid-class.md)对象。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

所有者是在此访问令牌生效时用于创建的新对象的默认所有者。

## <a name="caccesstokensetprimarygroup"></a><a name="setprimarygroup"></a>CAccessToken：： SetPrimaryGroup

调用此方法可设置`CAccessToken`对象的主要组。

```cpp
bool SetPrimaryGroup(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>参数

*rSid*<br/>
包含主要组信息的[CSid 类](../../atl/reference/csid-class.md)对象。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

主组是在此访问令牌有效的情况下创建的新对象的默认组。

## <a name="see-also"></a>另请参阅

[Atlsecurity.h 示例](../../overview/visual-cpp-samples.md)<br/>
[访问令牌](/windows/win32/SecAuthZ/access-tokens)<br/>
[类概述](../../atl/atl-class-overview.md)
