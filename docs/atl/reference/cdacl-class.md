---
title: CDacl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CDacl
- ATLSECURITY/ATL::CDacl
- ATLSECURITY/ATL::CDacl::CDacl
- ATLSECURITY/ATL::CDacl::AddAllowedAce
- ATLSECURITY/ATL::CDacl::AddDeniedAce
- ATLSECURITY/ATL::CDacl::GetAceCount
- ATLSECURITY/ATL::CDacl::RemoveAce
- ATLSECURITY/ATL::CDacl::RemoveAllAces
dev_langs:
- C++
helpviewer_keywords:
- CDacl class
ms.assetid: 2dc76616-6362-4967-b6cf-e2d39ca37ddd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f3d0b817fc080ff81e11e1789387f50cb3e871e5
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50076004"
---
# <a name="cdacl-class"></a>CDacl 类

此类是 DACL （自由访问控制列表） 结构的包装器。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
class CDacl : public CAcl
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CDacl::CDacl](#cdacl)|构造函数。|
|[CDacl::~CDacl](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CDacl::AddAllowedAce](#addallowedace)|将允许的 ACE （访问控制项） 添加到`CDacl`对象。|
|[CDacl::AddDeniedAce](#adddeniedace)|将添加到一个拒绝的 ACE`CDacl`对象。|
|[CDacl::GetAceCount](#getacecount)|在返回 Ace （访问控制项） 的数量`CDacl`对象。|
|[CDacl::RemoveAce](#removeace)|从删除特定的 ACE （访问控制项）`CDacl`对象。|
|[CDacl::RemoveAllAces](#removeallaces)|移除所有中包含的 Ace`CDacl`对象。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CDacl::operator =](#operator_eq)|赋值运算符。|

## <a name="remarks"></a>备注

对象的安全描述符可以包含 DACL。 DACL 包含标识用户和组有权访问该对象零个或多个 Ace （访问控制项）。 如果是空的 DACL （即，它包含零个 Ace），显式授予无访问权限，所以隐式拒绝访问。 但是，如果对象的安全描述符不具有 DACL，该对象是不受保护，每个人都有完全访问权限。

若要检索对象的 DACL，必须是对象的所有者或具有 READ_CONTROL 访问对象。 若要更改对象的 DACL，必须具有对对象的 WRITE_DAC 访问。

使用类方法提供用于创建、 添加、 删除和删除 Ace 从`CDacl`对象。 另请参阅[AtlGetDacl](security-global-functions.md#atlgetdacl)并[AtlSetDacl](security-global-functions.md#atlsetdacl)。

有关 Windows 中的访问控制模型的简介，请参阅[访问控制](/windows/desktop/SecAuthZ/access-control)Windows SDK 中。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CAcl](../../atl/reference/cacl-class.md)

`CDacl`

## <a name="requirements"></a>要求

**标头：** atlsecurity.h

##  <a name="addallowedace"></a>  CDacl::AddAllowedAce

将允许的 ACE （访问控制项） 添加到`CDacl`对象。

```
bool AddAllowedAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags = 0) throw(...);

bool AddAllowedAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags,
    const GUID* pObjectType,
    const GUID* pInheritedObjectType) throw(...);
```

### <a name="parameters"></a>参数

*rSid*<br/>
一个[CSid](../../atl/reference/csid-class.md)对象。

*AccessMask*<br/>
指定允许的访问权限的掩码指定`CSid`对象。

*AceFlags*<br/>
一组位标志，用于控制 ACE 继承。

*pObjectType*<br/>
对象类型。

*pInheritedObjectType*<br/>
继承的对象类型。

### <a name="return-value"></a>返回值

如果 ACE 添加到，则返回 TRUE`CDacl`对象，则返回 FALSE 失败。

### <a name="remarks"></a>备注

一个`CDacl`对象包含零个或多个 Ace （访问控制项） 的标识的用户和组有权访问该对象。 此方法将添加一个允许访问的 ACE`CDacl`对象。

请参阅[ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-_ace_header)有关的各种标志可设置中的说明`AceFlags`参数。

##  <a name="adddeniedace"></a>  CDacl::AddDeniedAce

将拒绝的 ACE （访问控制项） 添加到`CDacl`对象。

```
bool AddDeniedAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags = 0) throw(...);

bool AddDeniedAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags,
    const GUID* pObjectType,
    const GUID* pInheritedObjectType) throw(...);
```

### <a name="parameters"></a>参数

*rSid*<br/>
一个 `CSid` 对象。

*AccessMask*<br/>
指定要对其拒绝访问权限的掩码指定`CSid`对象。

*AceFlags*<br/>
一组位标志，用于控制 ACE 继承。 默认值为 0 的方法的第一个窗体中。

*pObjectType*<br/>
对象类型。

*pInheritedObjectType*<br/>
继承的对象类型。

### <a name="return-value"></a>返回值

如果 ACE 添加到，则返回 TRUE`CDacl`对象，则返回 FALSE 失败。

### <a name="remarks"></a>备注

一个`CDacl`对象包含零个或多个 Ace （访问控制项） 的标识的用户和组有权访问该对象。 此方法将添加一个拒绝访问的 ACE`CDacl`对象。

请参阅[ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-_ace_header)有关的各种标志可设置中的说明`AceFlags`参数。

##  <a name="cdacl"></a>  CDacl::CDacl

构造函数。

```
CDacl (const ACL& rhs) throw(...);
CDacl () throw();
```

### <a name="parameters"></a>参数

*rhs*<br/>
将现有`ACL`（访问控制列表） 结构。

### <a name="remarks"></a>备注

`CDacl`对象可以根据需要使用创建的现有`ACL`结构。 务必要注意，只有 DACL （自由访问控制列表） 和 SACL （系统访问控制列表），不应作为此参数进行传递。 在调试版本中，传递 SACL 将导致断言。 发布版本中传递 SACL 将导致 （访问控制项） 的 Ace 的 ACL 被忽略，不会发生错误。

##  <a name="dtor"></a>  CDacl::~CDacl

析构函数。

```
~CDacl () throw();
```

### <a name="remarks"></a>备注

析构函数释放获取的对象，包括所有 Ace （访问控制项） 的使用的任何资源[CDacl::RemoveAllAces](#removeallaces)。

##  <a name="getacecount"></a>  CDacl::GetAceCount

在返回 Ace （访问控制项） 的数量`CDacl`对象。

```
UINT GetAceCount() const throw();
```

### <a name="return-value"></a>返回值

返回中包含的 Ace 的数量`CDacl`对象。

##  <a name="operator_eq"></a>  CDacl::operator =

赋值运算符。

```
CDacl& operator= (const ACL& rhs) throw(...);
```

### <a name="parameters"></a>参数

*rhs*<br/>
删除的 ACL （访问控制列表） 要分配给现有对象。

### <a name="return-value"></a>返回值

返回对已更新的引用`CDacl`对象。

### <a name="remarks"></a>备注

您应该确保你仅向此函数传递 DACL （自由访问控制列表）。 传入 SACL （系统访问控制列表） 对此函数将导致在调试版本中的断言，但将导致在发布版本中的任何错误。

##  <a name="removeace"></a>  CDacl::RemoveAce

从删除特定的 ACE （访问控制项）`CDacl`对象。

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要移除的 ACE 项的索引。

### <a name="remarks"></a>备注

此方法派生自[CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat)。

##  <a name="removeallaces"></a>  CDacl::RemoveAllAces

移除所有 Ace （访问控制项） 中包含`CDacl`对象。

```
void RemoveAllAces() throw();
```

### <a name="remarks"></a>备注

删除每个`ACE`（访问控制项） 结构 （如果有） 中的`CDacl`对象。

## <a name="see-also"></a>请参阅

[安全示例](../../visual-cpp-samples.md)<br/>
[CAcl 类](../../atl/reference/cacl-class.md)<br/>
[Acl](/windows/desktop/SecAuthZ/access-control-lists)<br/>
[Ace](/windows/desktop/SecAuthZ/access-control-entries)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[安全全局函数](../../atl/reference/security-global-functions.md)
