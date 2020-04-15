---
title: CAcl 类
ms.date: 11/04/2016
f1_keywords:
- CAcl
- ATLSECURITY/ATL::CAcl
- ATLSECURITY/ATL::CAcl::CAccessMaskArray
- ATLSECURITY/ATL::CAcl::CAceFlagArray
- ATLSECURITY/ATL::CAcl::CAceTypeArray
- ATLSECURITY/ATL::CAcl::CAcl
- ATLSECURITY/ATL::CAcl::GetAceCount
- ATLSECURITY/ATL::CAcl::GetAclEntries
- ATLSECURITY/ATL::CAcl::GetAclEntry
- ATLSECURITY/ATL::CAcl::GetLength
- ATLSECURITY/ATL::CAcl::GetPACL
- ATLSECURITY/ATL::CAcl::IsEmpty
- ATLSECURITY/ATL::CAcl::IsNull
- ATLSECURITY/ATL::CAcl::RemoveAce
- ATLSECURITY/ATL::CAcl::RemoveAces
- ATLSECURITY/ATL::CAcl::SetEmpty
- ATLSECURITY/ATL::CAcl::SetNull
helpviewer_keywords:
- CAcl class
ms.assetid: 20bcb9af-dc1c-4737-b923-3864776680d6
ms.openlocfilehash: 87bf903220a584798ea59c5f1c701fc35049e901
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321659"
---
# <a name="cacl-class"></a>CAcl 类

