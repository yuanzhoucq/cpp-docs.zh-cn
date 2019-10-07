---
title: 安全全局函数
ms.date: 11/04/2016
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
helpviewer_keywords:
- SIDs [C++], modifying SID objects
- ACL object global functions
- security IDs [C++]
ms.assetid: 6a584bfe-16b7-47f4-8439-9c789c41567a
ms.openlocfilehash: 5f3c0464b239f4500d416b80ae4fdf06c2dc386f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495174"
---
# <a name="security-global-functions"></a>安全全局函数

这些函数为修改 SID 和 ACL 对象提供支持。

> [!IMPORTANT]
>  下表中列出的函数不能用于在 Windows 运行时中执行的应用程序。

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

**标头:** atlsecurity。h

##  <a name="atlgetdacl"></a>  AtlGetDacl

调用此函数可检索指定对象的自由访问控制列表 (DACL) 信息。

> [!IMPORTANT]
>  此函数不能用于在 Windows 运行时中执行的应用程序。

```
inline bool AtlGetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CDacl* pDacl) throw();
```

### <a name="parameters"></a>参数

*hObject*<br/>
要检索其安全信息的对象的句柄。

*ObjectType*<br/>
指定[SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type)枚举中的一个值, 该值指示由*hObject*参数标识的对象的类型。

*pDacl*<br/>
指向包含检索到的安全信息的 DACL 对象的指针。

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

### <a name="remarks"></a>备注

在调试版本中, 如果*hObject*或*pDacl*无效, 则会发生断言错误。

##  <a name="atlsetdacl"></a>  AtlSetDacl

调用此函数可设置指定对象的自由访问控制列表 (DACL) 信息。

> [!IMPORTANT]
>  此函数不能用于在 Windows 运行时中执行的应用程序。

```
inline bool AtlSetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CDacl& rDacl,
    DWORD dwInheritanceFlowControl = 0) throw(...);
```

### <a name="parameters"></a>参数

*hObject*<br/>
要为其设置安全信息的对象的句柄。

*ObjectType*<br/>
指定[SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type)枚举中的一个值, 该值指示由*hObject*参数标识的对象的类型。

*rDacl*<br/>
包含新安全信息的 DACL。

*dwInheritanceFlowControl*<br/>
继承流控制。 此值可以是 0 (默认值)、PROTECTED_DACL_SECURITY_INFORMATION 或 UNPROTECTED_DACL_SECURITY_INFORMATION。

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

### <a name="remarks"></a>备注

在调试版本中, 如果*hObject*无效或*dwInheritanceFlowControl*不是三个允许的值之一, 则将发生断言错误。
### <a name="requirements"></a>要求

**标头:** atlsecurity。h

##  <a name="atlgetgroupsid"></a>  AtlGetGroupSid

调用此函数可检索对象的组安全标识符 (SID)。

> [!IMPORTANT]
>  此函数不能用于在 Windows 运行时中执行的应用程序。

```
inline bool AtlGetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```

### <a name="parameters"></a>参数

*hObject*<br/>
要从中检索安全信息的对象的句柄。

*ObjectType*<br/>
指定[SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type)枚举中的一个值, 该值指示由*hObject*参数标识的对象的类型。

*pSid*<br/>
指向`CSid`对象的指针, 该对象将包含新的安全信息。

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

### <a name="requirements"></a>要求

**标头:** atlsecurity。h

##  <a name="atlsetgroupsid"></a>  AtlSetGroupSid

调用此函数可设置对象的组安全标识符 (SID)。

> [!IMPORTANT]
>  此函数不能用于在 Windows 运行时中执行的应用程序。

```
inline bool AtlSetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```

### <a name="parameters"></a>参数

*hObject*<br/>
要为其设置安全信息的对象的句柄。

*ObjectType*<br/>
指定[SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type)枚举中的一个值, 该值指示由*hObject*参数标识的对象的类型。

*rSid*<br/>
包含`CSid`新安全信息的对象。

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

### <a name="requirements"></a>要求

**标头:** atlsecurity。h

##  <a name="atlgetownersid"></a>  AtlGetOwnerSid

调用此函数可检索对象的所有者安全标识符 (SID)。

> [!IMPORTANT]
>  此函数不能用于在 Windows 运行时中执行的应用程序。

```
inline bool AtlGetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```

### <a name="parameters"></a>参数

*hObject*<br/>
要从中检索安全信息的对象的句柄。

*ObjectType*<br/>
指定[SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type)枚举中的一个值, 该值指示由*hObject*参数标识的对象的类型。

*pSid*<br/>
指向`CSid`对象的指针, 该对象将包含新的安全信息。

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

### <a name="requirements"></a>要求

**标头:** atlsecurity。h

