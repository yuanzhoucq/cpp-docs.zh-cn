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
ms.openlocfilehash: f7a2ee2f9d633c1ed743621eec5b2f7cc04c0e0b
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748825"
---
# <a name="caccesstoken-class"></a>CAccessToken 类

此类是访问令牌的包装器。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
class CAccessToken
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CAccessToken：：*CAccessToken](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CAccessToken：：附加](#attach)|调用此方法以取得给定访问令牌句柄的所有权。|
|[CAccessToken：：检查令牌成员资格](#checktokenmembership)|调用此方法以确定`CAccessToken`对象中是否启用了指定的 SID。|
|[CAccessToken：：创建模拟令牌](#createimpersonationtoken)|调用此方法以创建新的模拟访问令牌。|
|[CAccessToken：：创建主要令牌](#createprimarytoken)|调用此方法以创建新的主令牌。|
|[CAccessToken：：创建进程用户](#createprocessasuser)|调用此方法以创建在`CAccessToken`对象表示的用户的安全上下文中运行的新进程。|
|[CAccessToken：：创建受限令牌](#createrestrictedtoken)|调用此方法以创建新的受限`CAccessToken`对象。|
|[CAccessToken：:Detach](#detach)|调用此方法以撤消访问令牌的所有权。|
|[CAccessToken：:D可特权](#disableprivilege)|调用此方法以禁用对象中`CAccessToken`的特权。|
|[CAccessToken：:D可特权](#disableprivileges)|调用此方法以禁用`CAccessToken`对象中的一个或多个权限。|
|[CAccessToken：：启用特权](#enableprivilege)|调用此方法以在`CAccessToken`对象中启用权限。|
|[CAccessToken：：启用特权](#enableprivileges)|调用此方法以启用对象中的`CAccessToken`一个或多个权限。|
|[CAccessToken：获取默认Dacl](#getdefaultdacl)|调用此方法以返回`CAccessToken`对象的默认 DACL。|
|[CAccessToken：获取有效令牌](#geteffectivetoken)|调用此方法以获取等于当前`CAccessToken`线程有效的访问令牌的对象。|
|[CAccessToken：获取群组](#getgroups)|调用此方法以返回`CAccessToken`对象的令牌组。|
|[CAccessToken：获取句柄](#gethandle)|调用此方法以检索访问令牌的句柄。|
|[CAccessToken：获取模拟级别](#getimpersonationlevel)|调用此方法从访问令牌获取模拟级别。|
|[CAccessToken：获取登录会话 Id](#getlogonsessionid)|调用此方法以获取与`CAccessToken`对象关联的登录会话 ID。|
|[CAccessToken：获取登录 Sid](#getlogonsid)|调用此方法以获取与`CAccessToken`对象关联的登录 SID。|
|[CAccessToken：获取所有者](#getowner)|调用此方法以获取与`CAccessToken`对象关联的所有者。|
|[CAccessToken：获取主要组](#getprimarygroup)|调用此方法获取与`CAccessToken`对象关联的主组。|
|[CAccessToken：获取特权](#getprivileges)|调用此方法获取与`CAccessToken`对象关联的权限。|
|[CAccessToken：：获取进程令牌](#getprocesstoken)|调用此方法可使用给定进程中的访问令牌初始化 `CAccessToken`。|
|[CAccessToken：获取配置文件](#getprofile)|调用此方法以获取指向与对象关联的用户配置文件的`CAccessToken`句柄。|
|[CAccessToken：获取来源](#getsource)|调用此方法以获取`CAccessToken`对象的源。|
|[CAccessToken：获取统计信息](#getstatistics)|调用此方法以获取有关`CAccessToken`对象的信息。|
|[CAccessToken：：获取终端服务会话Id](#getterminalservicessessionid)|调用此方法获取与`CAccessToken`对象关联的终端服务会话 ID。|
|[CAccessToken：获取线程令牌](#getthreadtoken)|调用此方法以使用给定线程中的`CAccessToken`令牌初始化 。|
|[CAccessToken：：获取令牌 ID](#gettokenid)|调用此方法以获取与`CAccessToken`对象关联的令牌 ID。|
|[CAccessToken：获取类型](#gettype)|调用此方法以获取`CAccessToken`对象的令牌类型。|
|[CAccessToken：获取用户](#getuser)|调用此方法以标识与`CAccessToken`对象关联的用户。|
|[CAccessToken：：HKeycurrentUser](#hkeycurrentuser)|调用此方法以获取指向与对象关联的用户配置文件的`CAccessToken`句柄。|
|[CAccessToken：模拟](#impersonate)|调用此方法以将模拟`CAccessToken`分配给线程。|
|[CAccessToken：：模拟登录用户](#impersonateloggedonuser)|调用此方法以允许调用线程模拟登录用户的安全上下文。|
|[CAccessToken：：受限制](#istokenrestricted)|调用此方法以测试`CAccessToken`对象是否包含受限 S 的清单。|
|[CAccessToken：：加载用户配置文件](#loaduserprofile)|调用此方法以加载与`CAccessToken`对象关联的用户配置文件。|
|[CAccessToken：：登录用户](#logonuser)|调用此方法为与给定凭据关联的用户创建登录会话。|
|[CAccessToken：：打开COM客户端令牌](#opencomclienttoken)|从处理来自客户端的呼叫的 COM 服务器内调用此方法，以便`CAccessToken`使用 COM 客户端的访问令牌初始化 。|
|[CAccessToken：：打开命名管道客户端令牌](#opennamedpipeclienttoken)|从服务器内调用此方法，通过命名管道获取请求，以便使用客户端的访问令牌`CAccessToken`初始化 。|
|[CAccessToken：：打开RPC客户端令牌](#openrpcclienttoken)|从服务器内调用此方法，以处理来自 RPC 客户端的调用，以便`CAccessToken`使用客户端的访问令牌初始化 。|
|[CAccessToken：：打开线程令牌](#openthreadtoken)|调用此方法以设置模拟级别，然后使用给定线程中的令牌初始化`CAccessToken`。|
|[CAccessToken：:P里维莱格检查](#privilegecheck)|调用此方法以确定对象中`CAccessToken`是否启用了指定的权限集。|
|[CAccessToken：：恢复](#revert)|调用此方法以阻止使用模拟令牌的线程。|
|[CAccessToken：：设置默认Dacl](#setdefaultdacl)|调用此方法以设置`CAccessToken`对象的默认 DACL。|
|[CAccessToken：：SetOwner](#setowner)|调用此方法以设置`CAccessToken`对象的所有者。|
|[CAccessToken：：设置主要组](#setprimarygroup)|调用此方法以设置`CAccessToken`对象的主组。|

## <a name="remarks"></a>备注

[访问令牌](/windows/win32/SecAuthZ/access-tokens)是描述进程或线程的安全上下文并分配给登录到 Windows 系统的每个用户的对象。

有关 Windows 中访问控制模型的简介，请参阅 Windows SDK 中[的访问控制](/windows/win32/SecAuthZ/access-control)。

## <a name="requirements"></a>要求

**标题：** atlsecurity.h

## <a name="caccesstokenattach"></a><a name="attach"></a>CAccessToken：：附加

调用此方法以取得给定访问令牌句柄的所有权。

```cpp
void Attach(HANDLE hToken) throw();
```

### <a name="parameters"></a>参数

*hToken*<br/>
访问令牌的句柄。

### <a name="remarks"></a>备注

在调试生成中，如果对象已拥有访问令牌`CAccessToken`的所有权，则会发生断言错误。

## <a name="caccesstokencaccesstoken"></a><a name="dtor"></a>CAccessToken：：*CAccessToken

析构函数。

```
virtual ~CAccessToken() throw();
```

### <a name="remarks"></a>备注

释放所有分配的资源。

## <a name="caccesstokenchecktokenmembership"></a><a name="checktokenmembership"></a>CAccessToken：：检查令牌成员资格

调用此方法以确定`CAccessToken`对象中是否启用了指定的 SID。

```
bool CheckTokenMembership(
    const CSid& rSid,
    bool* pbIsMember) const throw(...);
```

### <a name="parameters"></a>参数

*rSid*<br/>
对[CSid 类](../../atl/reference/csid-class.md)对象的引用。

*pbIs成员*<br/>
指向接收检查结果的变量的指针。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

该方法`CheckTokenMembership`检查访问令牌的用户和组 SID 中是否存在 SID。 如果 SID 存在并且具有SE_GROUP_ENABLED属性，*则 pbIs成员*设置为 TRUE;如果 SID 具有 SE_GROUP_ENABLED属性，则 pbIs会员将设置为 TRUE;否则，它将设置为 FALSE。

在调试生成中，如果*pbIs会员*不是有效的指针，则会发生断言错误。

> [!NOTE]
> 该`CAccessToken`对象必须是模拟令牌，而不是主令牌。

## <a name="caccesstokencreateimpersonationtoken"></a><a name="createimpersonationtoken"></a>CAccessToken：：创建模拟令牌

调用此方法以创建模拟访问令牌。

```
bool CreateImpersonationToken(
    CAccessToken* pImp,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) const throw(...);
```

### <a name="parameters"></a>参数

*皮条 客*<br/>
指向新`CAccessToken`对象的指针。

*Sil*<br/>
指定提供新令牌的模拟级别的[SECURITY_IMPERSONATION_LEVEL](/windows/win32/api/winnt/ne-winnt-security_impersonation_level)枚举类型。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

`CreateImpersonationToken`调用[重复令牌](/windows/win32/api/securitybaseapi/nf-securitybaseapi-duplicatetoken)以创建新的模拟令牌。

## <a name="caccesstokencreateprimarytoken"></a><a name="createprimarytoken"></a>CAccessToken：：创建主要令牌

调用此方法以创建新的主令牌。

```
bool CreatePrimaryToken(
    CAccessToken* pPri,
    DWORD dwDesiredAccess = MAXIMUM_ALLOWED,
    const CSecurityAttributes* pTokenAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>参数

*pPri*<br/>
指向新`CAccessToken`对象的指针。

*dwddAccess*<br/>
指定新令牌的请求访问权限。 默认的 MAXIMUM_ALLOWED 请求对调用方有效的所有访问权限。 有关访问权限的更多，请参阅[访问权限和访问掩码](/windows/win32/SecAuthZ/access-rights-and-access-masks)。

*pToken属性*<br/>
指向[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))结构的指针，该结构指定新令牌的安全描述符，并确定子进程是否可以继承令牌。 如果*pTokenAttributes*为 NULL，则令牌获取默认安全描述符，并且无法继承句柄。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

`CreatePrimaryToken`调用[重复令牌Ex](/windows/win32/api/securitybaseapi/nf-securitybaseapi-duplicatetokenex)创建新的主令牌。

## <a name="caccesstokencreateprocessasuser"></a><a name="createprocessasuser"></a>CAccessToken：：创建进程用户

调用此方法以创建在`CAccessToken`对象表示的用户的安全上下文中运行的新进程。

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

*p 应用程序名称*<br/>
指向指定要执行的模块的 null 终止字符串的指针。 此参数可能不是 NULL。

*pCommandLine*<br/>
指向指定要执行的命令行的 null 终止字符串的指针。

*p进程信息*<br/>
指向接收有关新进程的标识信息[的PROCESS_INFORMATION结构](/windows/win32/api/processthreadsapi/ns-processthreadsapi-process_information)的指针。

*pStartup信息*<br/>
指向[STARTUPINFO](/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfow)结构的指针，该结构指定新进程的主窗口的显示方式。

*dw创造标志*<br/>
指定控制优先级类和进程创建的其他标志。 有关标志列表，请参阅 Win32 函数["创建进程AsUser"。](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessasuserw)

*bLoad配置文件*<br/>
如果为 TRUE，则用户的配置文件将加载[LoadUserProfile](/windows/win32/api/userenv/nf-userenv-loaduserprofilew)。

*p进程属性*<br/>
指向[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))结构的指针，该结构指定新进程的安全描述符，并确定子进程是否可以继承返回的句柄。 如果*pProcessAttributes*为 NULL，则进程将获取默认安全描述符，并且无法继承句柄。

*pThread属性*<br/>
指向[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))结构的指针，该结构指定新线程的安全描述符，并确定子进程是否可以继承返回的句柄。 如果*pThreadAttributes*为 NULL，则线程将获取默认安全描述符，并且无法继承句柄。

*b继承*<br/>
指示新进程是否从调用进程继承句柄。 如果为 TRUE，则调用进程中的每个可继承打开句柄都由新进程继承。 继承的句柄具有与原始句柄相同的值和访问权限。

*pCurrentDirectory*<br/>
指向 null 端接字符串的指针，该字符串指定新进程的当前驱动器和目录。 字符串必须是包含驱动器号的完整路径。 如果此参数为 NULL，则新进程将具有与调用进程相同的当前驱动器和目录。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

`CreateProcessAsUser`使用`CreateProcessAsUser`Win32 函数创建在`CAccessToken`对象表示的用户的安全上下文中运行的新进程。 有关所需参数的完整讨论，请参阅[CreateProcessAsUser 函数](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessasuserw)的说明。

要使此方法成功，`CAccessToken`对象必须保留 AssignPrimaryToken（除非它是受限令牌）和"增加配额"权限。

## <a name="caccesstokencreaterestrictedtoken"></a><a name="createrestrictedtoken"></a>CAccessToken：：创建受限令牌

调用此方法以创建新的受限`CAccessToken`对象。

```
bool CreateRestrictedToken(
    CAccessToken* pRestrictedToken,
    const CTokenGroups& SidsToDisable,
    const CTokenGroups& SidsToRestrict,
    const CTokenPrivileges& PrivilegesToDelete = CTokenPrivileges()) const throw(...);
```

### <a name="parameters"></a>参数

*p受限令牌*<br/>
新的受限`CAccessToken`对象。

*Sidsto 禁用*<br/>
指定`CTokenGroups`仅拒绝 S 的对象。

*Sidsto 限制*<br/>
`CTokenGroups`指定限制 S 的对象。

*要删除的权限*<br/>
指定`CTokenPrivileges`在受限令牌中删除的权限的对象。 默认值创建一个空对象。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

`CreateRestrictedToken`使用[Create 限制令牌](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createrestrictedtoken)Win32 函数创建`CAccessToken`具有限制的新对象。

> [!IMPORTANT]
> 使用`CreateRestrictedToken`时，请确保以下内容：现有令牌有效（用户未输入）和*SidsTo 禁用*和*特权删除*都有效（并且用户不输入）。 如果该方法返回 FALSE，则拒绝功能。

## <a name="caccesstokendetach"></a><a name="detach"></a>CAccessToken：:Detach

调用此方法以撤消访问令牌的所有权。

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>返回值

将句柄返回到已分离`CAccessToken`的 句柄。

### <a name="remarks"></a>备注

此方法撤消`CAccessToken`访问令牌的所有权。

## <a name="caccesstokendisableprivilege"></a><a name="disableprivilege"></a>CAccessToken：:D可特权

调用此方法以禁用对象中`CAccessToken`的特权。

```
bool DisablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>参数

*psz特权*<br/>
指向包含要在对象中禁用的权限的字符串的`CAccessToken`指针。

*p 上一个状态*<br/>
指向将包含`CTokenPrivileges`权限的上一个状态的对象的指针。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

## <a name="caccesstokendisableprivileges"></a><a name="disableprivileges"></a>CAccessToken：:D可特权

调用此方法以禁用`CAccessToken`对象中的一个或多个权限。

```
bool DisablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>参数

*r特权*<br/>
指向包含要在`CAccessToken`对象中禁用的权限的字符串数组的指针。

*p 上一个状态*<br/>
指向将包含`CTokenPrivileges`权限的上一个状态的对象的指针。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

## <a name="caccesstokenenableprivilege"></a><a name="enableprivilege"></a>CAccessToken：：启用特权

调用此方法以在`CAccessToken`对象中启用权限。

```
bool EnablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>参数

*psz特权*<br/>
指向包含要在对象中启用的权限的`CAccessToken`字符串的指针。

*p 上一个状态*<br/>
指向将包含`CTokenPrivileges`权限的上一个状态的对象的指针。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

## <a name="caccesstokenenableprivileges"></a><a name="enableprivileges"></a>CAccessToken：：启用特权

调用此方法以启用对象中的`CAccessToken`一个或多个权限。

```
bool EnablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>参数

*r特权*<br/>
指向包含要在`CAccessToken`对象中启用的权限的字符串数组。

*p 上一个状态*<br/>
指向将包含`CTokenPrivileges`权限的上一个状态的对象的指针。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

## <a name="caccesstokengetdefaultdacl"></a><a name="getdefaultdacl"></a>CAccessToken：获取默认Dacl

调用此方法以返回`CAccessToken`对象的默认 DACL。

```
bool GetDefaultDacl(CDacl* pDacl) const throw(...);
```

### <a name="parameters"></a>参数

*pDacl*<br/>
指向[CDacl 类](../../atl/reference/cdacl-class.md)对象的指针，`CAccessToken`该对象将接收对象的默认 DACL。

### <a name="return-value"></a>返回值

如果默认 DACL 已恢复，则返回 TRUE，否则返回 FALSE。

## <a name="caccesstokengeteffectivetoken"></a><a name="geteffectivetoken"></a>CAccessToken：获取有效令牌

调用此方法以获取等于当前`CAccessToken`线程有效的访问令牌的对象。

```
bool GetEffectiveToken(DWORD dwDesiredAccess) throw();
```

### <a name="parameters"></a>参数

*dwddAccess*<br/>
指定一个访问掩码，该掩码指定对访问令牌发起访问的请求类型。 这些请求的访问类型与令牌的 DACL 比较来确定同意或拒绝哪些访问。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

## <a name="caccesstokengetgroups"></a><a name="getgroups"></a>CAccessToken：获取群组

调用此方法以返回`CAccessToken`对象的令牌组。

```
bool GetGroups(CTokenGroups* pGroups) const throw(...);
```

### <a name="parameters"></a>参数

*p组*<br/>
指向将接收组信息的[CTokenGroup 类](../../atl/reference/ctokengroups-class.md)对象。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

## <a name="caccesstokengethandle"></a><a name="gethandle"></a>CAccessToken：获取句柄

调用此方法以检索访问令牌的句柄。

```
HANDLE GetHandle() const throw();
```

### <a name="return-value"></a>返回值

返回对象访问令牌的`CAccessToken`句柄。

## <a name="caccesstokengetimpersonationlevel"></a><a name="getimpersonationlevel"></a>CAccessToken：获取模拟级别

调用此方法从访问令牌获取模拟级别。

```
bool GetImpersonationLevel(
    SECURITY_IMPERSONATION_LEVEL* pImpersonationLevel) const throw(...);
```

### <a name="parameters"></a>参数

*p 模拟级别*<br/>
指向[SECURITY_IMPERSONATION_LEVEL](/windows/win32/api/winnt/ne-winnt-security_impersonation_level)枚举类型的指针，该类型将接收模拟级别信息。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

## <a name="caccesstokengetlogonsessionid"></a><a name="getlogonsessionid"></a>CAccessToken：获取登录会话 Id

调用此方法以获取与`CAccessToken`对象关联的登录会话 ID。

```
bool GetLogonSessionId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>参数

*普卢伊德*<br/>
指向将接收登录会话 ID 的[LUID](/windows/win32/api/winnt/ns-winnt-luid)的指针。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

在调试生成中，如果*pluid*是无效值，则会发生断言错误。

## <a name="caccesstokengetlogonsid"></a><a name="getlogonsid"></a>CAccessToken：获取登录 Sid

调用此方法以获取与`CAccessToken`对象关联的登录 SID。

```
bool GetLogonSid(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>参数

*pSid*<br/>
指向[CSid 类](../../atl/reference/csid-class.md)对象的指针。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

在调试生成中，如果*pSid*是无效值，则会发生断言错误。

## <a name="caccesstokengetowner"></a><a name="getowner"></a>CAccessToken：获取所有者

调用此方法以获取与`CAccessToken`对象关联的所有者。

```
bool GetOwner(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>参数

*pSid*<br/>
指向[CSid 类](../../atl/reference/csid-class.md)对象的指针。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

默认情况下，将在此访问令牌生效时创建的任何对象上设置所有者。

## <a name="caccesstokengetprimarygroup"></a><a name="getprimarygroup"></a>CAccessToken：获取主要组

调用此方法获取与`CAccessToken`对象关联的主组。

```
bool GetPrimaryGroup(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>参数

*pSid*<br/>
指向[CSid 类](../../atl/reference/csid-class.md)对象的指针。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

默认情况下，该组将设置在此访问令牌生效时创建的任何对象上。

## <a name="caccesstokengetprivileges"></a><a name="getprivileges"></a>CAccessToken：获取特权

调用此方法获取与`CAccessToken`对象关联的权限。

```
bool GetPrivileges(CTokenPrivileges* pPrivileges) const throw(...);
```

### <a name="parameters"></a>参数

*p特权*<br/>
指向将收到特权[的 CToken 特权类](../../atl/reference/ctokenprivileges-class.md)对象。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

## <a name="caccesstokengetprocesstoken"></a><a name="getprocesstoken"></a>CAccessToken：：获取进程令牌

调用此方法可使用给定进程中的访问令牌初始化 `CAccessToken`。

```
bool GetProcessToken(DWORD dwDesiredAccess, HANDLE hProcess = NULL) throw();
```

### <a name="parameters"></a>参数

*dwddAccess*<br/>
指定一个访问掩码，该掩码指定对访问令牌发起访问的请求类型。 这些请求的访问类型与令牌的 DACL 比较来确定同意或拒绝哪些访问。

*h进程*<br/>
用于访问令牌已打开的进程的句柄。 如果使用 NULL 的默认值，则使用当前过程。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

调用[OpenProcessToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-openprocesstoken) Win32 功能。

## <a name="caccesstokengetprofile"></a><a name="getprofile"></a>CAccessToken：获取配置文件

调用此方法以获取指向与对象关联的用户配置文件的`CAccessToken`句柄。

```
HANDLE GetProfile() const throw();
```

### <a name="return-value"></a>返回值

返回指向用户配置文件的句柄，如果不存在配置文件，则返回 NULL。

## <a name="caccesstokengetsource"></a><a name="getsource"></a>CAccessToken：获取来源

调用此方法以获取`CAccessToken`对象的源。

```
bool GetSource(TOKEN_SOURCE* pSource) const throw(...);
```

### <a name="parameters"></a>参数

*p来源*<br/>
指向[TOKEN_SOURCE](/windows/win32/api/winnt/ns-winnt-token_source)结构的指针。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

## <a name="caccesstokengetstatistics"></a><a name="getstatistics"></a>CAccessToken：获取统计信息

调用此方法以获取有关`CAccessToken`对象的信息。

```
bool GetStatistics(TOKEN_STATISTICS* pStatistics) const throw(...);
```

### <a name="parameters"></a>参数

*p统计*<br/>
指向[TOKEN_STATISTICS](/windows/win32/api/winnt/ns-winnt-token_statistics)结构的指针。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

## <a name="caccesstokengetterminalservicessessionid"></a><a name="getterminalservicessessionid"></a>CAccessToken：：获取终端服务会话Id

调用此方法获取与`CAccessToken`对象关联的终端服务会话 ID。

```
bool GetTerminalServicesSessionId(DWORD* pdwSessionId) const throw(...);
```

### <a name="parameters"></a>参数

*pdwSessionId*<br/>
终端服务会话 ID。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

## <a name="caccesstokengetthreadtoken"></a><a name="getthreadtoken"></a>CAccessToken：获取线程令牌

调用此方法以使用给定线程中的`CAccessToken`令牌初始化 。

```
bool GetThreadToken(
    DWORD dwDesiredAccess,
    HANDLE hThread = NULL,
    bool bOpenAsSelf = true) throw();
```

### <a name="parameters"></a>参数

*dwddAccess*<br/>
指定一个访问掩码，该掩码指定对访问令牌发起访问的请求类型。 这些请求的访问类型与令牌的 DACL 比较来确定同意或拒绝哪些访问。

*hThread*<br/>
处理其访问令牌打开的线程。

*bOpenAsSelf*<br/>
指示是针对调用`GetThreadToken`方法的线程的安全上下文或调用线程的进程的安全上下文进行访问检查。

如果此参数为 FALSE，则使用调用线程的安全上下文执行访问检查。 如果线程正在模拟客户端，则此安全上下文可以是客户端进程的安全上下文。 如果此参数为 TRUE，则使用调用线程的进程的安全上下文进行访问检查。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

## <a name="caccesstokengettokenid"></a><a name="gettokenid"></a>CAccessToken：：获取令牌 ID

调用此方法以获取与`CAccessToken`对象关联的令牌 ID。

```
bool GetTokenId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>参数

*普卢伊德*<br/>
指向将接收令牌 ID 的[LUID](/windows/win32/api/winnt/ns-winnt-luid)的指针。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

## <a name="caccesstokengettype"></a><a name="gettype"></a>CAccessToken：获取类型

调用此方法以获取`CAccessToken`对象的令牌类型。

```
bool GetType(TOKEN_TYPE* pType) const throw(...);
```

### <a name="parameters"></a>参数

*p类型*<br/>
[TOKEN_TYPE](/windows/win32/api/winnt/ne-winnt-token_type)变量的地址，在成功时，该变量接收令牌的类型。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

TOKEN_TYPE枚举类型包含区分主令牌和模拟令牌的值。

## <a name="caccesstokengetuser"></a><a name="getuser"></a>CAccessToken：获取用户

调用此方法以标识与`CAccessToken`对象关联的用户。

```
bool GetUser(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>参数

*pSid*<br/>
指向[CSid 类](../../atl/reference/csid-class.md)对象的指针。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

## <a name="caccesstokenhkeycurrentuser"></a><a name="hkeycurrentuser"></a>CAccessToken：：HKeycurrentUser

调用此方法以获取指向与对象关联的用户配置文件的`CAccessToken`句柄。

```
HKEY HKeyCurrentUser() const throw();
```

### <a name="return-value"></a>返回值

返回指向用户配置文件的句柄，如果不存在配置文件，则返回 NULL。

## <a name="caccesstokenimpersonate"></a><a name="impersonate"></a>CAccessToken：模拟

调用此方法以将模拟`CAccessToken`分配给线程。

```
bool Impersonate(HANDLE hThread = NULL) const throw(...);
```

### <a name="parameters"></a>参数

*hThread*<br/>
句柄到线程以将模拟令牌分配给 。 此句柄必须已打开，具有TOKEN_IMPERSONATE访问权限。 如果*hThread*为 NULL，则该方法会导致线程停止使用模拟令牌。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

在调试生成中，如果没有`CAccessToken`指向令牌的有效指针，将发生断言错误。

[CAuto 还原模拟类](../../atl/reference/cautorevertimpersonation-class.md)可用于自动还原模拟访问令牌。

## <a name="caccesstokenimpersonateloggedonuser"></a><a name="impersonateloggedonuser"></a>CAccessToken：：模拟登录用户

调用此方法以允许调用线程模拟登录用户的安全上下文。

```
bool ImpersonateLoggedOnUser() const throw(...);
```

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

> [!IMPORTANT]
> 如果对模拟函数的调用由于任何原因失败，则客户端不会模拟，并且客户端请求是在发出调用的进程的安全上下文中进行的。 如果进程以高度特权帐户或管理组的成员运行，则用户可能能够执行否则将不允许执行的操作。 因此，应始终确认此函数的返回值。

## <a name="caccesstokenistokenrestricted"></a><a name="istokenrestricted"></a>CAccessToken：：受限制

调用此方法以测试`CAccessToken`对象是否包含受限 S 的清单。

```
bool IsTokenRestricted() const throw();
```

### <a name="return-value"></a>返回值

如果对象包含限制 S 的列表，则返回 TRUE;如果没有限制 SID 或方法失败，则为 FALSE。

## <a name="caccesstokenloaduserprofile"></a><a name="loaduserprofile"></a>CAccessToken：：加载用户配置文件

调用此方法以加载与`CAccessToken`对象关联的用户配置文件。

```
bool LoadUserProfile() throw(...);
```

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

在调试生成中，如果`CAccessToken`不包含有效的令牌，或者用户配置文件已存在，则会发生断言错误。

## <a name="caccesstokenlogonuser"></a><a name="logonuser"></a>CAccessToken：：登录用户

调用此方法为与给定凭据关联的用户创建登录会话。

```
bool LogonUser(
    LPCTSTR pszUserName,
    LPCTSTR pszDomain,
    LPCTSTR pszPassword,
    DWORD dwLogonType = LOGON32_LOGON_INTERACTIVE,
    DWORD dwLogonProvider = LOGON32_PROVIDER_DEFAULT) throw();
```

### <a name="parameters"></a>参数

*pszUser名称*<br/>
指向指定用户名的 null 终止字符串的指针。 这是要登录的用户帐户的名称。

*pszDomain*<br/>
指向 null 终止字符串的指针，该字符串指定其帐户数据库包含*pszUserName*帐户的域或服务器的名称。

*psz密码*<br/>
指向 null 终止字符串的指针，该字符串指定*pszUserName*指定的用户帐户的明文密码。

*dwLogon 类型*<br/>
指定要执行的登录操作的类型。 有关详细信息[，请参阅登录用户](/windows/win32/api/winbase/nf-winbase-logonuserw)。

*dwLogon 提供商*<br/>
指定登录提供程序。 有关详细信息[，请参阅登录用户](/windows/win32/api/winbase/nf-winbase-logonuserw)。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

登录产生的访问令牌将与 相关联`CAccessToken`。 要使此方法成功，`CAccessToken`对象必须保留SE_TCB_NAME权限，将持有者标识为受信任的计算机基础的一部分。 有关所需权限的详细信息，请参阅[登录用户](/windows/win32/api/winbase/nf-winbase-logonuserw)。

## <a name="caccesstokenopencomclienttoken"></a><a name="opencomclienttoken"></a>CAccessToken：：打开COM客户端令牌

从处理来自客户端的呼叫的 COM 服务器内调用此方法，以便`CAccessToken`使用 COM 客户端的访问令牌初始化 。

```
bool OpenCOMClientToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>参数

*dwddAccess*<br/>
指定一个访问掩码，该掩码指定对访问令牌发起访问的请求类型。 这些请求的访问类型与令牌的 DACL 比较来确定同意或拒绝哪些访问。

*b 模拟*<br/>
如果为 TRUE，则如果此调用成功完成，则当前线程将模拟调用 COM 客户端。 如果 FALSE，将打开访问令牌，但线程将在此调用完成时没有模拟令牌。

*bOpenAsSelf*<br/>
指示是针对调用[GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread)方法的线程的安全上下文或调用线程进程的安全上下文进行访问检查。

如果此参数为 FALSE，则使用调用线程的安全上下文执行访问检查。 如果线程正在模拟客户端，则此安全上下文可以是客户端进程的安全上下文。 如果此参数为 TRUE，则使用调用线程的进程的安全上下文进行访问检查。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

[CAuto 还原模拟类](../../atl/reference/cautorevertimpersonation-class.md)可用于通过将*bImpersonate*标志设置为 TRUE 自动还原创建的模拟访问令牌。

## <a name="caccesstokenopennamedpipeclienttoken"></a><a name="opennamedpipeclienttoken"></a>CAccessToken：：打开命名管道客户端令牌

从服务器内调用此方法，通过命名管道获取请求，以便使用客户端的访问令牌`CAccessToken`初始化 。

```
bool OpenNamedPipeClientToken(
    HANDLE hPipe,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>参数

*hPipe*<br/>
处理命名管道。

*dwddAccess*<br/>
指定一个访问掩码，该掩码指定对访问令牌发起访问的请求类型。 这些请求的访问类型与令牌的 DACL 比较来确定同意或拒绝哪些访问。

*b 模拟*<br/>
如果 TRUE，如果此调用成功完成，则当前线程将模拟调用管道客户端。 如果 FALSE，将打开访问令牌，但线程将在此调用完成时没有模拟令牌。

*bOpenAsSelf*<br/>
指示是针对调用[GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread)方法的线程的安全上下文或调用线程进程的安全上下文进行访问检查。

如果此参数为 FALSE，则使用调用线程的安全上下文执行访问检查。 如果线程正在模拟客户端，则此安全上下文可以是客户端进程的安全上下文。 如果此参数为 TRUE，则使用调用线程的进程的安全上下文进行访问检查。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

[CAuto 还原模拟类](../../atl/reference/cautorevertimpersonation-class.md)可用于通过将*bImpersonate*标志设置为 TRUE 自动还原创建的模拟访问令牌。

## <a name="caccesstokenopenrpcclienttoken"></a><a name="openrpcclienttoken"></a>CAccessToken：：打开RPC客户端令牌

从服务器内调用此方法，以处理来自 RPC 客户端的调用，以便`CAccessToken`使用客户端的访问令牌初始化 。

```
bool OpenRPCClientToken(
    RPC_BINDING_HANDLE BindingHandle,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>参数

*绑定句柄*<br/>
服务器上表示对客户端绑定的绑定句柄。

*dwddAccess*<br/>
指定一个访问掩码，该掩码指定对访问令牌发起访问的请求类型。 这些请求的访问类型与令牌的 DACL 比较来确定同意或拒绝哪些访问。

*b 模拟*<br/>
如果为 TRUE，则如果此调用成功完成，则当前线程将模拟调用 RPC 客户端。 如果 FALSE，将打开访问令牌，但线程将在此调用完成时没有模拟令牌。

*bOpenAsSelf*<br/>
指示是针对调用[GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread)方法的线程的安全上下文或调用线程进程的安全上下文进行访问检查。

如果此参数为 FALSE，则使用调用线程的安全上下文执行访问检查。 如果线程正在模拟客户端，则此安全上下文可以是客户端进程的安全上下文。 如果此参数为 TRUE，则使用调用线程的进程的安全上下文进行访问检查。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

[CAuto 还原模拟类](../../atl/reference/cautorevertimpersonation-class.md)可用于通过将*bImpersonate*标志设置为 TRUE 自动还原创建的模拟访问令牌。

## <a name="caccesstokenopenthreadtoken"></a><a name="openthreadtoken"></a>CAccessToken：：打开线程令牌

调用此方法以设置模拟级别，然后使用给定线程中的令牌初始化`CAccessToken`。

```
bool OpenThreadToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) throw(...);
```

### <a name="parameters"></a>参数

*dwddAccess*<br/>
指定一个访问掩码，该掩码指定对访问令牌发起访问的请求类型。 这些请求的访问类型与令牌的 DACL 比较来确定同意或拒绝哪些访问。

*b 模拟*<br/>
如果为 TRUE，则在此方法完成后，线程将留在请求的模拟级别。 如果 FALSE，线程将恢复为其原始模拟级别。

*bOpenAsSelf*<br/>
指示是针对调用[GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread)方法的线程的安全上下文或调用线程进程的安全上下文进行访问检查。

如果此参数为 FALSE，则使用调用线程的安全上下文执行访问检查。 如果线程正在模拟客户端，则此安全上下文可以是客户端进程的安全上下文。 如果此参数为 TRUE，则使用调用线程的进程的安全上下文进行访问检查。

*Sil*<br/>
指定提供令牌模拟级别的[SECURITY_IMPERSONATION_LEVEL](/windows/win32/api/winnt/ne-winnt-security_impersonation_level)枚举类型。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

`OpenThreadToken`类似于[CAccessToken：：getThreadToken](#getthreadtoken)，但在从线程的访问令牌初始化`CAccessToken`之前设置模拟级别。

[CAuto 还原模拟类](../../atl/reference/cautorevertimpersonation-class.md)可用于通过将*bImpersonate*标志设置为 TRUE 自动还原创建的模拟访问令牌。

## <a name="caccesstokenprivilegecheck"></a><a name="privilegecheck"></a>CAccessToken：:P里维莱格检查

调用此方法以确定对象中`CAccessToken`是否启用了指定的权限集。

```
bool PrivilegeCheck(
    PPRIVILEGE_SET RequiredPrivileges,
    bool* pbResult) const throw();
```

### <a name="parameters"></a>参数

*必需权限*<br/>
指向[PRIVILEGE_SET](/windows/win32/api/winnt/ns-winnt-privilege_set)结构的指针。

*pb 结果*<br/>
指向方法集的值的指针，以指示`CAccessToken`对象中是否启用了任何或所有指定的权限。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

返回`PrivilegeCheck`时，如果`Attributes`启用了相应的权限，则每个[LUID_AND_ATTRIBUTES](/windows/win32/api/winnt/ns-winnt-luid_and_attributes)结构的成员设置为SE_PRIVILEGE_USED_FOR_ACCESS。 此方法调用[特权检查](/windows/win32/api/securitybaseapi/nf-securitybaseapi-privilegecheck)Win32 函数。

## <a name="caccesstokenrevert"></a><a name="revert"></a>CAccessToken：：恢复

调用此方法以阻止线程使用模拟令牌。

```
bool Revert(HANDLE hThread = NULL) const throw();
```

### <a name="parameters"></a>参数

*hThread*<br/>
句柄到线程以从模拟还原。 如果*hThread*为 NULL，则假定当前线程。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

模拟令牌的还原可以使用[CAuto 还原模拟类](../../atl/reference/cautorevertimpersonation-class.md)自动执行。

## <a name="caccesstokensetdefaultdacl"></a><a name="setdefaultdacl"></a>CAccessToken：：设置默认Dacl

调用此方法以设置`CAccessToken`对象的默认 DACL。

```
bool SetDefaultDacl(const CDacl& rDacl) throw(...);
```

### <a name="parameters"></a>参数

*rDacl*<br/>
新的默认[CDacl 类](../../atl/reference/cdacl-class.md)信息。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

默认 DACL 是 DACL，默认情况下，当使用此访问令牌创建新对象时，它使用 DACL。

## <a name="caccesstokensetowner"></a><a name="setowner"></a>CAccessToken：：SetOwner

调用此方法以设置`CAccessToken`对象的所有者。

```
bool SetOwner(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>参数

*rSid*<br/>
包含所有者信息的[CSid 类](../../atl/reference/csid-class.md)对象。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

所有者是默认所有者，用于在此访问令牌生效时创建的新对象。

## <a name="caccesstokensetprimarygroup"></a><a name="setprimarygroup"></a>CAccessToken：：设置主要组

调用此方法以设置`CAccessToken`对象的主组。

```
bool SetPrimaryGroup(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>参数

*rSid*<br/>
包含主组信息的[CSid 类](../../atl/reference/csid-class.md)对象。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

主组是此访问令牌生效时创建的新对象的默认组。

## <a name="see-also"></a>请参阅

[ATL 安全示例](../../overview/visual-cpp-samples.md)<br/>
[访问令牌](/windows/win32/SecAuthZ/access-tokens)<br/>
[类概述](../../atl/atl-class-overview.md)