此类是`ACL`（访问控制列表）结构的包装器。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
class CAcl
```

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|[CAcl：CAccessMaskarray](#caccessmaskarray)|ACCESS_MASKs数组。|
|[Acl：CAceFlagarray](#caceflagarray)|BYTEs 的数组。|
|[Acl：CAceTypearray](#cacetypearray)|BYTEs 的数组。|

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[Acl：CAcl](#cacl)|构造函数。|
|[CAcl：_CAcl](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[Acl：获取AceCount](#getacecount)|返回访问控制条目 （ACE） 对象的数量。|
|[Acl：获取 Acl](#getaclentries)|从`CAcl`对象检索访问控制列表 （ACL） 条目。|
|[Acl：获取 Aclentry](#getaclentry)|检索有关`CAcl`对象中条目的所有信息。|
|[Acl：获取长度](#getlength)|返回 ACL 的长度。|
|[Acl：GetPACL](#getpacl)|返回 PACL（指向 ACL 的指针）。|
|[Acl：为空](#isempty)|测试`CAcl`对象为条目。|
|[Acl：IsNull](#isnull)|返回`CAcl`对象的状态。|
|[Acl：删除Ace](#removeace)|从`CAcl`对象中删除特定的 ACE（访问控制条目）。|
|[Acl：删除 Ace](#removeaces)|从 中删除应用于给定`CAcl``CSid`的所有 ACE（访问控制条目）。|
|[Acl：设置空](#setempty)|将`CAcl`对象标记为空。|
|[Acl：设置 Null](#setnull)|将`CAcl`对象标记为 NULL。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[Acl：：运算符配置 ACL |](#operator_const_acl__star)|将`CAcl`对象强制转换为`ACL`结构。|
|[CAcl：：运算符 |](#operator_eq)|赋值运算符。|

## <a name="remarks"></a>备注

结构`ACL`是 ACL（访问控制列表）的标头。 ACL 包括零个或多个[ACE（](/windows/win32/SecAuthZ/access-control-entries)访问控制条目）的顺序列表。 ACL 中的单个 ACEs 编号为 0 到*n-1，* 其中*n*是 ACL 中的 ACEs 数。 编辑 ACL 时，应用程序通过索引引用 ACL 中的访问控制条目 （ACE）。

有两种 ACL 类型：

- 酌情

- 系统

可自由访问的 ACL 由对象的所有者或授予WRITE_DAC访问该对象的任何人控制。 它指定特定用户和组对对象的访问。 例如，文件的所有者可以使用任意 ACL 来控制哪些用户和组可以并且不能访问该文件。

对象还可以以系统管理员控制的系统 ACL 的形式与其关联系统级安全信息。 系统 ACL 可以允许系统管理员审核任何访问对象的尝试。

有关详细信息，请参阅 Windows SDK 中的[ACL](/windows/win32/SecAuthZ/access-control-lists)讨论。

有关 Windows 中访问控制模型的简介，请参阅 Windows SDK 中[的访问控制](/windows/win32/SecAuthZ/access-control)。

## <a name="requirements"></a>要求

**标题：** atlsecurity.h

## <a name="caclcaccessmaskarray"></a><a name="caccessmaskarray"></a>CAcl：CAccessMaskarray

ACCESS_MASK对象的数组。

```
typedef CAtlArray<ACCESS_MASK> CAccessMaskArray;
```

### <a name="remarks"></a>备注

此 typedef 指定可用于存储访问控制条目 （ACE） 中使用的访问权限的数组类型。

## <a name="caclcaceflagarray"></a><a name="caceflagarray"></a>Acl：CAceFlagarray

BYTEs 的数组。

```
typedef CAtlArray<BYTE> CAceFlagArray;
```

### <a name="remarks"></a>备注

此 typedef 指定用于定义访问控制条目 （ACE） 类型特定的控制标志的数组类型。 有关可能的标志的完整列表，请参阅[ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header)定义。

## <a name="caclcacetypearray"></a><a name="cacetypearray"></a>Acl：CAceTypearray

BYTEs 的数组。

```
typedef CAtlArray<BYTE> CAceTypeArray;
```

### <a name="remarks"></a>备注

此 typedef 指定用于定义访问控制条目 （ACE） 对象（如ACCESS_ALLOWED_ACE_TYPE或ACCESS_DENIED_ACE_TYPE）性质的数组类型。 有关可能类型的完整列表，请参阅[ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header)定义。

## <a name="caclcacl"></a><a name="cacl"></a>Acl：CAcl

构造函数。

```
CAcl() throw();
CAcl(const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>参数

rhs**<br/>
一个现有的 `CAcl` 对象。

### <a name="remarks"></a>备注

可以使用`CAcl`现有`CAcl`对象选择创建该对象。

## <a name="caclcacl"></a><a name="dtor"></a>CAcl：_CAcl

析构函数。

```
virtual ~CAcl() throw();
```

### <a name="remarks"></a>备注

析构函数释放对象获取的任何资源。

## <a name="caclgetacecount"></a><a name="getacecount"></a>Acl：获取AceCount

返回访问控制条目 （ACE） 对象的数量。

```
virtual UINT GetAceCount() const throw() = 0;
```

### <a name="return-value"></a>返回值

返回`CAcl`对象中的 ACE 条目数。

## <a name="caclgetaclentries"></a><a name="getaclentries"></a>Acl：获取 Acl

从`CAcl`对象检索访问控制列表 （ACL） 条目。

```
void GetAclEntries(
    CSid::CSidArray* pSids,
    CAccessMaskArray* pAccessMasks = NULL,
    CAceTypeArray* pAceTypes = NULL,
    CAceFlagArray* pAceFlags = NULL) const throw(...);
```

### <a name="parameters"></a>参数

*pSids*<br/>
指向[CSid](../../atl/reference/csid-class.md)对象数组的指针。

*pAccess 掩码*<br/>
访问掩码。

*pAce类型*<br/>
访问控制条目 （ACE） 类型。

*pAceFlags*<br/>
ACE 标志。

### <a name="remarks"></a>备注

此方法使用`CAcl`对象中包含的每个 ACE 对象的详细信息填充数组参数。 当不需要该特定数组的详细信息时，请使用 NULL。

每个数组的内容彼此对应，即`CAccessMaskArray`数组的第一个元素对应于`CSidArray`数组中的第一个元素，等等。

有关 ACE 类型和标志的更多详细信息[，请参阅ACE_HEADER。](/windows/win32/api/winnt/ns-winnt-ace_header)

## <a name="caclgetaclentry"></a><a name="getaclentry"></a>Acl：获取 Aclentry

检索有关访问控制列表 （ACL） 中条目的所有信息。

```
void GetAclEntry(
    UINT nIndex,
    CSid* pSid,
    ACCESS_MASK* pMask = NULL,
    BYTE* pType = NULL,
    BYTE* pFlags = NULL,
    GUID* pObjectType = NULL,
    GUID* pInheritedObjectType = NULL) const throw(...);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要检索的 ACL 条目的索引。

*pSid*<br/>
ACL 条目应用于的[CSid](../../atl/reference/csid-class.md)对象。

*pMask*<br/>
指定授予或拒绝访问权限的掩码。

*p类型*<br/>
ACE 类型。

*pFlags*<br/>
ACE 标志。

*pObject类型*<br/>
对象类型。 如果未在 ACE 中指定对象类型，或者 ACE 不是对象 ACE，则将设置为GUID_NULL。

*p继承对象类型*<br/>
继承的对象类型。 如果 ACE 中未指定继承的对象类型，或者 ACE 不是对象 ACE，则将设置为GUID_NULL。

### <a name="remarks"></a>备注

此方法将检索有关单个 ACE 的所有信息，提供比[仅提供 CAcl：getAcl 条目](#getaclentries)提供的信息更多的信息。

有关 ACE 类型和标志的更多详细信息[，请参阅ACE_HEADER。](/windows/win32/api/winnt/ns-winnt-ace_header)

## <a name="caclgetlength"></a><a name="getlength"></a>Acl：获取长度

返回访问控制列表 （ACL） 的长度。

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>返回值

返回保存`ACL`结构所需的长度（以字节为单位）。

## <a name="caclgetpacl"></a><a name="getpacl"></a>Acl：GetPACL

返回指向访问控制列表 （ACL） 的指针。

```
const ACL* GetPACL() const throw(...);
```

### <a name="return-value"></a>返回值

返回指向结构的`ACL`指针。

## <a name="caclisempty"></a><a name="isempty"></a>Acl：为空

测试`CAcl`对象为条目。

```
bool IsEmpty() const throw();
```

### <a name="remarks"></a>备注

如果`CAcl`对象不是 NULL，并且不包含任何条目，则返回 TRUE。 如果`CAcl`对象为 NULL 或至少包含一个条目，则返回 FALSE。

## <a name="caclisnull"></a><a name="isnull"></a>Acl：IsNull

返回`CAcl`对象的状态。

```
bool IsNull() const throw();
```

### <a name="return-value"></a>返回值

如果对象为`CAcl`NULL，则返回 TRUE，否则返回 FALSE。

## <a name="cacloperator-const-acl-"></a><a name="operator_const_acl__star"></a>Acl：：运算符配置 ACL |

将`CAcl`对象强制转换为`ACL`（访问控制列表）结构。

```
operator const ACL *() const throw(...);
```

### <a name="remarks"></a>备注

返回结构的地址`ACL`。

## <a name="cacloperator-"></a><a name="operator_eq"></a>CAcl：：运算符 |

赋值运算符。

```
CAcl& operator= (const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>参数

rhs**<br/>
`CAcl`要分配给现有对象。

### <a name="return-value"></a>返回值

返回对更新`CAcl`对象的引用。

## <a name="caclremoveace"></a><a name="removeace"></a>Acl：删除Ace

从`CAcl`对象中删除特定的 ACE（访问控制条目）。

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要删除的 ACE 条目的索引。

### <a name="remarks"></a>备注

此方法派生自[CAtlarray：：removeAt。](../../atl/reference/catlarray-class.md#removeat)

## <a name="caclremoveaces"></a><a name="removeaces"></a>Acl：删除 Ace

从 中删除应用于给定`CAcl``CSid`的所有 ACE（访问控制条目）。

```
bool RemoveAces(const CSid& rSid) throw(...)
```

### <a name="parameters"></a>参数

*rSid*<br/>
对 `CSid` 对象的引用。

## <a name="caclsetempty"></a><a name="setempty"></a>Acl：设置空

将`CAcl`对象标记为空。

```
void SetEmpty() throw();
```

### <a name="remarks"></a>备注

`CAcl`可以设置为空或 NULL：两种状态是截然不同的。

## <a name="caclsetnull"></a><a name="setnull"></a>Acl：设置 Null

将`CAcl`对象标记为 NULL。

```
void SetNull() throw();
```

### <a name="remarks"></a>备注

`CAcl`可以设置为空或 NULL：两种状态是截然不同的。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)<br/>
[安全全局功能](../../atl/reference/security-global-functions.md)
