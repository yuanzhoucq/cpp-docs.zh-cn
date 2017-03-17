---
title: "CTokenPrivileges 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges::CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges::Add
- ATLSECURITY/ATL::CTokenPrivileges::Delete
- ATLSECURITY/ATL::CTokenPrivileges::DeleteAll
- ATLSECURITY/ATL::CTokenPrivileges::GetCount
- ATLSECURITY/ATL::CTokenPrivileges::GetDisplayNames
- ATLSECURITY/ATL::CTokenPrivileges::GetLength
- ATLSECURITY/ATL::CTokenPrivileges::GetLuidsAndAttributes
- ATLSECURITY/ATL::CTokenPrivileges::GetNamesAndAttributes
- ATLSECURITY/ATL::CTokenPrivileges::GetPTOKEN_PRIVILEGES
- ATLSECURITY/ATL::CTokenPrivileges::LookupPrivilege
dev_langs:
- C++
helpviewer_keywords:
- CTokenPrivileges class
ms.assetid: 89590105-f001-4014-870d-142926091231
caps.latest.revision: 23
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 4d732dbf27c2155ffb98ca59b140d01ea92458e0
ms.lasthandoff: 02/24/2017

---
# <a name="ctokenprivileges-class"></a>CTokenPrivileges 类
此类是包装器**TOKEN_PRIVILEGES**结构。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
class CTokenPrivileges
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CTokenPrivileges::CTokenPrivileges](#ctokenprivileges)|构造函数。|  
|[CTokenPrivileges:: ~ CTokenPrivileges](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CTokenPrivileges::Add](#add)|将添加一个或多个权限`CTokenPrivileges`对象。|  
|[CTokenPrivileges::Delete](#delete)|删除从特权`CTokenPrivileges`对象。|  
|[CTokenPrivileges::DeleteAll](#deleteall)|删除所有权限从`CTokenPrivileges`对象。|  
|[CTokenPrivileges::GetCount](#getcount)|返回中的权限条目数`CTokenPrivileges`对象。|  
|[CTokenPrivileges::GetDisplayNames](#getdisplaynames)|检索显示名称中包含的特权`CTokenPrivileges`对象。|  
|[CTokenPrivileges::GetLength](#getlength)|返回以字节为单位保存所需的缓冲区大小**TOKEN_PRIVILEGES**结构由表示`CTokenPrivileges`对象。|  
|[CTokenPrivileges::GetLuidsAndAttributes](#getluidsandattributes)|检索本地唯一标识符 (Luid) 和属性标志从`CTokenPrivileges`对象。|  
|[CTokenPrivileges::GetNamesAndAttributes](#getnamesandattributes)|检索的权限名称和属性标志从`CTokenPrivileges`对象。|  
|[CTokenPrivileges::GetPTOKEN_PRIVILEGES](#getptoken_privileges)|返回一个指向**TOKEN_PRIVILEGES**结构。|  
|[CTokenPrivileges::LookupPrivilege](#lookupprivilege)|检索与给定的特权名称相关联的属性。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CTokenPrivileges::operator const TOKEN_PRIVILEGES *](#operator_const_token_privileges__star)|将为指针值强制转换**TOKEN_PRIVILEGES**结构。|  
|[CTokenPrivileges::operator =](#operator_eq)|赋值运算符。|  
  
## <a name="remarks"></a>备注  
 [访问令牌](http://msdn.microsoft.com/library/windows/desktop/aa374909)是一个对象，描述进程或线程的安全上下文，并分配给每个用户登录到 Windows NT 或 Windows 2000 的系统。  
  
 访问令牌用于描述每个用户授予的各种安全权限。 一项权限由名为本地唯一标识符的 64 位数字组成 ( [LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261)) 和描述符字符串。  
  
 `CTokenPrivileges`类是包装器[TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630)结构，并包含 0 或更多特权。 已删除，或查询使用提供的类方法，可以添加权限。  
  
 在 Windows 访问控制模型的简介，请参阅[访问控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlsecurity.h  
  
##  <a name="add"></a>CTokenPrivileges::Add  
 将添加一个或多个权限`CTokenPrivileges`访问令牌的对象。  
  
```
bool Add(LPCTSTR pszPrivilege, bool bEnable) throw(...);  
void Add(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `pszPrivilege`  
 以 null 结尾的字符串，它指定的权限的名称，如 WINNT 中所定义的指针。H 头文件中。  
  
 `bEnable`  
 如果为 true，则启用特权。 如果为 false，将禁用特权。  
  
 `rPrivileges`  
 引用[TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630)结构。 权限和属性都从该结构中复制并添加到`CTokenPrivileges`对象。  
  
### <a name="return-value"></a>返回值  
 此方法的第一种形式返回权限已成功添加，false 否则如果为 true。  
  
##  <a name="ctokenprivileges"></a>CTokenPrivileges::CTokenPrivileges  
 构造函数。  
  
```
CTokenPrivileges() throw();
CTokenPrivileges(const CTokenPrivileges& rhs) throw(... );  
CTokenPrivileges(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `rhs`  
 `CTokenPrivileges`要分配给新的对象。  
  
 `rPrivileges`  
 [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630)结构以分配给新`CTokenPrivileges`对象。  
  
### <a name="remarks"></a>备注  
 `CTokenPrivileges` （可选） 可以使用创建对象**TOKEN_PRIVILEGES**结构或以前定义`CTokenPrivileges`对象。  
  
##  <a name="dtor"></a>CTokenPrivileges:: ~ CTokenPrivileges  
 析构函数。  
  
```
virtual ~CTokenPrivileges() throw();
```  
  
### <a name="remarks"></a>备注  
 析构函数释放所有已分配的资源。  
  
##  <a name="delete"></a>CTokenPrivileges::Delete  
 删除从特权`CTokenPrivileges`访问令牌的对象。  
  
```
bool Delete(LPCTSTR pszPrivilege) throw();
```  
  
### <a name="parameters"></a>参数  
 `pszPrivilege`  
 以 null 结尾的字符串，它指定的权限的名称，如 WINNT 中所定义的指针。H 头文件中。 例如，此参数可以指定常量 SE_SECURITY_NAME 或其对应的字符串"sesecurityprivilege 权限。"  
  
### <a name="return-value"></a>返回值  
 如果特权否则是已成功删除，则返回 false，则返回 true。  
  
### <a name="remarks"></a>备注  
 此方法可作为一种工具用于创建在 Windows 2000 的受限的令牌。  
  
##  <a name="deleteall"></a>CTokenPrivileges::DeleteAll  
 删除所有权限从`CTokenPrivileges`访问令牌的对象。  
  
```
void DeleteAll() throw();
```  
  
### <a name="remarks"></a>备注  
 删除中包含的所有权限`CTokenPrivileges`访问令牌的对象。  
  
##  <a name="getdisplaynames"></a>CTokenPrivileges::GetDisplayNames  
 检索显示名称中包含的特权`CTokenPrivileges`访问令牌的对象。  
  
```
void GetDisplayNames(CNames* pDisplayNames) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 `pDisplayNames`  
 指向 `CString` 对象的数组的指针。 **Cname**被定义为一个 typedef: **CTokenPrivileges::CAtlArray\<CString&1;>**。  
  
### <a name="remarks"></a>备注  
 该参数`pDisplayNames`是指向数组的指针`CString`对象将接收与中包含的权限相对应的显示名称`CTokenPrivileges`对象。 此方法检索显示名称，名称仅 WINNT 定义权限部分中指定的权限。H。  
  
 此方法检索可显示名称︰ 例如，如果属性名称 SE_REMOTE_SHUTDOWN_NAME，可显示的名称是"从远程系统强制关机"。 若要获取的系统名称，请使用[CTokenPrivileges::GetNamesAndAttributes](#getnamesandattributes)。  
  
##  <a name="getcount"></a>CTokenPrivileges::GetCount  
 返回中的权限条目数`CTokenPrivileges`对象。  
  
```
UINT GetCount() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回的权限包含在数`CTokenPrivileges`对象。  
  
##  <a name="getlength"></a>CTokenPrivileges::GetLength  
 返回的长度`CTokenPrivileges`对象。  
  
```
UINT GetLength() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回包含所需的字节数**TOKEN_PRIVILEGES**结构由表示`CTokenPrivileges`对象，包括所有特权与其包含的项数。  
  
##  <a name="getluidsandattributes"></a>CTokenPrivileges::GetLuidsAndAttributes  
 检索本地唯一标识符 (Luid) 和属性标志从`CTokenPrivileges`对象。  
  
```
void GetLuidsAndAttributes(
    CLUIDArray* pPrivileges,
    CAttributes* pAttributes = NULL) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 `pPrivileges`  
 指向数组的指针[LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261)对象。 **CLUIDArray** typedef 定义为**CAtlArray\<LUID&1;> CLUIDArray**。  
  
 `pAttributes`  
 指向 DWORD 对象的数组的指针。 如果此参数被省略或为 NULL，将不会检索属性。 **CAttributes** typedef 定义为**CAtlArray \<DWORD&1;> CAttributes**。  
  
### <a name="remarks"></a>备注  
 此方法将枚举所有中包含的特权`CTokenPrivileges`访问令牌的对象和单个 Luid 和 （可选） 的特性标志放入数组对象。  
  
##  <a name="getnamesandattributes"></a>CTokenPrivileges::GetNamesAndAttributes  
 检索中的名称和属性标志`CTokenPrivileges`对象。  
  
```
void GetNamesAndAttributes(
    CNames* pNames,
    CAttributes* pAttributes = NULL) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 *pNames*  
 指向数组的指针`CString`对象。 **Cname** typedef 定义为**CAtlArray \<CString&1;> Cname**。  
  
 `pAttributes`  
 指向 DWORD 对象的数组的指针。 如果此参数被省略或为 NULL，将不会检索属性。 **CAttributes** typedef 定义为**CAtlArray \<DWORD&1;> CAttributes**。  
  
### <a name="remarks"></a>备注  
 此方法将枚举所有中包含的特权`CTokenPrivileges`对象，将名称和 （可选） 的特性标志放入数组对象。  
  
 此方法检索属性名称，而不是可显示名称︰ 例如，如果属性名称 SE_REMOTE_SHUTDOWN_NAME，该系统的名称是"SeRemoteShutdownPrivilege。" 若要获取可显示的名称，请使用[CTokenPrivileges::GetDisplayNames](#getdisplaynames)。  
  
##  <a name="getptoken_privileges"></a>CTokenPrivileges::GetPTOKEN_PRIVILEGES  
 返回一个指向**TOKEN_PRIVILEGES**结构。  
  
```
const TOKEN_PRIVILEGES* GetPTOKEN_PRIVILEGES() const throw(...);
```  
  
### <a name="return-value"></a>返回值  
 返回一个指向[TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630)结构。  
  
##  <a name="lookupprivilege"></a>CTokenPrivileges::LookupPrivilege  
 检索与给定的特权名称相关联的属性。  
  
```
bool LookupPrivilege(
    LPCTSTR pszPrivilege,
    DWORD* pdwAttributes = NULL) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 `pszPrivilege`  
 以 null 结尾的字符串，它指定的权限的名称，如 WINNT 中所定义的指针。H 头文件中。 例如，此参数可以指定常量 SE_SECURITY_NAME 或其对应的字符串"sesecurityprivilege 权限。"  
  
 `pdwAttributes`  
 指向接收属性的变量的指针。  
  
### <a name="return-value"></a>返回值  
 如果属性否则是已成功检索，则返回 false，则返回 true。  
  
##  <a name="operator_eq"></a>CTokenPrivileges::operator =  
 赋值运算符。  
  
```
CTokenPrivileges& operator= (const TOKEN_PRIVILEGES& rPrivileges) throw(...);  
CTokenPrivileges& operator= (const CTokenPrivileges& rhs) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `rPrivileges`  
 [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630)结构要分配给`CTokenPrivileges`对象。  
  
 `rhs`  
 `CTokenPrivileges`要分配给该对象。  
  
### <a name="return-value"></a>返回值  
 返回已更新`CTokenPrivileges`对象。  
  
##  <a name="operator_const_token_privileges__star"></a>CTokenPrivileges::operator const TOKEN_PRIVILEGES *  
 将为指针值强制转换**TOKEN_PRIVILEGES**结构。  
  
```  
operator const TOKEN_PRIVILEGES *() const throw(...);
```  
  
### <a name="remarks"></a>备注  
 将为指针值强制转换[TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630)结构。  
  
## <a name="see-also"></a>另请参阅  
 [安全示例](../../visual-cpp-samples.md)   
 [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630)   
 [LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261)   
 [LUID_AND_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379263)   
 [类概述](../../atl/atl-class-overview.md)   
 [安全的全局函数](../../atl/reference/security-global-functions.md)

