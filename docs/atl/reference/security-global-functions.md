---
title: 安全全局功能
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
ms.openlocfilehash: 682d44aa80f5d6de521223dfd67db2813cb6738c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326025"
---
# <a name="security-global-functions"></a>安全全局功能

这些函数支持修改 SID 和 ACL 对象。

> [!IMPORTANT]
> 下表中列出的函数不能在 Windows 运行时中执行的应用程序中使用。

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

**标题：** atlsecurity.h

## <a name="atlgetdacl"></a><a name="atlgetdacl"></a>AtlGetDacl

调用此函数可检索指定对象的自由访问控制列表 (DACL) 信息。

> [!IMPORTANT]
> 此函数不能在 Windows 运行时中执行的应用程序中使用。

```
inline bool AtlGetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CDacl* pDacl) throw();
```

### <a name="parameters"></a>参数

*hObject*<br/>
处理要为其检索安全信息的对象。

*对象类型*<br/>
指定[SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type)枚举中的值，该枚举指示*hObject*参数标识的对象类型。

*pDacl*<br/>
指向包含检索的安全信息的 DACL 对象的指针。

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

### <a name="remarks"></a>备注

在调试生成中，如果*hObject*或*pDacl*无效，将发生断言错误。

## <a name="atlsetdacl"></a><a name="atlsetdacl"></a>阿特尔塞特达克

调用此函数可设置指定对象的自由访问控制列表 (DACL) 信息。

> [!IMPORTANT]
> 此函数不能在 Windows 运行时中执行的应用程序中使用。

```
inline bool AtlSetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CDacl& rDacl,
    DWORD dwInheritanceFlowControl = 0) throw(...);
```

### <a name="parameters"></a>参数

*hObject*<br/>
处理为其设置安全信息的对象。

*对象类型*<br/>
指定[SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type)枚举中的值，该枚举指示*hObject*参数标识的对象类型。

*rDacl*<br/>
包含新安全信息的 DACL。

*dw继承流控制*<br/>
继承流控件。 此值可以是 0（默认值）、PROTECTED_DACL_SECURITY_INFORMATION或UNPROTECTED_DACL_SECURITY_INFORMATION。

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

### <a name="remarks"></a>备注

在调试生成中，如果*hObject*无效，或者*dwInheritFlowControl*不是三个允许的值之一，则会发生断言错误。

### <a name="requirements"></a>要求

**标题：** atlsecurity.h

## <a name="atlgetgroupsid"></a><a name="atlgetgroupsid"></a>AtlGetGroupSid

调用此函数可检索对象的组安全标识符 (SID)。

> [!IMPORTANT]
> 此函数不能在 Windows 运行时中执行的应用程序中使用。

```
inline bool AtlGetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```

### <a name="parameters"></a>参数

*hObject*<br/>
处理从中检索安全信息的对象。

*对象类型*<br/>
指定[SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type)枚举中的值，该枚举指示*hObject*参数标识的对象类型。

*pSid*<br/>
指向将包含`CSid`新安全信息的对象的指针。

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

### <a name="requirements"></a>要求

**标题：** atlsecurity.h

## <a name="atlsetgroupsid"></a><a name="atlsetgroupsid"></a>AtlSetGroupSid

调用此函数可设置对象的组安全标识符 (SID)。

> [!IMPORTANT]
> 此函数不能在 Windows 运行时中执行的应用程序中使用。

```
inline bool AtlSetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```

### <a name="parameters"></a>参数

*hObject*<br/>
处理为其设置安全信息的对象。

*对象类型*<br/>
指定[SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type)枚举中的值，该枚举指示*hObject*参数标识的对象类型。

*rSid*<br/>
包含`CSid`新安全信息的对象。

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

### <a name="requirements"></a>要求

**标题：** atlsecurity.h

## <a name="atlgetownersid"></a><a name="atlgetownersid"></a>AtlGetOwnerSid

调用此函数可检索对象的所有者安全标识符 (SID)。

> [!IMPORTANT]
> 此函数不能在 Windows 运行时中执行的应用程序中使用。

```
inline bool AtlGetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```

### <a name="parameters"></a>参数

*hObject*<br/>
处理从中检索安全信息的对象。

*对象类型*<br/>
指定[SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type)枚举中的值，该枚举指示*hObject*参数标识的对象类型。

*pSid*<br/>
指向将包含`CSid`新安全信息的对象的指针。

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

### <a name="requirements"></a>要求

**标题：** atlsecurity.h

