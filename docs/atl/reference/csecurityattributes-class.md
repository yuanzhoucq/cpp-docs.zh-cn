---
title: CSecurityAttributes 类
ms.date: 11/04/2016
f1_keywords:
- CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::Set
helpviewer_keywords:
- CSecurityAttributes class
ms.assetid: a094880c-52e1-4a28-97ff-752d5869908e
ms.openlocfilehash: 66188a2c944379cfae813220937ac1e7e98fb41d
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58768336"
---
# <a name="csecurityattributes-class"></a>CSecurityAttributes 类

此类是安全的属性结构的精简包装。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
class CSecurityAttributes : public SECURITY_ATTRIBUTES
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CSecurityAttributes::CSecurityAttributes](#csecurityattributes)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CSecurityAttributes::Set](#set)|调用此方法以设置的属性`CSecurityAttributes`对象。|

## <a name="remarks"></a>备注

`SECURITY_ATTRIBUTES`结构包含[安全描述符](/windows/desktop/api/winnt/ns-winnt-_security_descriptor)用于创建对象并指定检索通过指定此结构的句柄是否可继承。

有关 Windows 中的访问控制模型的简介，请参阅[访问控制](/windows/desktop/SecAuthZ/access-control)Windows SDK 中。

## <a name="inheritance-hierarchy"></a>继承层次结构

`SECURITY_ATTRIBUTES`

`CSecurityAttributes`

## <a name="requirements"></a>要求

**标头：** atlsecurity.h

##  <a name="csecurityattributes"></a>  CSecurityAttributes::CSecurityAttributes

构造函数。

```
CSecurityAttributes() throw();
explicit CSecurityAttributes(const CSecurityDesc& rSecurityDescriptor, bool bInheritsHandle = false) throw(...);
```

### <a name="parameters"></a>参数

*rSecurityDescriptor*<br/>
对安全描述符的引用。

*bInheritsHandle*<br/>
指定在创建新进程时是否继承返回的句柄。 如果此成员为 true，则新进程继承该句柄。

##  <a name="set"></a>  CSecurityAttributes::Set

调用此方法以设置的属性`CSecurityAttributes`对象。

```
void Set(const CSecurityDesc& rSecurityDescriptor, bool bInheritHandle = false) throw(...);
```

### <a name="parameters"></a>参数

*rSecurityDescriptor*<br/>
对安全描述符的引用。

*bInheritHandle*<br/>
指定在创建新进程时是否继承返回的句柄。 如果此成员为 true，则新进程继承该句柄。

### <a name="remarks"></a>备注

构造函数使用此方法以初始化`CSecurityAttributes`对象。

## <a name="see-also"></a>请参阅

[安全示例](../../overview/visual-cpp-samples.md)<br/>
[SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560)<br/>
[安全描述符](/windows/desktop/api/winnt/ns-winnt-_security_descriptor)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[安全全局函数](../../atl/reference/security-global-functions.md)
