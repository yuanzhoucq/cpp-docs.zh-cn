---
title: "CAccessToken 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
caps.latest.revision: 24
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 79845a2be4f79a1ee94a9440e8508bcb0e38bcdd
ms.lasthandoff: 02/24/2017

---
# <a name="caccesstoken-class"></a>CAccessToken 类
此类是一个访问令牌的包装器。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
class CAccessToken
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CAccessToken:: ~ CAccessToken](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CAccessToken::Attach](#attach)|调用此方法的授予的访问权限标记的句柄所有权。|  
|[CAccessToken::CheckTokenMembership](#checktokenmembership)|调用此方法以确定是否在中启用具有指定的 SID`CAccessToken`对象。|  
|[CAccessToken::CreateImpersonationToken](#createimpersonationtoken)|调用此方法以创建新的模拟访问令牌。|  
|[CAccessToken::CreatePrimaryToken](#createprimarytoken)|调用此方法以创建新的主令牌。|  
|[CAccessToken::CreateProcessAsUser](#createprocessasuser)|调用此方法以创建新的进程所表示的用户的安全上下文中运行`CAccessToken`对象。|  
|[CAccessToken::CreateRestrictedToken](#createrestrictedtoken)|调用此方法以创建一个新的受限`CAccessToken`对象。|  
|[CAccessToken::Detach](#detach)|调用此方法以撤消访问令牌的所有权。|  
|[CAccessToken::DisablePrivilege](#disableprivilege)|调用此方法以禁用在特权`CAccessToken`对象。|  
|[CAccessToken::DisablePrivileges](#disableprivileges)|调用此方法以禁用中的一个或多个权限`CAccessToken`对象。|  
|[CAccessToken::EnablePrivilege](#enableprivilege)|调用此方法以启用中的特权`CAccessToken`对象。|  
|[CAccessToken::EnablePrivileges](#enableprivileges)|调用此方法以启用中的一个或多个权限`CAccessToken`对象。|  
|[CAccessToken::GetDefaultDacl](#getdefaultdacl)|调用此方法以返回`CAccessToken`对象的默认 DACL。|  
|[CAccessToken::GetEffectiveToken](#geteffectivetoken)|调用此方法以获取`CAccessToken`对象等于当前线程在有效的访问令牌。|  
|[CAccessToken::GetGroups](#getgroups)|调用此方法以返回`CAccessToken`令牌对象的组。|  
|[CAccessToken::GetHandle](#gethandle)|调用此方法以检索访问令牌的句柄。|  
|[CAccessToken::GetImpersonationLevel](#getimpersonationlevel)|调用此方法来获得访问令牌的模拟级别。|  
|[CAccessToken::GetLogonSessionId](#getlogonsessionid)|调用此方法以获取与关联的登录会话 ID`CAccessToken`对象。|  
|[CAccessToken::GetLogonSid](#getlogonsid)|调用此方法以获取与关联的登录 SID`CAccessToken`对象。|  
|[CAccessToken::GetOwner](#getowner)|调用此方法以获取与关联的所有者`CAccessToken`对象。|  
|[CAccessToken::GetPrimaryGroup](#getprimarygroup)|调用此方法以获取与关联的主组`CAccessToken`对象。|  
|[CAccessToken::GetPrivileges](#getprivileges)|调用此方法以获取与关联的权限`CAccessToken`对象。|  
|[CAccessToken::GetProcessToken](#getprocesstoken)|调用此方法可使用给定进程中的访问令牌初始化 `CAccessToken`。|  
|[CAccessToken::GetProfile](#getprofile)|调用此方法以获取指向关联的用户配置文件的句柄`CAccessToken`对象。|  
|[CAccessToken::GetSource](#getsource)|调用此方法以获取的源`CAccessToken`对象。|  
|[CAccessToken::GetStatistics](#getstatistics)|调用此方法以获取与关联的信息`CAccessToken`对象。|  
|[CAccessToken::GetTerminalServicesSessionId](#getterminalservicessessionid)|调用此方法以获取与关联的终端服务会话 ID`CAccessToken`对象。|  
|[CAccessToken::GetThreadToken](#getthreadtoken)|调用此方法以初始化`CAccessToken`使用给定的线程中的令牌。|  
|[CAccessToken::GetTokenId](#gettokenid)|调用此方法以获取与关联的标记 ID`CAccessToken`对象。|  
|[CAccessToken::GetType](#gettype)|调用此方法以获取的令牌类型`CAccessToken`对象。|  
|[CAccessToken::GetUser](#getuser)|调用此方法来确定与关联的用户`CAccessToken`对象。|  
|[CAccessToken::HKeyCurrentUser](#hkeycurrentuser)|调用此方法以获取指向关联的用户配置文件的句柄`CAccessToken`对象。|  
|[CAccessToken::Impersonate](#impersonate)|调用此方法来分配模拟`CAccessToken`给线程。|  
|[CAccessToken::ImpersonateLoggedOnUser](#impersonateloggedonuser)|调用此方法以允许调用线程，同时模拟登录的用户的安全上下文。|  
|[CAccessToken::IsTokenRestricted](#istokenrestricted)|调用此方法来测试是否`CAccessToken`对象包含的受限 Sid 的列表。|  
|[CAccessToken::LoadUserProfile](#loaduserprofile)|调用此方法以加载用户配置文件与相关联`CAccessToken`对象。|  
|[CAccessToken::LogonUser](#logonuser)|调用此方法以创建与给定的凭据关联的用户的登录会话。|  
|[CAccessToken::OpenCOMClientToken](#opencomclienttoken)|内调用此方法从使用 COM 服务器来处理来自客户端执行调用以初始化`CAccessToken`使用从 COM 客户端的访问令牌。|  
|[CAccessToken::OpenNamedPipeClientToken](#opennamedpipeclienttoken)|内调用此方法从一台服务器采用请求通过命名管道来初始化`CAccessToken`使用从客户端的访问令牌。|  
|[CAccessToken::OpenRPCClientToken](#openrpcclienttoken)|内调用此方法从使用服务器来处理从 RPC 客户端执行调用以初始化`CAccessToken`使用从客户端的访问令牌。|  
|[CAccessToken::OpenThreadToken](#openthreadtoken)|调用此方法可将模拟级别设置，然后初始化`CAccessToken`使用给定的线程中的令牌。|  
|[CAccessToken::PrivilegeCheck](#privilegecheck)|调用此方法以确定是否在中启用指定的一组特权**CAccessToken**对象。|  
|[CAccessToken::Revert](#revert)|调用此方法来停止正在使用模拟标记的线程。|  
|[CAccessToken::SetDefaultDacl](#setdefaultdacl)|调用此方法可设置默认的 DACL`CAccessToken`对象。|  
|[CAccessToken::SetOwner](#setowner)|调用此方法以设置其所有者的`CAccessToken`对象。|  
|[CAccessToken::SetPrimaryGroup](#setprimarygroup)|调用此方法可设置的主要组`CAccessToken`对象。|  
  
## <a name="remarks"></a>备注  
 [访问令牌](http://msdn.microsoft.com/library/windows/desktop/aa374909)是一个对象，描述进程或线程的安全上下文，并分配给每个用户登录到 Windows NT 或 Windows 2000 的系统。  
  
 在 Windows 访问控制模型的简介，请参阅[访问控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlsecurity.h  
  
##  <a name="attach"></a>CAccessToken::Attach  
 调用此方法的授予的访问权限标记的句柄所有权。  
  
```
void Attach(HANDLE hToken) throw();
```  
  
### <a name="parameters"></a>参数  
 *hToken*  
 对访问令牌的句柄。  
  
### <a name="remarks"></a>备注  
 在调试版本中，如果发生断言错误`CAccessToken`对象已具有一个访问令牌的所有权。  
  
##  <a name="dtor"></a>CAccessToken:: ~ CAccessToken  
 析构函数。  
  
```
virtual ~CAccessToken() throw();
```  
  
### <a name="remarks"></a>备注  
 释放所有已分配的资源。  
  
##  <a name="checktokenmembership"></a>CAccessToken::CheckTokenMembership  
 调用此方法以确定是否在中启用具有指定的 SID`CAccessToken`对象。  
  
```
bool CheckTokenMembership(
    const CSid& rSid, 
    bool* pbIsMember) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 `rSid`  
 引用[CSid 类](../../atl/reference/csid-class.md)对象。  
  
 `pbIsMember`  
 指向接收检查的结果的变量的指针。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
 `CheckTokenMembership`方法检查是否存在的用户和组 Sid 的访问令牌中的 SID。 如果 SID 存在且具有 SE_GROUP_ENABLED 属性*pbIsMember*是设置为 true; 否则为它将设置为 false。  
  
 在调试版本中，如果发生断言错误`pbIsMember`不是有效的指针。  
  
> [!NOTE]
>  `CAccessToken`对象必须是模拟令牌，并且没有主标记。  
  
##  <a name="createimpersonationtoken"></a>CAccessToken::CreateImpersonationToken  
 调用此方法以创建模拟访问令牌。  
  
```
bool CreateImpersonationToken(
    CAccessToken* pImp, 
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 `pImp`  
 指向新`CAccessToken`对象。  
  
 `sil`  
 指定[SECURITY_IMPERSONATION_LEVEL](http://msdn.microsoft.com/library/windows/desktop/aa379572)枚举类型，用于提供新的令牌的模拟级别。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
 `CreateImpersonationToken`调用[DuplicateToken](http://msdn.microsoft.com/library/windows/desktop/aa446616)来创建新的模拟令牌。  
  
##  <a name="createprimarytoken"></a>CAccessToken::CreatePrimaryToken  
 调用此方法以创建新的主令牌。  
  
```
bool CreatePrimaryToken(
    CAccessToken* pPri,
    DWORD dwDesiredAccess = MAXIMUM_ALLOWED,
    const CSecurityAttributes* pTokenAttributes = NULL) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 *pPri*  
 指向新`CAccessToken`对象。  
  
 `dwDesiredAccess`  
 指定新的令牌的请求的访问权限。 默认情况下，MAXIMUM_ALLOWED，请求所有调用方对有效的访问权限。 请参阅[访问权限和访问掩码](http://msdn.microsoft.com/library/windows/desktop/aa374902)对更多的访问权限。  
  
 *pTokenAttributes*  
 指向[SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560)结构，它指定新的令牌的安全描述符，并确定是否子进程可以继承的标记。 如果*pTokenAttributes*为 NULL，该令牌获取的默认安全描述符并不能继承句柄。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
 `CreatePrimaryToken`调用[DuplicateTokenEx](http://msdn.microsoft.com/library/windows/desktop/aa446617)若要创建新的主令牌。  
  
##  <a name="createprocessasuser"></a>CAccessToken::CreateProcessAsUser  
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
 *pApplicationName*  
 以 null 结尾的字符串，指定要执行的模块的指针。 此参数可能不能为 NULL。  
  
 *pCommandLine*  
 以 null 结尾的字符串，指定要执行的命令行的指针。  
  
 *pProcessInformation*  
 指向[PROCESS_INFORMATION](http://msdn.microsoft.com/library/windows/desktop/ms684873)收到有关新进程的标识信息的结构。  
  
 *pStartupInfo*  
 指向[STARTUPINFO](http://msdn.microsoft.com/library/windows/desktop/ms686331)结构，它指定新的进程的主窗口的显示方式。  
  
 `dwCreationFlags`  
 指定用于控制优先级类和过程的创建其他标志。 请参阅 Win32 函数[CreateProcessAsUser](http://msdn.microsoft.com/library/windows/desktop/ms682429)的标志的列表。  
  
 *bLoadProfile*  
 如果为 true，用户的配置文件加载与[LoadUserProfile](http://msdn.microsoft.com/library/windows/desktop/bb762281)。  
  
 *pProcessAttributes*  
 指向[SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560)结构，它指定新的进程的安全描述符，并确定是否子进程可以继承返回的句柄。 如果*pProcessAttributes*为 NULL，该进程获取的默认安全描述符并不能继承句柄。  
  
 *pThreadAttributes*  
 指向[SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560)结构，它指定新的线程的安全描述符，并确定是否子进程可以继承返回的句柄。 如果*pThreadAttributes*为 NULL，该线程将获取的默认安全描述符，不能继承句柄。  
  
 *bInherit*  
 指示新进程是否从调用进程继承句柄。 如果为 true，新进程将继承调用进程中每个可继承的打开句柄。 继承句柄具有与原始句柄相同的值和访问权限。  
  
 *pCurrentDirectory*  
 指向以 null 结尾的字符串，指定当前驱动器和新进程的目录。 字符串必须包含一个驱动器号的完整路径。 如果此参数为 NULL，则新进程将具有相同的当前驱动器和目录与调用进程。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
 **CreateProcessAsUser**使用`CreateProcessAsUser`用来创建所表示的用户的安全上下文中运行一个新进程的 Win32 函数`CAccessToken`对象。 请参阅的说明[CreateProcessAsUser](http://msdn.microsoft.com/library/windows/desktop/ms682429)有关所需的参数的完整讨论的函数。  
  
 若要成功，此方法`CAccessToken`对象必须保持 AssignPrimaryToken （除非它是受限制的标记） 和 IncreaseQuota 特权。  
  
##  <a name="createrestrictedtoken"></a>CAccessToken::CreateRestrictedToken  
 调用此方法以创建一个新的受限`CAccessToken`对象。  
  
```
bool CreateRestrictedToken(
    CAccessToken* pRestrictedToken,
    const CTokenGroups& SidsToDisable,
    const CTokenGroups& SidsToRestrict,
    const CTokenPrivileges& PrivilegesToDelete = CTokenPrivileges()) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 *pRestrictedToken*  
 将新的、 受限`CAccessToken`对象。  
  
 `SidsToDisable`  
 一个`CTokenGroups`对象，它指定仅拒绝 Sid。  
  
 *SidsToRestrict*  
 一个`CTokenGroups`对象，它指定的限制 Sid。  
  
 `PrivilegesToDelete`  
 一个`CTokenPrivileges`对象，它在受限制的令牌中指定要删除的特权。 默认值创建一个空对象。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
 `CreateRestrictedToken`使用[CreateRestrictedToken](http://msdn.microsoft.com/library/windows/desktop/aa446583)用来创建一个新的 Win32 函数`CAccessToken`对象的限制。  
  
> [!NOTE]
>  此方法仅可在 Windows 2000 或更高版本。  
  
> [!IMPORTANT]
>  当使用`CreateRestrictedToken`，请确保满足以下︰ 现有令牌为有效 （而不由用户输入） 和`SidsToDisable`和`PrivilegesToDelete`是同时有效 （且不由用户输入）。 如果该方法返回 false，则拒绝功能。  
  
##  <a name="detach"></a>CAccessToken::Detach  
 调用此方法以撤消访问令牌的所有权。  
  
```
HANDLE Detach() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回的句柄`CAccessToken`已分离的。  
  
### <a name="remarks"></a>备注  
 此方法撤消`CAccessToken`的访问令牌的所有权。  
  
##  <a name="disableprivilege"></a>CAccessToken::DisablePrivilege  
 调用此方法以禁用在特权`CAccessToken`对象。  
  
```
bool DisablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `pszPrivilege`  
 指向包含的权限，则禁用中以字符串的指针`CAccessToken`对象。  
  
 `pPreviousState`  
 指向`CTokenPrivileges`对象，它将包含权限的以前的状态。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
##  <a name="disableprivileges"></a>CAccessToken::DisablePrivileges  
 调用此方法以禁用中的一个或多个权限`CAccessToken`对象。  
  
```
bool DisablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `rPrivileges`  
 指向包含要在中禁用的特权的字符串数组指针`CAccessToken`对象。  
  
 `pPreviousState`  
 指向`CTokenPrivileges`对象，它将包含权限的以前的状态。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
##  <a name="enableprivilege"></a>CAccessToken::EnablePrivilege  
 调用此方法以启用中的特权`CAccessToken`对象。  
  
```
bool EnablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `pszPrivilege`  
 包含在中启用的权限的字符串指针`CAccessToken`对象。  
  
 `pPreviousState`  
 指向`CTokenPrivileges`对象，它将包含权限的以前的状态。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
##  <a name="enableprivileges"></a>CAccessToken::EnablePrivileges  
 调用此方法以启用中的一个或多个权限`CAccessToken`对象。  
  
```
bool EnablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `rPrivileges`  
 指向包含要在中启用的权限的字符串数组指针`CAccessToken`对象。  
  
 `pPreviousState`  
 指向`CTokenPrivileges`对象，它将包含权限的以前的状态。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
##  <a name="getdefaultdacl"></a>CAccessToken::GetDefaultDacl  
 调用此方法以返回`CAccessToken`对象的默认 DACL。  
  
```
bool GetDefaultDacl(CDacl* pDacl) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 `pDacl`  
 指向[CDacl 类](../../atl/reference/cdacl-class.md)对象将接收**CAccessToken**对象的默认 DACL。  
  
### <a name="return-value"></a>返回值  
 如果默认的 DACL 已否则被恢复，则返回 false，则返回 true。  
  
##  <a name="geteffectivetoken"></a>CAccessToken::GetEffectiveToken  
 调用此方法以获取`CAccessToken`对象等于当前线程在有效的访问令牌。  
  
```
bool GetEffectiveToken(DWORD dwDesiredAccess) throw();
```  
  
### <a name="parameters"></a>参数  
 `dwDesiredAccess`  
 指定一个访问掩码，该掩码指定对访问令牌发起访问的请求类型。 这些请求的访问类型与令牌的 DACL 比较来确定同意或拒绝哪些访问。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
##  <a name="getgroups"></a>CAccessToken::GetGroups  
 调用此方法以返回`CAccessToken`令牌对象的组。  
  
```
bool GetGroups(CTokenGroups* pGroups) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 *pGroups*  
 指向[CTokenGroups 类](../../atl/reference/ctokengroups-class.md)将收到的组信息的对象。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
##  <a name="gethandle"></a>CAccessToken::GetHandle  
 调用此方法以检索访问令牌的句柄。  
  
```
HANDLE GetHandle() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回的句柄`CAccessToken`对象的访问令牌。  
  
##  <a name="getimpersonationlevel"></a>CAccessToken::GetImpersonationLevel  
 调用此方法来获得访问令牌的模拟级别。  
  
```
bool GetImpersonationLevel(
    SECURITY_IMPERSONATION_LEVEL* pImpersonationLevel) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 *pImpersonationLevel*  
 指向[SECURITY_IMPERSONATION_LEVEL](http://msdn.microsoft.com/library/windows/desktop/aa379572)枚举类型将接收模拟级别的信息。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
##  <a name="getlogonsessionid"></a>CAccessToken::GetLogonSessionId  
 调用此方法以获取与关联的登录会话 ID`CAccessToken`对象。  
  
```
bool GetLogonSessionId(LUID* pluid) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 `pluid`  
 指向[LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261)它将收到登录会话的 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
 在调试版本中，如果发生断言错误`pluid`是无效的值。  
  
##  <a name="getlogonsid"></a>CAccessToken::GetLogonSid  
 调用此方法以获取与关联的登录 SID`CAccessToken`对象。  
  
```
bool GetLogonSid(CSid* pSid) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 `pSid`  
 指向[CSid 类](../../atl/reference/csid-class.md)对象。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
 在调试版本中，如果发生断言错误*pSid*是无效的值。  
  
##  <a name="getowner"></a>CAccessToken::GetOwner  
 调用此方法以获取与关联的所有者`CAccessToken`对象。  
  
```
bool GetOwner(CSid* pSid) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 `pSid`  
 指向[CSid 类](../../atl/reference/csid-class.md)对象。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
 默认情况下，在此访问令牌有效期间创建的任何对象上设置所有者。  
  
##  <a name="getprimarygroup"></a>CAccessToken::GetPrimaryGroup  
 调用此方法以获取与关联的主组`CAccessToken`对象。  
  
```
bool GetPrimaryGroup(CSid* pSid) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 `pSid`  
 指向[CSid 类](../../atl/reference/csid-class.md)对象。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
 在此访问令牌有效期间创建的任何对象上的默认设置组。  
  
##  <a name="getprivileges"></a>CAccessToken::GetPrivileges  
 调用此方法以获取与关联的权限`CAccessToken`对象。  
  
```
bool GetPrivileges(CTokenPrivileges* pPrivileges) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 `pPrivileges`  
 指向[CTokenPrivileges 类](../../atl/reference/ctokenprivileges-class.md)将收到的权限的对象。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
##  <a name="getprocesstoken"></a>CAccessToken::GetProcessToken  
 调用此方法可使用给定进程中的访问令牌初始化 `CAccessToken`。  
  
```
bool GetProcessToken(DWORD dwDesiredAccess, HANDLE hProcess = NULL) throw();
```  
  
### <a name="parameters"></a>参数  
 `dwDesiredAccess`  
 指定一个访问掩码，该掩码指定对访问令牌发起访问的请求类型。 这些请求的访问类型与令牌的 DACL 比较来确定同意或拒绝哪些访问。  
  
 *hProcess*  
 用于访问令牌已打开的进程的句柄。 如果使用默认值 `NULL`，将使用当前进程。  
  
### <a name="return-value"></a>返回值  
 成功时返回 `true`，失败时返回 `false`。  
  
### <a name="remarks"></a>备注  
 调用[OpenProcessToken](http://msdn.microsoft.com/library/aa379295\(vs.85\).aspx) Win32 函数。  
  
##  <a name="getprofile"></a>CAccessToken::GetProfile  
 调用此方法以获取指向关联的用户配置文件的句柄`CAccessToken`对象。  
  
```
HANDLE GetProfile() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回指向用户配置文件，则为 NULL，如果没有配置文件存在的句柄。  
  
##  <a name="getsource"></a>CAccessToken::GetSource  
 调用此方法以获取的源`CAccessToken`对象。  
  
```
bool GetSource(TOKEN_SOURCE* pSource) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 *pSource*  
 指向[TOKEN_SOURCE](http://msdn.microsoft.com/library/windows/desktop/aa379631)结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
##  <a name="getstatistics"></a>CAccessToken::GetStatistics  
 调用此方法以获取与关联的信息`CAccessToken`对象。  
  
```
bool GetStatistics(TOKEN_STATISTICS* pStatistics) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 *pStatistics*  
 指向[TOKEN_STATISTICS](http://msdn.microsoft.com/library/windows/desktop/aa379632)结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
##  <a name="getterminalservicessessionid"></a>CAccessToken::GetTerminalServicesSessionId  
 调用此方法以获取与关联的终端服务会话 ID`CAccessToken`对象。  
  
```
bool GetTerminalServicesSessionId(DWORD* pdwSessionId) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 *pdwSessionId*  
 终端服务会话 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
##  <a name="getthreadtoken"></a>CAccessToken::GetThreadToken  
 调用此方法以初始化`CAccessToken`使用给定的线程中的令牌。  
  
```
bool GetThreadToken(
    DWORD dwDesiredAccess,
    HANDLE hThread = NULL,
    bool bOpenAsSelf = true) throw();
```  
  
### <a name="parameters"></a>参数  
 `dwDesiredAccess`  
 指定一个访问掩码，该掩码指定对访问令牌发起访问的请求类型。 这些请求的访问类型与令牌的 DACL 比较来确定同意或拒绝哪些访问。  
  
 `hThread`  
 其访问令牌已打开的线程的句柄。  
  
 `bOpenAsSelf`  
 指示是否要对线程调用的安全上下文执行访问检查`GetThreadToken`方法或对调用线程的过程的安全上下文。  
  
 如果此参数为 false，为调用线程使用的安全上下文执行访问检查。 如果该线程正在模拟客户端，此安全上下文可以是客户端过程。 如果此参数为 true，为调用线程使用该进程的安全上下文进行访问检查。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
##  <a name="gettokenid"></a>CAccessToken::GetTokenId  
 调用此方法以获取与关联的标记 ID`CAccessToken`对象。  
  
```
bool GetTokenId(LUID* pluid) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 `pluid`  
 指向[LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261)中有哪些将接收令牌的 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
##  <a name="gettype"></a>CAccessToken::GetType  
 调用此方法以获取的令牌类型`CAccessToken`对象。  
  
```
bool GetType(TOKEN_TYPE* pType) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 `pType`  
 地址的指针[TOKEN_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379633)变量，在成功时，收到的令牌的类型。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
 **TOKEN_TYPE**枚举类型包含一个主令牌和模拟令牌有差异的值。  
  
##  <a name="getuser"></a>CAccessToken::GetUser  
 调用此方法来确定与关联的用户`CAccessToken`对象。  
  
```
bool GetUser(CSid* pSid) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 `pSid`  
 指向[CSid 类](../../atl/reference/csid-class.md)对象。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
##  <a name="hkeycurrentuser"></a>CAccessToken::HKeyCurrentUser  
 调用此方法以获取指向关联的用户配置文件的句柄`CAccessToken`对象。  
  
```
HKEY HKeyCurrentUser() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回指向用户配置文件，则为 NULL，如果没有配置文件存在的句柄。  
  
##  <a name="impersonate"></a>CAccessToken::Impersonate  
 调用此方法来分配模拟`CAccessToken`给线程。  
  
```
bool Impersonate(HANDLE hThread = NULL) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 `hThread`  
 若要将分配到模拟标记的线程的句柄。 必须具有 TOKEN_IMPERSONATE 访问权限打开此句柄。 如果`hThread`为 NULL，该方法会导致要停止使用模拟标记的线程。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
 在调试版本中，如果发生断言错误`CAccessToken`没有指向有效的标记。  
  
 [CAutoRevertImpersonation 类](../../atl/reference/cautorevertimpersonation-class.md)可用于自动还原模拟的访问令牌。  
  
##  <a name="impersonateloggedonuser"></a>CAccessToken::ImpersonateLoggedOnUser  
 调用此方法以允许调用线程，同时模拟登录的用户的安全上下文。  
  
```
bool ImpersonateLoggedOnUser() const throw(...);
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
  
> [!IMPORTANT]
>  如果出于任何原因，对模拟函数的调用失败，无法模拟该客户端并且客户端请求由执行调用进程的安全上下文中。 如果该进程正在作为高特权帐户，或作为管理组的成员，用户可能能够执行的操作，系统将否则允许他或她。 因此，应该始终确认此函数的返回值。  
  
##  <a name="istokenrestricted"></a>CAccessToken::IsTokenRestricted  
 调用此方法来测试是否`CAccessToken`对象包含的受限 Sid 的列表。  
  
```
bool IsTokenRestricted() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果对象包含限制 Sid，false 是否存在任何限制 Sid 的列表，或该方法将失败，则返回 true。  
  
##  <a name="loaduserprofile"></a>CAccessToken::LoadUserProfile  
 调用此方法以加载用户配置文件与相关联`CAccessToken`对象。  
  
```
bool LoadUserProfile() throw(...);
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
 在调试版本中，如果发生断言错误`CAccessToken`不包含有效的令牌，或者如果用户配置文件已存在。  
  
##  <a name="logonuser"></a>CAccessToken::LogonUser  
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
 `pszUserName`  
 以 null 结尾的字符串，它指定用户名称的指针。 这是用于登录到的用户帐户的名称。  
  
 *pszDomain*  
 以 null 结尾的字符串，它指定域或其帐户数据库中包含的服务器的名称的指针`pszUserName`帐户。  
  
 `pszPassword`  
 指向以 null 结尾的字符串，指定所指定的用户帐户的明文密码`pszUserName`。  
  
 *dwLogonType*  
 指定要执行的登录操作的类型。 请参阅[LogonUser](http://msdn.microsoft.com/library/windows/desktop/aa378184)的更多详细信息。  
  
 *dwLogonProvider*  
 指定登录提供程序。 请参阅[LogonUser](http://msdn.microsoft.com/library/windows/desktop/aa378184)的更多详细信息。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
 登录过程中的令牌生成将与关联的访问`CAccessToken`。 若要成功，此方法`CAccessToken`对象必须具有相关 SE_TCB_NAME 权限，作为基的受信任计算机的一部分识别持有者。 请参阅[LogonUser](http://msdn.microsoft.com/library/windows/desktop/aa378184)有关所需的权限的详细信息。  
  
##  <a name="opencomclienttoken"></a>CAccessToken::OpenCOMClientToken  
 内调用此方法从使用 COM 服务器来处理来自客户端执行调用以初始化`CAccessToken`使用从 COM 客户端的访问令牌。  
  
```
bool OpenCOMClientToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `dwDesiredAccess`  
 指定一个访问掩码，该掩码指定对访问令牌发起访问的请求类型。 这些请求的访问类型与令牌的 DACL 比较来确定同意或拒绝哪些访问。  
  
 `bImpersonate`  
 如果为 true，当前线程将模拟调用 COM 客户端，如果此调用成功完成。 如果为 false，将打开访问令牌，但该线程将没有模拟令牌，此调用完成时。  
  
 `bOpenAsSelf`  
 指示是否要对线程调用的安全上下文执行访问检查[GetThreadToken](http://msdn.microsoft.com/library/windows/desktop/ms683182)方法或对调用线程的过程的安全上下文。  
  
 如果此参数为 false，为调用线程使用的安全上下文执行访问检查。 如果该线程正在模拟客户端，此安全上下文可以是客户端过程。 如果此参数为 true，为调用线程使用该进程的安全上下文进行访问检查。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
 [CAutoRevertImpersonation 类](../../atl/reference/cautorevertimpersonation-class.md)可用于自动还原模拟的访问令牌通过设置创建`bImpersonate`标记，用于*true*。  
  
##  <a name="opennamedpipeclienttoken"></a>CAccessToken::OpenNamedPipeClientToken  
 内调用此方法从一台服务器采用请求通过命名管道来初始化`CAccessToken`使用从客户端的访问令牌。  
  
```
bool OpenNamedPipeClientToken(
    HANDLE hPipe,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```  
  
### <a name="parameters"></a>参数  
 *hPipe*  
 命名管道的句柄。  
  
 `dwDesiredAccess`  
 指定一个访问掩码，该掩码指定对访问令牌发起访问的请求类型。 这些请求的访问类型与令牌的 DACL 比较来确定同意或拒绝哪些访问。  
  
 `bImpersonate`  
 如果为 true，则当前线程成功完成此调用时将模拟调用管道客户端。 如果为 false，将打开访问令牌，但该线程将没有模拟令牌，此调用完成时。  
  
 `bOpenAsSelf`  
 指示是否要对线程调用的安全上下文执行访问检查[GetThreadToken](http://msdn.microsoft.com/library/windows/desktop/ms683182)方法或对调用线程的过程的安全上下文。  
  
 如果此参数为 false，为调用线程使用的安全上下文执行访问检查。 如果该线程正在模拟客户端，此安全上下文可以是客户端过程。 如果此参数为 true，为调用线程使用该进程的安全上下文进行访问检查。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
 [CAutoRevertImpersonation 类](../../atl/reference/cautorevertimpersonation-class.md)可用于自动还原模拟的访问令牌通过设置创建`bImpersonate`标记，用于*true*。  
  
##  <a name="openrpcclienttoken"></a>CAccessToken::OpenRPCClientToken  
 内调用此方法从使用服务器来处理从 RPC 客户端执行调用以初始化`CAccessToken`使用从客户端的访问令牌。  
  
```
bool OpenRPCClientToken(
    RPC_BINDING_HANDLE BindingHandle,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```  
  
### <a name="parameters"></a>参数  
 *BindingHandle*  
 表示与客户端的绑定的服务器上的绑定句柄。  
  
 `dwDesiredAccess`  
 指定一个访问掩码，该掩码指定对访问令牌发起访问的请求类型。 这些请求的访问类型与令牌的 DACL 比较来确定同意或拒绝哪些访问。  
  
 `bImpersonate`  
 如果为 true，则当前线程成功完成此调用时将模拟调用 RPC 客户端。 如果为 false，将打开访问令牌，但该线程将没有模拟令牌，此调用完成时。  
  
 `bOpenAsSelf`  
 指示是否要对线程调用的安全上下文执行访问检查[GetThreadToken](http://msdn.microsoft.com/library/windows/desktop/ms683182)方法或对调用线程的过程的安全上下文。  
  
 如果此参数为 false，为调用线程使用的安全上下文执行访问检查。 如果该线程正在模拟客户端，此安全上下文可以是客户端过程。 如果此参数为 true，为调用线程使用该进程的安全上下文进行访问检查。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
 [CAutoRevertImpersonation 类](../../atl/reference/cautorevertimpersonation-class.md)可用于自动还原模拟的访问令牌通过设置创建`bImpersonate`标记，用于*true*。  
  
##  <a name="openthreadtoken"></a>CAccessToken::OpenThreadToken  
 调用此方法可将模拟级别设置，然后初始化`CAccessToken`使用给定的线程中的令牌。  
  
```
bool OpenThreadToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `dwDesiredAccess`  
 指定一个访问掩码，该掩码指定对访问令牌发起访问的请求类型。 这些请求的访问类型与令牌的 DACL 比较来确定同意或拒绝哪些访问。  
  
 `bImpersonate`  
 如果为 true，该线程将保留在请求的模拟级别中，该方法完成之后。 如果为 false，则线程将恢复到原来的模拟级别。  
  
 `bOpenAsSelf`  
 指示是否要对线程调用的安全上下文执行访问检查[GetThreadToken](http://msdn.microsoft.com/library/windows/desktop/ms683182)方法或对调用线程的过程的安全上下文。  
  
 如果此参数为 false，为调用线程使用的安全上下文执行访问检查。 如果该线程正在模拟客户端，此安全上下文可以是客户端过程。 如果此参数为 true，为调用线程使用该进程的安全上下文进行访问检查。  
  
 `sil`  
 指定[SECURITY_IMPERSONATION_LEVEL](http://msdn.microsoft.com/library/windows/desktop/aa379572)枚举类型，用于提供令牌的模拟级别。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
 `OpenThreadToken`类似于[CAccessToken::GetThreadToken](#getthreadtoken)，但在初始化之前设置的模拟级别`CAccessToken`从线程的访问令牌。  
  
 [CAutoRevertImpersonation 类](../../atl/reference/cautorevertimpersonation-class.md)可用于自动还原模拟的访问令牌通过设置创建`bImpersonate`标记，用于*true*。  
  
##  <a name="privilegecheck"></a>CAccessToken::PrivilegeCheck  
 调用此方法以确定是否在中启用指定的一组特权**CAccessToken**对象。  
  
```
bool PrivilegeCheck(
    PPRIVILEGE_SET RequiredPrivileges,
     bool* pbResult) const throw();
```  
  
### <a name="parameters"></a>参数  
 *RequiredPrivileges*  
 指向[PRIVILEGE_SET](http://msdn.microsoft.com/library/windows/desktop/aa379307)结构。  
  
 *pbResult*  
 指向某一值的方法设置，以指示是否在中启用任何或所有指定的特权`CAccessToken`对象。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
 当`PrivilegeCheck`返回时，**属性**的每个成员[LUID_AND_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379263)结构设置为 SE_PRIVILEGE_USED_FOR_ACCESS，如果启用了相应的权限。 此方法调用[PrivilegeCheck](http://msdn.microsoft.com/library/windows/desktop/aa379304) Win32 函数。  
  
##  <a name="revert"></a>CAccessToken::Revert  
 调用此方法来停止来自使用模拟标记的线程。  
  
```
bool Revert(HANDLE hThread = NULL) const throw();
```  
  
### <a name="parameters"></a>参数  
 `hThread`  
 要将模拟从还原的线程的句柄。 如果*hThread*为 NULL，则假定当前线程。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
 可以使用自动执行的模拟令牌重新[CAutoRevertImpersonation 类](../../atl/reference/cautorevertimpersonation-class.md)。  
  
##  <a name="setdefaultdacl"></a>CAccessToken::SetDefaultDacl  
 调用此方法可设置默认的 DACL`CAccessToken`对象。  
  
```
bool SetDefaultDacl(const CDacl& rDacl) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `rDacl`  
 新的默认[CDacl 类](../../atl/reference/cdacl-class.md)信息。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
 默认值 DACL 是实际上使用此访问令牌创建新对象时，默认情况下使用的 DACL。  
  
##  <a name="setowner"></a>CAccessToken::SetOwner  
 调用此方法以设置其所有者的`CAccessToken`对象。  
  
```
bool SetOwner(const CSid& rSid) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `rSid`  
 [CSid 类](../../atl/reference/csid-class.md)对象，其中包含所有者信息。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
 所有者是用于在此访问令牌有效期间创建的新对象的默认所有者。  
  
##  <a name="setprimarygroup"></a>CAccessToken::SetPrimaryGroup  
 调用此方法可设置的主要组`CAccessToken`对象。  
  
```
bool SetPrimaryGroup(const CSid& rSid) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `rSid`  
 [CSid 类](../../atl/reference/csid-class.md)对象，其中包含的主要组信息。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
 主要组是在此访问令牌有效期间创建的新对象的默认组。  
  
## <a name="see-also"></a>另请参阅  
 [ATLSecurity 示例](../../visual-cpp-samples.md)   
 [访问令牌](http://msdn.microsoft.com/library/windows/desktop/aa374909)   
 [类概述](../../atl/atl-class-overview.md)