##  <a name="atlsetownersid"></a>  AtlSetOwnerSid

调用此函数可设置对象的所有者安全标识符 (SID)。

> [!IMPORTANT]
>  此函数不能用于在 Windows 运行时中执行的应用程序。

```
inline bool AtlSetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```

### <a name="parameters"></a>参数

*hObject*<br/>
要为其设置安全信息的对象的句柄。

*ObjectType*<br/>
指定[SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type)枚举中的一个值, 该值指示由*hObject*参数标识的对象的类型。

*rSid*<br/>
包含`CSid`新安全信息的对象。

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

### <a name="requirements"></a>要求

**标头:** atlsecurity。h

##  <a name="atlgetsacl"></a>  AtlGetSacl

调用此函数可检索指定对象的系统访问控制列表 (SACL) 信息。

> [!IMPORTANT]
>  此函数不能用于在 Windows 运行时中执行的应用程序。

```
inline bool AtlGetSacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSacl* pSacl,
    bool bRequestNeededPrivileges = true) throw(...);
```

### <a name="parameters"></a>参数

*hObject*<br/>
要从中检索安全信息的对象的句柄。

*ObjectType*<br/>
指定[SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type)枚举中的一个值, 该值指示由*hObject*参数标识的对象的类型。

*pSacl*<br/>
指向将包含检索到的安全信息的 SACL 对象的指针。

*bRequestNeededPrivileges*<br/>
如果为 true, 则函数将尝试启用 SE_SECURITY_NAME 权限, 并在完成时还原。

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

### <a name="remarks"></a>备注

如果`AtlGetSacl`要在多个不同的对象上调用多次, 则在调用函数之前启用 SE_SECURITY_NAME 权限会更有效, 并将*bRequestNeededPrivileges*设置为 false。

### <a name="requirements"></a>要求

**标头:** atlsecurity。h

##  <a name="atlsetsacl"></a>  AtlSetSacl

调用此函数可设置指定对象的系统访问控制列表 (SACL) 信息。

> [!IMPORTANT]
>  此函数不能用于在 Windows 运行时中执行的应用程序。

```
inline bool AtlSetSacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSacl& rSacl,
    DWORD dwInheritanceFlowControl = 0,
    bool bRequestNeededPrivileges = true) throw(...);
```

### <a name="parameters"></a>参数

*hObject*<br/>
要为其设置安全信息的对象的句柄。

*ObjectType*<br/>
指定[SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type)枚举中的一个值, 该值指示由*hObject*参数标识的对象的类型。

*rSacl*<br/>
包含新安全信息的 SACL。

*dwInheritanceFlowControl*<br/>
继承流控制。 此值可以是 0 (默认值)、PROTECTED_SACL_SECURITY_INFORMATION 或 UNPROTECTED_SACL_SECURITY_INFORMATION。

*bRequestNeededPrivileges*<br/>
如果为 true, 则函数将尝试启用 SE_SECURITY_NAME 权限, 并在完成时还原。

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

### <a name="remarks"></a>备注

在调试版本中, 如果*hObject*无效或*dwInheritanceFlowControl*不是三个允许的值之一, 则将发生断言错误。

如果`AtlSetSacl`要在多个不同的对象上调用多次, 则在调用函数之前启用 SE_SECURITY_NAME 权限会更有效, 并将*bRequestNeededPrivileges*设置为 false。

### <a name="requirements"></a>要求

**标头:** atlsecurity。h

##  <a name="atlgetsecuritydescriptor"></a>  AtlGetSecurityDescriptor

调用此函数可检索给定对象的安全说明符。

> [!IMPORTANT]
>  此函数不能用于在 Windows 运行时中执行的应用程序。

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

*pszObjectName*<br/>
指向以 null 结尾的字符串的指针, 该字符串指定要从中检索安全信息的对象的名称。

*ObjectType*<br/>
指定[SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type)枚举中的一个值, 该值指示由*pszObjectName*参数标识的对象的类型。

*pSecurityDescriptor*<br/>
接收请求的安全描述符的对象。

*requestedInfo*<br/>
一组[SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information)位标志, 用于指示要检索的安全信息的类型。 此参数可以是下列值的组合。

*bRequestNeededPrivileges*<br/>
如果为 true, 则函数将尝试启用 SE_SECURITY_NAME 权限, 并在完成时还原。

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

### <a name="remarks"></a>备注

如果`AtlGetSecurityDescriptor`要在多个不同的对象上调用多次, 则在调用函数之前启用 SE_SECURITY_NAME 权限会更有效, 并将*bRequestNeededPrivileges*设置为 false。

### <a name="requirements"></a>要求

**标头:** atlsecurity。h

## <a name="see-also"></a>请参阅

[函数](../../atl/reference/atl-functions.md)
