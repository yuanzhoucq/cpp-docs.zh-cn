---
title: CDacl 类
ms.date: 11/04/2016
f1_keywords:
- CDacl
- ATLSECURITY/ATL::CDacl
- ATLSECURITY/ATL::CDacl::CDacl
- ATLSECURITY/ATL::CDacl::AddAllowedAce
- ATLSECURITY/ATL::CDacl::AddDeniedAce
- ATLSECURITY/ATL::CDacl::GetAceCount
- ATLSECURITY/ATL::CDacl::RemoveAce
- ATLSECURITY/ATL::CDacl::RemoveAllAces
helpviewer_keywords:
- CDacl class
ms.assetid: 2dc76616-6362-4967-b6cf-e2d39ca37ddd
ms.openlocfilehash: 713e78635fe261615a82ab518cdb2c68ac0eeed4
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747737"
---
# <a name="cdacl-class"></a>CDacl 类

此类是 DACL（自由访问控制列表）结构的包装器。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
class CDacl : public CAcl
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CDacl：CDacl](#cdacl)|构造函数。|
|[CDacl：*CDacl](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CDacl：：添加允许的Ace](#addallowedace)|向对象添加允许的`CDacl`ACE（访问控制条目）。|
|[CDacl：：添加否认](#adddeniedace)|向对象添加被拒绝的`CDacl`ACE。|
|[CDacl：：获取服务计数](#getacecount)|返回对象中的 ACE（访问控制条目）数`CDacl`。|
|[CDacl：：删除Ace](#removeace)|从`CDacl`对象中删除特定的 ACE（访问控制条目）。|
|[CDacl：：删除所有Aces](#removeallaces)|删除`CDacl`对象中包含的所有 ACA。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CDacl：：运算符 |](#operator_eq)|赋值运算符。|

## <a name="remarks"></a>备注

对象的安全描述符可以包含 DACL。 DACL 包含零个或多个 ACE（访问控制条目），用于标识可以访问该对象的用户和组。 如果 DACL 为空（即它包含零 ACEs），则不会显式授予访问权限，因此隐式拒绝访问。 但是，如果对象的安全描述符没有 DACL，则该对象不受保护，并且每个人都可以完全访问。

若要检索对象的 DACL，您必须是对象的所有者，或具有对该对象的READ_CONTROL访问权限。 要更改对象的 DACL，必须具有对该对象的WRITE_DAC访问权限。

使用提供的类方法从`CDacl`对象创建、添加、删除和删除 A。 另见[AtlGetDacl](security-global-functions.md#atlgetdacl)和[AtlSetDacl](security-global-functions.md#atlsetdacl)。

有关 Windows 中访问控制模型的简介，请参阅 Windows SDK 中[的访问控制](/windows/win32/SecAuthZ/access-control)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CAcl](../../atl/reference/cacl-class.md)

`CDacl`

## <a name="requirements"></a>要求

**标题：** atlsecurity.h

## <a name="cdacladdallowedace"></a><a name="addallowedace"></a>CDacl：：添加允许的Ace

向对象添加允许的`CDacl`ACE（访问控制条目）。

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
[CSid](../../atl/reference/csid-class.md)对象。

*访问掩码*<br/>
指定指定`CSid`对象允许的访问权限的掩码。

*王牌标志*<br/>
控制 ACE 继承的一组位标志。

*pObject类型*<br/>
对象类型。

*p继承对象类型*<br/>
继承的对象类型。

### <a name="return-value"></a>返回值

如果 ACE 添加到对象，`CDacl`则返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

对象`CDacl`包含零个或多个 ACE（访问控制条目），用于标识可以访问该对象的用户和组。 此方法添加了允许访问`CDacl`对象的 ACE。

有关可在`AceFlags`参数中设置的各种标志的说明，请参阅[ACE_HEADER。](/windows/win32/api/winnt/ns-winnt-ace_header)

## <a name="cdacladddeniedace"></a><a name="adddeniedace"></a>CDacl：：添加否认

向对象添加被拒绝的`CDacl`ACE（访问控制条目）。

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
`CSid` 对象。

*访问掩码*<br/>
指定要拒绝指定`CSid`对象的访问权限的掩码。

*王牌标志*<br/>
控制 ACE 继承的一组位标志。 在方法的第一种形式中默认为 0。

*pObject类型*<br/>
对象类型。

*p继承对象类型*<br/>
继承的对象类型。

### <a name="return-value"></a>返回值

如果 ACE 添加到对象，`CDacl`则返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

对象`CDacl`包含零个或多个 ACE（访问控制条目），用于标识可以访问该对象的用户和组。 此方法添加拒绝访问`CDacl`对象的 ACE。

有关可在`AceFlags`参数中设置的各种标志的说明，请参阅[ACE_HEADER。](/windows/win32/api/winnt/ns-winnt-ace_header)

## <a name="cdaclcdacl"></a><a name="cdacl"></a>CDacl：CDacl

构造函数。

```
CDacl (const ACL& rhs) throw(...);
CDacl () throw();
```

### <a name="parameters"></a>参数

rhs**<br/>
现有`ACL`（访问控制列表）结构。

### <a name="remarks"></a>备注

可以使用`CDacl`现有`ACL`结构选择创建对象。 请务必注意，应仅传递 DACL（自由访问控制列表），而不是 SACL（系统访问控制列表）。作为此参数传递。 在调试生成中，传递 SACL 将导致 ASSERT。 在发布版本中，传递 SACL 将导致 ACL 中的 ACE（访问控制条目）被忽略，并且不会发生错误。

## <a name="cdaclcdacl"></a><a name="dtor"></a>CDacl：*CDacl

析构函数。

```
~CDacl () throw();
```

### <a name="remarks"></a>备注

析构函数释放对象获取的任何资源，包括使用[CDacl：：：：removeAllAce](#removeallaces)的所有 ACE（访问控制条目）。

## <a name="cdaclgetacecount"></a><a name="getacecount"></a>CDacl：：获取服务计数

返回对象中的 ACE（访问控制条目）数`CDacl`。

```
UINT GetAceCount() const throw();
```

### <a name="return-value"></a>返回值

返回`CDacl`对象中包含的 ACA 数。

## <a name="cdacloperator-"></a><a name="operator_eq"></a>CDacl：：运算符 |

赋值运算符。

```
CDacl& operator= (const ACL& rhs) throw(...);
```

### <a name="parameters"></a>参数

rhs**<br/>
要分配给现有对象的 ACL（访问控制列表）。

### <a name="return-value"></a>返回值

返回对更新`CDacl`对象的引用。

### <a name="remarks"></a>备注

应确保仅将 DACL（自由访问控制列表）传递给此函数。 将 SACL（系统访问控制列表）传递给此函数将导致调试版本中的 ASSERT，但不会在发布版本中造成错误。

## <a name="cdaclremoveace"></a><a name="removeace"></a>CDacl：：删除Ace

从`CDacl`对象中删除特定的 ACE（访问控制条目）。

```cpp
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要删除的 ACE 条目的索引。

### <a name="remarks"></a>备注

此方法派生自[CAtlarray：：removeAt。](../../atl/reference/catlarray-class.md#removeat)

## <a name="cdaclremoveallaces"></a><a name="removeallaces"></a>CDacl：：删除所有Aces

删除`CDacl`对象中包含的所有 ACE（访问控制条目）。

```cpp
void RemoveAllAces() throw();
```

### <a name="remarks"></a>备注

删除`CDacl`对象`ACE`中的每个（访问控制条目）结构（如果有）。

## <a name="see-also"></a>请参阅

[安全示例](../../overview/visual-cpp-samples.md)<br/>
[CAcl 类](../../atl/reference/cacl-class.md)<br/>
[ACL](/windows/win32/SecAuthZ/access-control-lists)<br/>
[A](/windows/win32/SecAuthZ/access-control-entries)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[安全全局功能](../../atl/reference/security-global-functions.md)
