---
title: CSimpleMap 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSimpleMap
- ATLSIMPCOLL/ATL::CSimpleMap
- ATLSIMPCOLL/ATL::CSimpleMap::_ArrayElementType
- ATLSIMPCOLL/ATL::CSimpleMap::_ArrayKeyType
- ATLSIMPCOLL/ATL::CSimpleMap::CSimpleMap
- ATLSIMPCOLL/ATL::CSimpleMap::Add
- ATLSIMPCOLL/ATL::CSimpleMap::FindKey
- ATLSIMPCOLL/ATL::CSimpleMap::FindVal
- ATLSIMPCOLL/ATL::CSimpleMap::GetKeyAt
- ATLSIMPCOLL/ATL::CSimpleMap::GetSize
- ATLSIMPCOLL/ATL::CSimpleMap::GetValueAt
- ATLSIMPCOLL/ATL::CSimpleMap::Lookup
- ATLSIMPCOLL/ATL::CSimpleMap::Remove
- ATLSIMPCOLL/ATL::CSimpleMap::RemoveAll
- ATLSIMPCOLL/ATL::CSimpleMap::RemoveAt
- ATLSIMPCOLL/ATL::CSimpleMap::ReverseLookup
- ATLSIMPCOLL/ATL::CSimpleMap::SetAt
- ATLSIMPCOLL/ATL::CSimpleMap::SetAtIndex
dev_langs:
- C++
helpviewer_keywords:
- CSimpleMap class
ms.assetid: 61b06eb4-ae73-44b0-a305-0afb5a33e8b1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4fb9985314a71c2da6eed50fd1ba3a486b0cff73
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50059514"
---
# <a name="csimplemap-class"></a>CSimpleMap 类

此类简单映射数组提供支持。

## <a name="syntax"></a>语法

```
template <class TKey, class TVal, class TEqual = CSimpleMapEqualHelper<TKey, TVal>>
class CSimpleMap
```

#### <a name="parameters"></a>参数

*TKey*<br/>
Key 元素类型。

*TVal*<br/>
值元素类型。

