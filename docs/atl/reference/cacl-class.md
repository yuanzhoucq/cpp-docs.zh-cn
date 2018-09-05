---
title: CAcl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CAcl class
ms.assetid: 20bcb9af-dc1c-4737-b923-3864776680d6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9f5e71fbf1a24a38b0a18e70ce7d0fa044ad4ec5
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43767873"
---
# <a name="cacl-class"></a>CAcl 类

此类是包装`ACL`（访问控制列表） 结构。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
class CAcl
```

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|[CAcl::CAccessMaskArray](#caccessmaskarray)|ACCESS_MASKs 的数组。|
|[CAcl::CAceFlagArray](#caceflagarray)|一个字节数组。|
|[CAcl::CAceTypeArray](#cacetypearray)|一个字节数组。|

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CAcl::CAcl](#cacl)|构造函数。|
|[CAcl:: ~ CAcl](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CAcl::GetAceCount](#getacecount)|返回数的访问控制项 (ACE) 的对象。|
|[CAcl::GetAclEntries](#getaclentries)|检索从访问控制列表 (ACL) 项`CAcl`对象。|
|[CAcl::GetAclEntry](#getaclentry)|检索有关中的条目的信息的所有`CAcl`对象。|
|[CAcl::GetLength](#getlength)|返回的 acl 的长度。|
|[CAcl::GetPACL](#getpacl)|返回程序包 （指针的 acl）。|
|[CAcl::IsEmpty](#isempty)|测试`CAcl`的条目对象。|
|[CAcl::IsNull](#isnull)|返回的状态`CAcl`对象。|
|[CAcl::RemoveAce](#removeace)|从删除特定的 ACE （访问控制项）`CAcl`对象。|
|[CAcl::RemoveAces](#removeaces)|从删除所有 Ace （访问控制项）`CAcl`适用于给定`CSid`。|
|[CAcl::SetEmpty](#setempty)|标记`CAcl`对象为空。|
|[CAcl::SetNull](#setnull)|标记`CAcl`对象为 NULL。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CAcl::operator const ACL *](#operator_const_acl__star)|强制转换`CAcl`对象传递给`ACL`结构。|
|[CAcl::operator =](#operator_eq)|赋值运算符。|

## <a name="remarks"></a>备注

`ACL`结构是 ACL （访问控制列表） 的标头。 ACL 包括零个或多了按顺序列出[Ace](/windows/desktop/SecAuthZ/access-control-entries) （访问控制项）。 从 0 到编号在 ACL 中的各个 Ace *n-1*，其中*n*是在 ACL 中 Ace 的数量。 在编辑 ACL 时，应用程序是通过其索引指中 ACL 的访问控制项 (ACE)。

有两种 ACL 类型：

- 自定义

- 系统

自由 ACL 控制对象的所有者或任何人都授予对该对象的 WRITE_DAC 访问权限。 它指定访问特定用户和组可以具有的对象。 例如，文件的所有者可以使用任意 ACL 来控制哪些用户和组可以和不能有权访问文件。

对象还可以具有与其关联的系统 ACL 由系统管理员控制窗体中的系统级别的安全信息。 系统 ACL 可以允许系统管理员可以审核访问对象的任何尝试。

有关更多详细信息，请参阅[ACL](/windows/desktop/SecAuthZ/access-control-lists) Windows SDK 中的讨论。

有关 Windows 中的访问控制模型的简介，请参阅[访问控制](/windows/desktop/SecAuthZ/access-control)Windows SDK 中。

## <a name="requirements"></a>要求

**标头：** atlsecurity.h

##  <a name="caccessmaskarray"></a>  CAcl::CAccessMaskArray

ACCESS_MASK 对象的数组。

```
typedef CAtlArray<ACCESS_MASK> CAccessMaskArray;
```

### <a name="remarks"></a>备注

此 typedef 指定可用于将使用的访问权限存储在访问控制项 (Ace) 的数组类型。

##  <a name="caceflagarray"></a>  CAcl::CAceFlagArray

一个字节数组。

```
typedef CAtlArray<BYTE> CAceFlagArray;
```

### <a name="remarks"></a>备注

此 typedef 指定用于定义访问控制项 (ACE) 特定于类型的控制标志的数组类型。 请参阅[ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-_ace_header)可能标志的完整列表的定义。

##  <a name="cacetypearray"></a>  CAcl::CAceTypeArray

一个字节数组。

```
typedef CAtlArray<BYTE> CAceTypeArray;
```

### <a name="remarks"></a>备注

此 typedef 指定用于定义访问控制项 (ACE) 对象，如 ACCESS_ALLOWED_ACE_TYPE 或 ACCESS_DENIED_ACE_TYPE 性质的数组类型。 请参阅[ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-_ace_header)的完整列表的可能的类型定义。

##  <a name="cacl"></a>  CAcl::CAcl

构造函数。

```
CAcl() throw();
CAcl(const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>参数

*rhs*  
一个现有的 `CAcl` 对象。

### <a name="remarks"></a>备注

`CAcl`对象可以根据需要使用创建的现有`CAcl`对象。

##  <a name="dtor"></a>  CAcl:: ~ CAcl

析构函数。

```
virtual ~CAcl() throw();
```

### <a name="remarks"></a>备注

析构函数释放由对象获取任何资源。

##  <a name="getacecount"></a>  CAcl::GetAceCount

返回数的访问控制项 (ACE) 的对象。

```
virtual UINT GetAceCount() const throw() = 0;
```

### <a name="return-value"></a>返回值

返回的 ACE 中的条目数`CAcl`对象。

##  <a name="getaclentries"></a>  CAcl::GetAclEntries

检索从访问控制列表 (ACL) 项`CAcl`对象。

```
void GetAclEntries(
    CSid::CSidArray* pSids,
    CAccessMaskArray* pAccessMasks = NULL,
    CAceTypeArray* pAceTypes = NULL,
    CAceFlagArray* pAceFlags = NULL) const throw(...);
```

### <a name="parameters"></a>参数

*pSids*  
指向数组的指针[CSid](../../atl/reference/csid-class.md)对象。

*pAccessMasks*  
访问掩码中。

*pAceTypes*  
访问控制项 (ACE) 类型。

*pAceFlags*  
ACE 的标志。

### <a name="remarks"></a>备注

此方法填充数组参数中包含的每个 ACE 对象的详细信息`CAcl`对象。 不需要该特定的数组的详细信息时，请使用空值。

每个数组的内容彼此对应，即，第一个元素的`CAccessMaskArray`数组中的第一个元素到对应`CSidArray`数组中，依次类推。

请参阅[ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-_ace_header)有关 ACE 类型和标志的详细信息。

##  <a name="getaclentry"></a>  CAcl::GetAclEntry

检索所有访问控制列表 (ACL) 中的条目有关的信息。

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

*nIndex*  
要检索的 ACL 项的索引。

*pSid*  
[CSid](../../atl/reference/csid-class.md) ACL 条目应用到对象。

*pMask*  
在指定的权限以授予或拒绝访问掩码。

*pType*  
ACE 类型。

*pFlags*  
ACE 的标志。

*pObjectType*  
对象类型。 这将设置为 GUID_NULL，如果该 ACE 中未指定的对象类型，或如果 ACE 不是对象 ACE。

*pInheritedObjectType*  
继承的对象类型。 这将设置为 GUID_NULL，如果该 ACE 中未指定继承的对象类型，或如果 ACE 不是对象 ACE。

### <a name="remarks"></a>备注

此方法将检索所有单独的 ACE，提供的更多消息有关的信息[CAcl::GetAclEntries](#getaclentries)单独提供。

请参阅[ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-_ace_header)有关 ACE 类型和标志的详细信息。

##  <a name="getlength"></a>  CAcl::GetLength

返回的访问控制列表 (ACL) 的长度。

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>返回值

返回以字节为单位的所需的长度存放所需`ACL`结构。

##  <a name="getpacl"></a>  CAcl::GetPACL

返回一个指向访问控制列表 (ACL)。

```
const ACL* GetPACL() const throw(...);
```

### <a name="return-value"></a>返回值

返回一个指向`ACL`结构。

##  <a name="isempty"></a>  CAcl::IsEmpty

测试`CAcl`的条目对象。

```
bool IsEmpty() const throw();
```

### <a name="remarks"></a>备注

返回 true; 否则`CAcl`对象不为 NULL，且不包含任何条目。 如果返回 FALSE`CAcl`对象为 NULL，或包含至少一个条目。

##  <a name="isnull"></a>  CAcl::IsNull

返回的状态`CAcl`对象。

```
bool IsNull() const throw();
```

### <a name="return-value"></a>返回值

返回 true; 否则`CAcl`对象否则是 NULL，则返回 FALSE。

##  <a name="operator_const_acl__star"></a>  CAcl::operator const ACL *

强制转换`CAcl`对象传递给`ACL`（访问控制列表） 结构。

```  
operator const ACL *() const throw(...);
```

### <a name="remarks"></a>备注

返回的地址`ACL`结构。

##  <a name="operator_eq"></a>  CAcl::operator =

赋值运算符。

```
CAcl& operator= (const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>参数

*rhs*  
`CAcl`要分配给现有对象。

### <a name="return-value"></a>返回值

返回对已更新的引用`CAcl`对象。

##  <a name="removeace"></a>  CAcl::RemoveAce

从删除特定的 ACE （访问控制项）`CAcl`对象。

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>参数

*nIndex*  
要移除的 ACE 项的索引。

### <a name="remarks"></a>备注

此方法派生自[CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat)。

##  <a name="removeaces"></a>  CAcl::RemoveAces

从删除 alls Ace （访问控制项）`CAcl`适用于给定`CSid`。

```
bool RemoveAces(const CSid& rSid) throw(...)
```

### <a name="parameters"></a>参数

*rSid*  
对 `CSid` 对象的引用。

##  <a name="setempty"></a>  CAcl::SetEmpty

标记`CAcl`对象为空。

```
void SetEmpty() throw();
```

### <a name="remarks"></a>备注

`CAcl`可以设置为空或为 NULL： 两个状态都不同。

##  <a name="setnull"></a>  CAcl::SetNull

标记`CAcl`对象为 NULL。

```
void SetNull() throw();
```

### <a name="remarks"></a>备注

`CAcl`可以设置为空或为 NULL： 两个状态都不同。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)   
[安全全局函数](../../atl/reference/security-global-functions.md)
