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
ms.openlocfilehash: a37ef47a4ea89d9ec24fac417e5b715bd2602fd7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496934"
---
# <a name="cdacl-class"></a>CDacl 类

此类是 DACL (自由访问控制列表) 结构的包装器。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

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
|[CDacl::AddAllowedAce](#addallowedace)|向`CDacl`对象添加一个允许的 ACE (访问控制项)。|
|[CDacl::AddDeniedAce](#adddeniedace)|将拒绝的 ACE 添加到`CDacl`对象。|
|[CDacl::GetAceCount](#getacecount)|返回`CDacl`对象中的 ace (访问控制项) 数。|
|[CDacl::RemoveAce](#removeace)|从`CDacl`对象中移除特定的 ACE (访问控制项)。|
|[CDacl::RemoveAllAces](#removeallaces)|删除`CDacl`对象中包含的所有 ace。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CDacl:: operator =](#operator_eq)|赋值运算符。|

## <a name="remarks"></a>备注

对象的安全描述符可以包含 DACL。 DACL 包含零个或多个 Ace (访问控制项), 这些 Ace 用于标识可以访问对象的用户和组。 如果 DACL 为空 (也就是说, 它包含零个 Ace), 则不会显式授予访问权限, 因此, 访问将被隐式拒绝。 但是, 如果对象的安全描述符没有 DACL, 则该对象是不受保护的, 并且每个人都具有完全访问权限。

若要检索对象的 DACL, 你必须是对象的所有者, 或者具有对象的 READ_CONTROL 访问权限。 若要更改对象的 DACL, 必须对该对象具有 WRITE_DAC 访问权限。

使用提供的类方法创建、添加、删除和删除对象中的`CDacl` ace。 另请参阅[AtlGetDacl](security-global-functions.md#atlgetdacl)和[AtlSetDacl](security-global-functions.md#atlsetdacl)。

有关 Windows 中的访问控制模型的简介, 请参阅 Windows SDK 中的[访问控制](/windows/win32/SecAuthZ/access-control)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CAcl](../../atl/reference/cacl-class.md)

`CDacl`

## <a name="requirements"></a>要求

**标头:** atlsecurity。h

##  <a name="addallowedace"></a>CDacl::AddAllowedAce

向`CDacl`对象添加一个允许的 ACE (访问控制项)。

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

*AccessMask*<br/>
指定要为指定`CSid`的对象允许的访问权限的掩码。

*AceFlags*<br/>
控制 ACE 继承的一组位标志。

*pObjectType*<br/>
对象类型。

*pInheritedObjectType*<br/>
继承的对象类型。

### <a name="return-value"></a>返回值

如果将 ACE 添加到`CDacl`对象中, 则返回 TRUE, 否则返回 FALSE。

### <a name="remarks"></a>备注

`CDacl`对象包含零个或多个 ace (访问控制项), 这些 ace 用于标识可以访问对象的用户和组。 此方法添加一个允许访问`CDacl`对象的 ACE。

有关可在`AceFlags`参数中设置的各种标志的说明, 请参阅 [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header)。

##  <a name="adddeniedace"></a>  CDacl::AddDeniedAce

向`CDacl`对象添加拒绝的 ACE (访问控制项)。

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
为指定`CSid`的对象指定要拒绝的访问权限的掩码。

*AceFlags*<br/>
控制 ACE 继承的一组位标志。 在方法的第一种形式下, 默认值为0。

*pObjectType*<br/>
对象类型。

*pInheritedObjectType*<br/>
继承的对象类型。

### <a name="return-value"></a>返回值

如果将 ACE 添加到`CDacl`对象中, 则返回 TRUE, 否则返回 FALSE。

### <a name="remarks"></a>备注

`CDacl`对象包含零个或多个 ace (访问控制项), 这些 ace 用于标识可以访问对象的用户和组。 此方法添加一个拒绝对对象的`CDacl`访问的 ACE。

有关可在`AceFlags`参数中设置的各种标志的说明, 请参阅 [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header)。

##  <a name="cdacl"></a>  CDacl::CDacl

构造函数。

```
CDacl (const ACL& rhs) throw(...);
CDacl () throw();
```

### <a name="parameters"></a>参数

rhs<br/>
现有`ACL` (访问控制列表) 结构。

### <a name="remarks"></a>备注

可以选择使用现有`ACL`的结构来创建对象。`CDacl` 请务必注意, 只有 DACL (自由访问控制列表), 而不是 SACL (系统访问控制列表) 应作为此参数传递。 在调试版本中, 传递 SACL 将导致断言。 在发布版本中, 传递 SACL 会使 ACL 中的 Ace (访问控制项) 被忽略, 并且不会发生错误。

##  <a name="dtor"></a>  CDacl::~CDacl

析构函数。

```
~CDacl () throw();
```

### <a name="remarks"></a>备注

析构函数释放对象获取的任何资源, 包括使用[CDacl:: RemoveAllAces](#removeallaces)的所有 ace (访问控制项)。

##  <a name="getacecount"></a>  CDacl::GetAceCount

返回`CDacl`对象中的 ace (访问控制项) 数。

```
UINT GetAceCount() const throw();
```

### <a name="return-value"></a>返回值

返回`CDacl`对象中包含的 ace 的数量。

##  <a name="operator_eq"></a>  CDacl::operator =

赋值运算符。

```
CDacl& operator= (const ACL& rhs) throw(...);
```

### <a name="parameters"></a>参数

rhs<br/>
要分配给现有对象的 ACL (访问控制列表)。

### <a name="return-value"></a>返回值

返回对已更新`CDacl`的对象的引用。

### <a name="remarks"></a>备注

你应确保仅向此函数传递 DACL (自由访问控制列表)。 将 SACL (系统访问控制列表) 传递到此函数将导致调试生成中出现断言, 但不会在发布版本中引发错误。

##  <a name="removeace"></a>  CDacl::RemoveAce

从`CDacl`对象中移除特定的 ACE (访问控制项)。

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要移除的 ACE 项的索引。

### <a name="remarks"></a>备注

此方法从[CAtlArray:: RemoveAt](../../atl/reference/catlarray-class.md#removeat)派生。

##  <a name="removeallaces"></a>  CDacl::RemoveAllAces

删除`CDacl`对象中包含的所有 ace (访问控制项)。

```
void RemoveAllAces() throw();
```

### <a name="remarks"></a>备注

删除对象`ACE`中的`CDacl`每个 (访问控制项) 结构 (如果有)。

## <a name="see-also"></a>请参阅

[安全示例](../../overview/visual-cpp-samples.md)<br/>
[CAcl 类](../../atl/reference/cacl-class.md)<br/>
[Acl](/windows/win32/SecAuthZ/access-control-lists)<br/>
[Ace](/windows/win32/SecAuthZ/access-control-entries)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[安全全局函数](../../atl/reference/security-global-functions.md)
