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
ms.openlocfilehash: 113bcebb7461415590156206ee7aa4c91e0e93d3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330978"
---
# <a name="csecurityattributes-class"></a>CSecurityAttributes 类

此类是安全属性结构的精简包装器。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
class CSecurityAttributes : public SECURITY_ATTRIBUTES
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[安全属性：：安全属性](#csecurityattributes)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[安全属性：：设置](#set)|调用此方法以设置对象的属性`CSecurityAttributes`。|

## <a name="remarks"></a>备注

结构`SECURITY_ATTRIBUTES`包含用于创建对象[的安全描述符](/windows/win32/api/winnt/ns-winnt-security_descriptor)，并指定通过指定此结构检索的句柄是否可继承。

有关 Windows 中访问控制模型的简介，请参阅 Windows SDK 中[的访问控制](/windows/win32/SecAuthZ/access-control)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`SECURITY_ATTRIBUTES`

`CSecurityAttributes`

## <a name="requirements"></a>要求

**标题：** atlsecurity.h

## <a name="csecurityattributescsecurityattributes"></a><a name="csecurityattributes"></a>安全属性：：安全属性

构造函数。

```
CSecurityAttributes() throw();
explicit CSecurityAttributes(const CSecurityDesc& rSecurityDescriptor, bool bInheritsHandle = false) throw(...);
```

### <a name="parameters"></a>参数

*r 安全描述器*<br/>
对安全描述符的引用。

*b继承者*<br/>
指定在创建新进程时是否继承返回的句柄。 如果此成员为 true，则新进程继承该句柄。

## <a name="csecurityattributesset"></a><a name="set"></a>安全属性：：设置

调用此方法以设置对象的属性`CSecurityAttributes`。

```
void Set(const CSecurityDesc& rSecurityDescriptor, bool bInheritHandle = false) throw(...);
```

### <a name="parameters"></a>参数

*r 安全描述器*<br/>
对安全描述符的引用。

*b继承手柄*<br/>
指定在创建新进程时是否继承返回的句柄。 如果此成员为 true，则新进程继承该句柄。

### <a name="remarks"></a>备注

构造函数使用此方法来初始化`CSecurityAttributes`对象。

## <a name="see-also"></a>另请参阅

[安全示例](../../overview/visual-cpp-samples.md)<br/>
[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))<br/>
[安全描述符](/windows/win32/api/winnt/ns-winnt-security_descriptor)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[安全全局功能](../../atl/reference/security-global-functions.md)
