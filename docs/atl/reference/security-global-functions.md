---
title: 安全全局函数 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlsecurity/ATL::AtlGetDacl
- atlsecurity/ATL::AtlSetDacl
- atlsecurity/ATL::AtlGetGroupSid
- atlsecurity/ATL::AtlSetGroupSid
- atlsecurity/ATL::AtlGetOwnerSid
- atlsecurity/ATL::AtlSetOwnerSid
- atlsecurity/ATL::AtlGetSacl
- atlsecurity/ATL::AtlSetSacl
- atlsecurity/ATL::AtlGetSecurityDescriptor
dev_langs:
- C++
helpviewer_keywords:
- SIDs [C++], modifying SID objects
- ACL object global functions
- security IDs [C++]
ms.assetid: 6a584bfe-16b7-47f4-8439-9c789c41567a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ad9ad170706b72c9d236e095db0e2b6df00031ff
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365049"
---
# <a name="security-global-functions"></a>安全全局函数
这些函数为修改 SID 和 ACL 对象提供支持。  
  
> [!IMPORTANT]
>  下表中列出的函数不能在 Windows 运行时中执行的应用程序。  
  
|||  
|-|-|  
|[AtlGetDacl](#atlgetdacl)|调用此函数可检索指定对象的自由访问控制列表 (DACL) 信息。|  
|[AtlSetDacl](#atlsetdacl)|调用此函数可设置指定对象的自由访问控制列表 (DACL) 信息。|  
|[AtlGetGroupSid](#atlgetgroupsid)|调用此函数可检索对象的组安全标识符 (SID)。|  
|[AtlSetGroupSid](#atlsetgroupsid)|调用此函数可设置对象的组安全标识符 (SID)。|  
|[AtlGetOwnerSid](#atlgetownersid)|调用此函数可检索对象的所有者安全标识符 (SID)。|  
|[AtlSetOwnerSid](#atlsetownersid)|调用此函数可设置对象的所有者安全标识符 (SID)。|  
|[AtlGetSacl](#atlgetsacl)|调用此函数可检索指定对象的系统访问控制列表 (SACL) 信息。|  
|[AtlSetSacl](#atlsetsacl)|调用此函数可设置指定对象的系统访问控制列表 (SACL) 信息。|  
|[AtlGetSecurityDescriptor](#atlgetsecuritydescriptor)|调用此函数可检索给定对象的安全说明符。|  

## <a name="requirements"></a>要求  
 **标头：** atlsecurity.h 

##  <a name="atlgetdacl"></a>  AtlGetDacl  
 调用此函数可检索指定对象的自由访问控制列表 (DACL) 信息。  
  
> [!IMPORTANT]
>  此函数不能在 Windows 运行时中执行的应用程序。  
  
```
inline bool AtlGetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CDacl* pDacl) throw();
```  
  
### <a name="parameters"></a>参数  
 `hObject`  
 为其检索安全信息的对象的句柄。  
  
 `ObjectType`  
 指定一个介于[SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593)枚举，指示由标识的对象的类型`hObject`参数。  
  
 `pDacl`  
 指向 DACL 对象将包含检索到的安全信息。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
 调试版本中，如果将会出错断言`hObject`或`pDacl`无效。  
  
##  <a name="atlsetdacl"></a>  AtlSetDacl  
 调用此函数可设置指定对象的自由访问控制列表 (DACL) 信息。  
  
> [!IMPORTANT]
>  此函数不能在 Windows 运行时中执行的应用程序。  
  
```
inline bool AtlSetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CDacl& rDacl,
    DWORD dwInheritanceFlowControl = 0) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `hObject`  
 为其设置安全信息的对象的句柄。  
  
 `ObjectType`  
 指定一个介于[SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593)枚举，指示由标识的对象的类型`hObject`参数。  
  
 `rDacl`  
 包含新的安全信息 DACL。  
  
 `dwInheritanceFlowControl`  
 继承流控制。 此值可为 0 （默认值）、 PROTECTED_DACL_SECURITY_INFORMATION 或 UNPROTECTED_DACL_SECURITY_INFORMATION。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
 在调试版本中，如果出现断言错误`hObject`是无效的或者如果`dwInheritanceFlowControl`不是三个允许的值之一。  
### <a name="requirements"></a>要求  
 **标头：** atlsecurity.h 

##  <a name="atlgetgroupsid"></a>  AtlGetGroupSid  
 调用此函数可检索对象的组安全标识符 (SID)。  
  
> [!IMPORTANT]
>  此函数不能在 Windows 运行时中执行的应用程序。  
  
```
inline bool AtlGetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `hObject`  
 要从中检索安全信息的对象的句柄。  
  
 `ObjectType`  
 指定一个介于[SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593)枚举，指示由标识的对象的类型`hObject`参数。  
  
 `pSid`  
 指向`CSid`对象将包含新的安全信息。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  

### <a name="requirements"></a>要求  
 **标头：** atlsecurity.h 

##  <a name="atlsetgroupsid"></a>  AtlSetGroupSid  
 调用此函数可设置对象的组安全标识符 (SID)。  
  
> [!IMPORTANT]
>  此函数不能在 Windows 运行时中执行的应用程序。  
  
```
inline bool AtlSetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `hObject`  
 为其设置安全信息的对象的句柄。  
  
 `ObjectType`  
 指定一个介于[SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593)枚举，指示由标识的对象的类型`hObject`参数。  
  
 `rSid`  
 `CSid`对象，其中包含新的安全信息。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  

### <a name="requirements"></a>要求  
 **标头：** atlsecurity.h 

##  <a name="atlgetownersid"></a>  AtlGetOwnerSid  
 调用此函数可检索对象的所有者安全标识符 (SID)。  
  
> [!IMPORTANT]
>  此函数不能在 Windows 运行时中执行的应用程序。  
  
```
inline bool AtlGetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `hObject`  
 要从中检索安全信息的对象的句柄。  
  
 `ObjectType`  
 指定一个介于[SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593)枚举，指示由标识的对象的类型`hObject`参数。  
  
 `pSid`  
 指向`CSid`对象将包含新的安全信息。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  

### <a name="requirements"></a>要求  
 **标头：** atlsecurity.h 

##  <a name="atlsetownersid"></a>  AtlSetOwnerSid  
 调用此函数可设置对象的所有者安全标识符 (SID)。  
  
> [!IMPORTANT]
>  此函数不能在 Windows 运行时中执行的应用程序。  
  
```
inline bool AtlSetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `hObject`  
 为其设置安全信息的对象的句柄。  
  
 `ObjectType`  
 指定一个介于[SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593)枚举，指示由标识的对象的类型`hObject`参数。  
  
 `rSid`  
 `CSid`对象，其中包含新的安全信息。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  

### <a name="requirements"></a>要求  
 **标头：** atlsecurity.h 

##  <a name="atlgetsacl"></a>  AtlGetSacl  
 调用此函数可检索指定对象的系统访问控制列表 (SACL) 信息。  
  
> [!IMPORTANT]
>  此函数不能在 Windows 运行时中执行的应用程序。  
  
```
inline bool AtlGetSacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSacl* pSacl,
    bool bRequestNeededPrivileges = true) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `hObject`  
 要从中检索安全信息的对象的句柄。  
  
 `ObjectType`  
 指定一个介于[SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593)枚举，指示由标识的对象的类型`hObject`参数。  
  
 `pSacl`  
 指向 SACL 对象将包含检索到的安全信息。  
  
 `bRequestNeededPrivileges`  
 如果为 true，则函数将尝试启用 SE_SECURITY_NAME 特权，并将其还原完成。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
 如果`AtlGetSacl`是多次调用多个不同的对象，它将会更有效地一次调用时使用函数，才能启用 SE_SECURITY_NAME 特权`bRequestNeededPrivileges`设置为 false。  

### <a name="requirements"></a>要求  
 **标头：** atlsecurity.h 

##  <a name="atlsetsacl"></a>  AtlSetSacl  
 调用此函数可设置指定对象的系统访问控制列表 (SACL) 信息。  
  
> [!IMPORTANT]
>  此函数不能在 Windows 运行时中执行的应用程序。  
  
```
inline bool AtlSetSacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSacl& rSacl,
    DWORD dwInheritanceFlowControl = 0,
    bool bRequestNeededPrivileges = true) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `hObject`  
 为其设置安全信息的对象的句柄。  
  
 `ObjectType`  
 指定一个介于[SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593)枚举，指示由标识的对象的类型`hObject`参数。  
  
 *rSacl*  
 SACL 包含新的安全信息。  
  
 `dwInheritanceFlowControl`  
 继承流控制。 此值可为 0 （默认值）、 PROTECTED_SACL_SECURITY_INFORMATION 或 UNPROTECTED_SACL_SECURITY_INFORMATION。  
  
 `bRequestNeededPrivileges`  
 如果为 true，则函数将尝试启用 SE_SECURITY_NAME 特权，并将其还原完成。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
 在调试版本中，如果出现断言错误`hObject`是无效的或者如果`dwInheritanceFlowControl`不是三个允许的值之一。  
  
 如果`AtlSetSacl`是多次调用多个不同的对象，它将会更有效地一次调用时使用函数，才能启用 SE_SECURITY_NAME 特权`bRequestNeededPrivileges`设置为 false。  

### <a name="requirements"></a>要求  
 **标头：** atlsecurity.h 

##  <a name="atlgetsecuritydescriptor"></a>  AtlGetSecurityDescriptor  
 调用此函数可检索给定对象的安全说明符。  
  
> [!IMPORTANT]
>  此函数不能在 Windows 运行时中执行的应用程序。  
  
```
inline bool AtlGetSecurityDescriptor(
    LPCTSTR pszObjectName,
    SE_OBJECT_TYPE ObjectType,
    CSecurityDesc* pSecurityDescriptor,
    SECURITY_INFORMATION requestedInfo = OWNER_SECURITY_INFORMATION |
    GROUP_SECURITY_INFORMATION | DACL_SECURITY_INFORMATION |
    SACL_SECURITY_INFORMATION,
 bool bRequestNeededPrivileges = true) throw(...);
```  
  
### <a name="parameters"></a>参数  
 *pszObjectName*  
 指向以 null 结尾的字符串，指定要从中检索安全信息的对象的名称。  
  
 `ObjectType`  
 指定一个介于[SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593)枚举，指示由标识的对象的类型*pszObjectName*参数。  
  
 *pSecurityDescriptor*  
 接收的请求的安全描述符对象。  
  
 *requestedInfo*  
 一套[SECURITY_INFORMATION](http://msdn.microsoft.com/library/windows/desktop/aa379573)位标志，指示要检索的安全信息的类型。 此参数可以为以下值的组合。  
  
 `bRequestNeededPrivileges`  
 如果为 true，则函数将尝试启用 SE_SECURITY_NAME 特权，并将其还原完成。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
 如果`AtlGetSecurityDescriptor`是多次调用多个不同的对象，它将会更有效地一次调用时使用函数，才能启用 SE_SECURITY_NAME 特权`bRequestNeededPrivileges`设置为 false。  

### <a name="requirements"></a>要求  
 **标头：** atlsecurity.h 
   
## <a name="see-also"></a>请参阅  
 [函数](../../atl/reference/atl-functions.md)