## <a name="atlsetownersid"></a><a name="atlsetownersid"></a>AtlSetOwnerSid

调用此函数可设置对象的所有者安全标识符 (SID)。

> [!IMPORTANT]
> 此函数不能在 Windows 运行时中执行的应用程序中使用。

```
inline bool AtlSetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```

### <a name="parameters"></a>参数

*hObject*<br/>
处理为其设置安全信息的对象。

*对象类型*<br/>
指定[SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type)枚举中的值，该枚举指示*hObject*参数标识的对象类型。

*rSid*<br/>
包含`CSid`新安全信息的对象。

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

### <a name="requirements"></a>要求

**标题：** atlsecurity.h

## <a name="atlgetsacl"></a><a name="atlgetsacl"></a>阿特尔茨萨克

调用此函数可检索指定对象的系统访问控制列表 (SACL) 信息。

> [!IMPORTANT]
> 此函数不能在 Windows 运行时中执行的应用程序中使用。

```
inline bool AtlGetSacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSacl* pSacl,
    bool bRequestNeededPrivileges = true) throw(...);
```

### <a name="parameters"></a>参数

*hObject*<br/>
处理从中检索安全信息的对象。

*对象类型*<br/>
指定[SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type)枚举中的值，该枚举指示*hObject*参数标识的对象类型。

*pSacl*<br/>
指向 SACL 对象的指针，该对象将包含检索到的安全信息。

*b 请求需要的权限*<br/>
如果为 true，则函数将尝试启用SE_SECURITY_NAME权限，并在完成后还原它。

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

### <a name="remarks"></a>备注

如果要`AtlGetSacl`在许多不同的对象上多次调用，则在调用函数之前启用SE_SECURITY_NAME权限将更为高效，将*bRequestDSs特权*设置为 false。

### <a name="requirements"></a>要求

**标题：** atlsecurity.h

## <a name="atlsetsacl"></a><a name="atlsetsacl"></a>阿特尔塞特萨克

调用此函数可设置指定对象的系统访问控制列表 (SACL) 信息。

> [!IMPORTANT]
> 此函数不能在 Windows 运行时中执行的应用程序中使用。

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
处理为其设置安全信息的对象。

*对象类型*<br/>
指定[SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type)枚举中的值，该枚举指示*hObject*参数标识的对象类型。

*rSacl*<br/>
包含新安全信息的 SACL。

*dw继承流控制*<br/>
继承流控件。 此值可以是 0（默认值）、PROTECTED_SACL_SECURITY_INFORMATION或UNPROTECTED_SACL_SECURITY_INFORMATION。

*b 请求需要的权限*<br/>
如果为 true，则函数将尝试启用SE_SECURITY_NAME权限，并在完成后还原它。

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

### <a name="remarks"></a>备注

在调试生成中，如果*hObject*无效，或者*dwInheritFlowControl*不是三个允许的值之一，则会发生断言错误。

如果要`AtlSetSacl`在许多不同的对象上多次调用，则在调用函数之前启用SE_SECURITY_NAME权限将更为高效，将*bRequestDSs特权*设置为 false。

### <a name="requirements"></a>要求

**标题：** atlsecurity.h

## <a name="atlgetsecuritydescriptor"></a><a name="atlgetsecuritydescriptor"></a>AtlGet 安全描述器

调用此函数可检索给定对象的安全说明符。

> [!IMPORTANT]
> 此函数不能在 Windows 运行时中执行的应用程序中使用。

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

*pszObject名称*<br/>
指向 null 端接字符串的指针，该字符串指定从中检索安全信息的对象的名称。

*对象类型*<br/>
指定[SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type)枚举中的值，该枚举指示*pszObjectName*参数标识的对象类型。

*p 安全描述器*<br/>
接收请求的安全描述符的对象。

*请求信息*<br/>
一组[SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information)位标志，指示要检索的安全信息的类型。 此参数可以是以下值的组合。

*b 请求需要的权限*<br/>
如果为 true，则函数将尝试启用SE_SECURITY_NAME权限，并在完成后还原它。

### <a name="return-value"></a>返回值

如果成功，则返回 true；如果失败，则返回 false。

### <a name="remarks"></a>备注

如果要`AtlGetSecurityDescriptor`在许多不同的对象上多次调用，则在调用函数之前启用SE_SECURITY_NAME权限将更为高效，将*bRequestDSs特权*设置为 false。

### <a name="requirements"></a>要求

**标题：** atlsecurity.h

## <a name="see-also"></a>另请参阅

[函数](../../atl/reference/atl-functions.md)