*TEqual*<br/>
特征对象，用于定义类型的元素的相等性测试`T`。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|[CSimpleMap::_ArrayElementType](#_arrayelementtype)|值类型的 Typedef。|
|[CSimpleMap::_ArrayKeyType](#_arraykeytype)|密钥类型的 Typedef。|

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CSimpleMap::CSimpleMap](#csimplemap)|构造函数。|
|[CSimpleMap:: ~ CSimpleMap](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CSimpleMap::Add](#add)|将键和关联的值添加到映射的数组中。|
|[CSimpleMap::FindKey](#findkey)|查找特定的键。|
|[CSimpleMap::FindVal](#findval)|查找特定值。|
|[CSimpleMap::GetKeyAt](#getkeyat)|检索指定的键。|
|[CSimpleMap::GetSize](#getsize)|映射数组中返回条目的数。|
|[CSimpleMap::GetValueAt](#getvalueat)|检索指定的值。|
|[CSimpleMap::Lookup](#lookup)|返回与给定键关联的值。|
|[CSimpleMap::Remove](#remove)|删除密钥和匹配的值。|
|[CSimpleMap::RemoveAll](#removeall)|移除所有键和值。|
|[CSimpleMap::RemoveAt](#removeat)|移除特定键和匹配的值。|
|[CSimpleMap::ReverseLookup](#reverselookup)|返回与给定的值关联的键。|
|[CSimpleMap::SetAt](#setat)|设置与给定键关联的值。|
|[CSimpleMap::SetAtIndex](#setatindex)|设置特定键和值。|

## <a name="remarks"></a>备注

`CSimpleMap` 为任何给定类型的一个简单的映射数组提供支持`T`，管理的关键元素和相关联的值的无序的数组。

将参数`TEqual`提供了一种定义类型的两个元素相等性比较函数`T`。 通过创建类类似于[CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md)，可以更改任何给定数组相等性测试的行为。 例如，在处理时的指针的数组，它可能很适合用于定义为具体取决于指针引用的值的相等性。 默认实现利用**operator==()**。

这两`CSimpleMap`并[CSimpleArray](../../atl/reference/csimplearray-class.md)为释放与上一 ATL 的兼容性，并通过提供更完整且有效的集合实现提供[CAtlArray](../../atl/reference/catlarray-class.md)并[CAtlMap](../../atl/reference/catlmap-class.md)。

与 ATL 和 MFC 中的其他映射集合，此类实现使用简单的数组，并查找搜索需要的线性搜索。 `CAtlMap` 该数组包含大量元素时，应使用。

## <a name="requirements"></a>要求

**标头：** atlsimpcoll.h

## <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#91](../../atl/codesnippet/cpp/csimplemap-class_1.cpp)]

##  <a name="add"></a>  CSimpleMap::Add

将键和关联的值添加到映射的数组中。

```
BOOL Add(const TKey& key, const TVal& val);
```

### <a name="parameters"></a>参数

*key*<br/>
键。

*val*<br/>
相关联的值。

### <a name="return-value"></a>返回值

如果键和值是已成功添加，则返回 FALSE 否则，则返回 TRUE。

### <a name="remarks"></a>备注

每个键 / 值对添加映射数组内存被释放并重新分配，从而确保每个数据始终连续存储的原因。 也就是说，第二个关键元素始终直接遵循在内存中的第一个关键元素，依此类推。

##  <a name="_arrayelementtype"></a>  CSimpleMap::_ArrayElementType

密钥类型的 typedef。

```
typedef TVal _ArrayElementType;
```

##  <a name="_arraykeytype"></a>  CSimpleMap::_ArrayKeyType

值类型的 typedef。

```
typedef TKey _ArrayKeyType;
```

##  <a name="csimplemap"></a>  CSimpleMap::CSimpleMap

构造函数。

```
CSimpleMap();
```

### <a name="remarks"></a>备注

初始化数据成员。

##  <a name="dtor"></a>  CSimpleMap:: ~ CSimpleMap

析构函数。

```
~CSimpleMap();
```

### <a name="remarks"></a>备注

释放所有已分配的资源。

##  <a name="findkey"></a>  CSimpleMap::FindKey

查找特定的键。

```
int FindKey(const TKey& key) const;
```

### <a name="parameters"></a>参数

*key*<br/>
要搜索的键。

### <a name="return-value"></a>返回值

返回找到的关键的 if 索引，否则返回-1。

##  <a name="findval"></a>  CSimpleMap::FindVal

查找特定值。

```
int FindVal(const TVal& val) const;
```

### <a name="parameters"></a>参数

*val*<br/>
要搜索值。

### <a name="return-value"></a>返回值

返回的值的索引如果找到，否则返回-1。

##  <a name="getkeyat"></a>  CSimpleMap::GetKeyAt

检索指定索引处的键。

```
TKey& GetKeyAt(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要返回的键的索引。

### <a name="return-value"></a>返回值

返回引用的键*nIndex*。

### <a name="remarks"></a>备注

传递的索引*nIndex*必须是有效的返回值才有意义。

##  <a name="getsize"></a>  CSimpleMap::GetSize

映射数组中返回条目的数。

```
int GetSize() const;
```

### <a name="return-value"></a>返回值

映射数组中返回的项数 （键和值是一个条目）。

##  <a name="getvalueat"></a>  CSimpleMap::GetValueAt

检索特定索引处的值。

```
TVal& GetValueAt(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要返回的值的索引。

### <a name="return-value"></a>返回值

返回由引用的值*nIndex*。

### <a name="remarks"></a>备注

传递的索引*nIndex*必须是有效的返回值才有意义。

##  <a name="lookup"></a>  CSimpleMap::Lookup

返回与给定键关联的值。

```
TVal Lookup(const TKey& key) const;
```

### <a name="parameters"></a>参数

*key*<br/>
键。

### <a name="return-value"></a>返回值

返回关联的值。 如果没有匹配的键是找到为 NULL 则返回。

##  <a name="remove"></a>  CSimpleMap::Remove

删除密钥和匹配的值。

```
BOOL Remove(const TKey& key);
```

### <a name="parameters"></a>参数

*key*<br/>
键。

### <a name="return-value"></a>返回值

如果键和值匹配已成功删除，则返回 FALSE 否则，则返回 TRUE。

##  <a name="removeall"></a>  CSimpleMap::RemoveAll

移除所有键和值。

```
void RemoveAll();
```

### <a name="remarks"></a>备注

从映射数组对象中移除所有键和值。

##  <a name="removeat"></a>  CSimpleMap::RemoveAt

移除键和关联的指定索引处的值。

```
BOOL RemoveAt(int nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
键和关联的值，若要删除的索引。

### <a name="return-value"></a>返回值

如果，返回 TRUE 成功后，FALSE 指定的索引是无效的索引。

##  <a name="reverselookup"></a>  CSimpleMap::ReverseLookup

返回与给定的值关联的键。

```
TKey ReverseLookup(const TVal& val) const;
```

### <a name="parameters"></a>参数

*val*<br/>
值。

### <a name="return-value"></a>返回值

返回关联的键。 如果没有匹配的键是找到为 NULL 则返回。

##  <a name="setat"></a>  CSimpleMap::SetAt

设置与给定键关联的值。

```
BOOL SetAt(const TKey& key, const TVal& val);
```

### <a name="parameters"></a>参数

*key*<br/>
键。

*val*<br/>
要分配的新值。

### <a name="return-value"></a>返回值

如果找到该键，和的值否则是已成功更改为 FALSE，则返回 TRUE。

##  <a name="setatindex"></a>  CSimpleMap::SetAtIndex

设置指定索引处的键和值。

```
BOOL SetAtIndex(
    int nIndex,
    const TKey& key,
    const TVal& val);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
引用的键和值配对，更改索引。

*key*<br/>
新的密钥。

*val*<br/>
新值。

### <a name="return-value"></a>返回值

如果，返回 TRUE 成功，则为 FALSE 如果索引无效。

### <a name="remarks"></a>备注

更新密钥和值指向*nIndex*。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
