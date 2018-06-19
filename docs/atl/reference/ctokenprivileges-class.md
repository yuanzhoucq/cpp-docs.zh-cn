---
title: CTokenPrivileges 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f6c9886b79739f42329b0f306c8bce6afc2d9fa0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366505"
---
# <a name="ctokenprivileges-class"></a>CTokenPrivileges 类
此类是包装器**TOKEN_PRIVILEGES**结构。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
class CTokenPrivileges
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CTokenPrivileges::CTokenPrivileges](#ctokenprivileges)|构造函数。|  
|[CTokenPrivileges:: ~ CTokenPrivileges](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CTokenPrivileges::Add](#add)|将添加一个或多个权限`CTokenPrivileges`对象。|  
|[CTokenPrivileges::Delete](#delete)|删除从特权`CTokenPrivileges`对象。|  
|[CTokenPrivileges::DeleteAll](#deleteall)|删除所有特权`CTokenPrivileges`对象。|  
|[CTokenPrivileges::GetCount](#getcount)|返回权限中的条目数`CTokenPrivileges`对象。|  
|[CTokenPrivileges::GetDisplayNames](#getdisplaynames)|检索显示名称中包含的特权`CTokenPrivileges`对象。|  
|[CTokenPrivileges::GetLength](#getlength)|返回以字节为单位保存所需的缓冲区大小**TOKEN_PRIVILEGES**结构由表示`CTokenPrivileges`对象。|  
|[CTokenPrivileges::GetLuidsAndAttributes](#getluidsandattributes)|检索本地唯一标识符 (Luid) 和从属性标志`CTokenPrivileges`对象。|  
|[CTokenPrivileges::GetNamesAndAttributes](#getnamesandattributes)|检索的权限名称和从属性标志`CTokenPrivileges`对象。|  
|[CTokenPrivileges::GetPTOKEN_PRIVILEGES](#getptoken_privileges)|返回一个指向**TOKEN_PRIVILEGES**结构。|  
|[CTokenPrivileges::LookupPrivilege](#lookupprivilege)|检索与给定的特权名称关联的属性。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CTokenPrivileges::operator const TOKEN_PRIVILEGES *](#operator_const_token_privileges__star)|将强制转换为指向的值**TOKEN_PRIVILEGES**结构。|  
|[CTokenPrivileges::operator =](#operator_eq)|赋值运算符。|  
  
## <a name="remarks"></a>备注  
 [访问令牌](http://msdn.microsoft.com/library/windows/desktop/aa374909)是介绍进程或线程的安全上下文，并分配给每个用户登录到 Windows 系统的对象。  
  
 访问令牌用于描述每个用户所授予的各种安全权限。 特权包含一个名为本地唯一标识符的 64 位数字 ( [LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261)) 和描述符字符串。  
  
 `CTokenPrivileges`类是包装器[TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630)结构和包含 0 个或更多权限。 已删除，或查询使用提供的类方法，可以添加权限。  
  
 有关 Windows 中的访问控制模型的简介，请参阅[访问控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)Windows SDK 中。  
  
## <a name="requirements"></a>要求  
 **标头：** atlsecurity.h  
  
##  <a name="add"></a>  CTokenPrivileges::Add  
 将添加一个或多个权限`CTokenPrivileges`访问令牌的对象。  
  
```
bool Add(LPCTSTR pszPrivilege, bool bEnable) throw(...);  
void Add(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `pszPrivilege`  
 以 null 结尾的字符串，它指定的权限的名称，WINNT 中定义的指针。H 标头文件。  
  
 `bEnable`  
 如果为 true，则启用特权。 如果为 false，已禁用权限。  
  
 `rPrivileges`  
 引用[TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630)结构。 权限和属性从复制了此结构并添加到`CTokenPrivileges`对象。  
  
### <a name="return-value"></a>返回值  
 此方法的第一种形式返回所拥有的权限已成功添加，false 否则如果为 true。  
  
##  <a name="ctokenprivileges"></a>  CTokenPrivileges::CTokenPrivileges  
 构造函数。  
  
```
CTokenPrivileges() throw();
CTokenPrivileges(const CTokenPrivileges& rhs) throw(... );  
CTokenPrivileges(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `rhs`  
 `CTokenPrivileges`对象要分配给新的对象。  
  
 `rPrivileges`  
 [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630)结构以将分配到新`CTokenPrivileges`对象。  
  
### <a name="remarks"></a>备注  
 `CTokenPrivileges` （可选） 可以使用创建对象**TOKEN_PRIVILEGES**结构或以前定义`CTokenPrivileges`对象。  
  
##  <a name="dtor"></a>  CTokenPrivileges:: ~ CTokenPrivileges  
 析构函数。  
  
```
virtual ~CTokenPrivileges() throw();
```  
  
### <a name="remarks"></a>备注  
 析构函数释放所有已分配的资源。  
  
##  <a name="delete"></a>  CTokenPrivileges::Delete  
 删除从特权`CTokenPrivileges`访问令牌的对象。  
  
```
bool Delete(LPCTSTR pszPrivilege) throw();
```  
  
### <a name="parameters"></a>参数  
 `pszPrivilege`  
 以 null 结尾的字符串，它指定的权限的名称，WINNT 中定义的指针。H 标头文件。 例如，此参数可以指定常量 SE_SECURITY_NAME 或其对应的字符串，"sesecurityprivilege 权限。"  
  
### <a name="return-value"></a>返回值  
 如果特权否则是已成功删除，则返回 false，则返回 true。  
  
### <a name="remarks"></a>备注  
 此方法很有用工具来创建受限制的令牌。  
  
##  <a name="deleteall"></a>  CTokenPrivileges::DeleteAll  
 删除所有特权`CTokenPrivileges`访问令牌的对象。  
  
```
void DeleteAll() throw();
```  
  
### <a name="remarks"></a>备注  
 删除中包含的所有权限`CTokenPrivileges`访问令牌的对象。  
  
##  <a name="getdisplaynames"></a>  CTokenPrivileges::GetDisplayNames  
 检索显示名称中包含的特权`CTokenPrivileges`访问令牌的对象。  
  
```
void GetDisplayNames(CNames* pDisplayNames) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 `pDisplayNames`  
 指向 `CString` 对象的数组的指针。 **Cname**定义为 typedef: **CTokenPrivileges::CAtlArray\<CString >**。  
  
### <a name="remarks"></a>备注  
 参数`pDisplayNames`是指向数组的指针`CString`对象将接收与中包含的权限相对应的显示名称`CTokenPrivileges`对象。 此方法检索 WINNT 的定义权限部分中指定的特权显示名称。H。  
  
 此方法检索可显示名称： 例如，如果属性名称为 SE_REMOTE_SHUTDOWN_NAME，可显示的名称是"从远程系统强制关机"。 若要获取的系统名称，使用[CTokenPrivileges::GetNamesAndAttributes](#getnamesandattributes)。  
  
##  <a name="getcount"></a>  CTokenPrivileges::GetCount  
 返回权限中的条目数`CTokenPrivileges`对象。  
  
```
UINT GetCount() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回的数目中包含的特权`CTokenPrivileges`对象。  
  
##  <a name="getlength"></a>  CTokenPrivileges::GetLength  
 返回的长度`CTokenPrivileges`对象。  
  
```
UINT GetLength() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回保存所需的字节数**TOKEN_PRIVILEGES**结构由表示`CTokenPrivileges`对象，包括所有特权与其包含的项数。  
  
##  <a name="getluidsandattributes"></a>  CTokenPrivileges::GetLuidsAndAttributes  
 检索本地唯一标识符 (Luid) 和从属性标志`CTokenPrivileges`对象。  
  
```
void GetLuidsAndAttributes(
    CLUIDArray* pPrivileges,
    CAttributes* pAttributes = NULL) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 `pPrivileges`  
 指向数组的指针[LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261)对象。 **CLUIDArray** typedef 定义为**CAtlArray\<LUID > CLUIDArray**。  
  
 `pAttributes`  
 指向 DWORD 对象的数组的指针。 如果省略或为 NULL，此参数，不会检索属性。 **CAttributes** typedef 定义为**CAtlArray \<DWORD > CAttributes**。  
  
### <a name="remarks"></a>备注  
 此方法将枚举所有中包含的特权`CTokenPrivileges`访问令牌的对象并将各个 Luid 和 （可选） 的属性标志放入数组对象。  
  
##  <a name="getnamesandattributes"></a>  CTokenPrivileges::GetNamesAndAttributes  
 检索从的名称和属性标志`CTokenPrivileges`对象。  
  
```
void GetNamesAndAttributes(
    CNames* pNames,
    CAttributes* pAttributes = NULL) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 *pNames*  
 指向数组的指针`CString`对象。 **Cname** typedef 定义为**CAtlArray \<CString > Cname**。  
  
 `pAttributes`  
 指向 DWORD 对象的数组的指针。 如果省略或为 NULL，此参数，不会检索属性。 **CAttributes** typedef 定义为**CAtlArray \<DWORD > CAttributes**。  
  
### <a name="remarks"></a>备注  
 此方法将枚举所有中包含的特权`CTokenPrivileges`对象，将名称和 （可选） 的属性标志放入数组对象。  
  
 此方法检索的属性名称，而不是可显示的名称： 例如，如果属性名称，SE_REMOTE_SHUTDOWN_NAME 的系统名称是"SeRemoteShutdownPrivilege。" 若要获取可显示的名称，请使用方法[CTokenPrivileges::GetDisplayNames](#getdisplaynames)。  
  
##  <a name="getptoken_privileges"></a>  CTokenPrivileges::GetPTOKEN_PRIVILEGES  
 返回一个指向**TOKEN_PRIVILEGES**结构。  
  
```
const TOKEN_PRIVILEGES* GetPTOKEN_PRIVILEGES() const throw(...);
```  
  
### <a name="return-value"></a>返回值  
 返回一个指向[TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630)结构。  
  
##  <a name="lookupprivilege"></a>  CTokenPrivileges::LookupPrivilege  
 检索与给定的特权名称关联的属性。  
  
```
bool LookupPrivilege(
    LPCTSTR pszPrivilege,
    DWORD* pdwAttributes = NULL) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 `pszPrivilege`  
 以 null 结尾的字符串，它指定的权限的名称，WINNT 中定义的指针。H 标头文件。 例如，此参数可以指定常量 SE_SECURITY_NAME 或其对应的字符串，"sesecurityprivilege 权限。"  
  
 `pdwAttributes`  
 指向接收属性的变量的指针。  
  
### <a name="return-value"></a>返回值  
 如果该特性否则是已成功检索，则返回 false，则返回 true。  
  
##  <a name="operator_eq"></a>  CTokenPrivileges::operator =  
 赋值运算符。  
  
```
CTokenPrivileges& operator= (const TOKEN_PRIVILEGES& rPrivileges) throw(...);  
CTokenPrivileges& operator= (const CTokenPrivileges& rhs) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `rPrivileges`  
 [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630)结构要分配给`CTokenPrivileges`对象。  
  
 `rhs`  
 `CTokenPrivileges`要分配给对象的对象。  
  
### <a name="return-value"></a>返回值  
 返回已更新`CTokenPrivileges`对象。  
  
##  <a name="operator_const_token_privileges__star"></a>  CTokenPrivileges::operator const TOKEN_PRIVILEGES *  
 将强制转换为指向的值**TOKEN_PRIVILEGES**结构。  
  
```  
operator const TOKEN_PRIVILEGES *() const throw(...);
```  
  
### <a name="remarks"></a>备注  
 将强制转换为指向的值[TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630)结构。  
  
## <a name="see-also"></a>请参阅  
 [安全示例](../../visual-cpp-samples.md)   
 [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630)   
 [LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261)   
 [LUID_AND_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379263)   
 [类概述](../../atl/atl-class-overview.md)   
 [安全全局函数](../../atl/reference/security-global-functions.md)
