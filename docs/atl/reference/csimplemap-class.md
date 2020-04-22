---
title: CSimpleMap 类
ms.date: 11/04/2016
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
helpviewer_keywords:
- CSimpleMap class
ms.assetid: 61b06eb4-ae73-44b0-a305-0afb5a33e8b1
ms.openlocfilehash: eed41c2250728d257b6d303e79c3afd36a543dbb
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747643"
---
# <a name="csimplemap-class"></a>CSimpleMap 类

此类支持简单的映射数组。

## <a name="syntax"></a>语法

```
template <class TKey, class TVal, class TEqual = CSimpleMapEqualHelper<TKey, TVal>>
class CSimpleMap
```

#### <a name="parameters"></a>参数

*TKey*<br/>
键元素类型。

*TVal*<br/>
值元素类型。

*TEqual*<br/>
特征对象，定义类型`T`元素的相等性测试。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|[CSimpleMap：_ArrayElementType](#_arrayelementtype)|值类型的类型。|
|[C简单映射：_ArrayKeyType](#_arraykeytype)|键类型的类型。|

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[简单映射：：C简单映射](#csimplemap)|构造函数。|
|[简单映射：：_C 简单映射](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[简单映射：：添加](#add)|向地图数组添加键和相关值。|
|[简单映射：：查找密钥](#findkey)|查找特定键。|
|[简单映射：：查找Val](#findval)|查找特定值。|
|[简单映射：：获取键](#getkeyat)|检索指定的密钥。|
|[C简单映射：：获取大小](#getsize)|返回映射数组中的条目数。|
|[简单映射：：获取价值](#getvalueat)|检索指定的值。|
|[C简单映射：：查找](#lookup)|返回与给定键关联的值。|
|[简单映射：：删除](#remove)|删除键和匹配值。|
|[简单映射：：删除所有](#removeall)|删除所有键和值。|
|[简单映射：：删除 AT](#removeat)|删除特定的键和匹配值。|
|[C简单映射：：反向查找](#reverselookup)|返回与给定值关联的键。|
|[简单映射：：Setat](#setat)|设置与给定键关联的值。|
|[简单映射：：设置Atindex](#setatindex)|设置特定的键和值。|

## <a name="remarks"></a>备注

`CSimpleMap`支持任何给定类型的`T`简单映射数组，管理键元素及其关联值的无序数组。

该参数`TEqual`提供了一种为类型中的`T`两个元素定义相等函数的方法。 通过创建类似于[CSimpleMapEqualHelper 的](../../atl/reference/csimplemapequalhelper-class.md)类，可以更改任何给定数组的相等测试的行为。 例如，在处理指针数组时，将相等性定义为根据指针引用的值可能很有用。 默认实现使用运算符 **_（）**。

`CSimpleMap`提供和[CSimpleArray](../../atl/reference/csimplearray-class.md)与以前的 ATL 版本兼容[，CAtlArray](../../atl/reference/catlarray-class.md)和[CAtlMap](../../atl/reference/catlmap-class.md)提供了更完整、更高效的收集实现。

与 ATL 和 MFC 中的其他地图集合不同，此类使用简单的数组实现，查找搜索需要线性搜索。 `CAtlMap`当数组包含大量元素时，应使用。

## <a name="requirements"></a>要求

**标题：** atlsimpcoll.h

## <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#91](../../atl/codesnippet/cpp/csimplemap-class_1.cpp)]

## <a name="csimplemapadd"></a><a name="add"></a>简单映射：：添加

向地图数组添加键和相关值。

```
BOOL Add(const TKey& key, const TVal& val);
```

### <a name="parameters"></a>参数

*键*<br/>
键。

*瓦尔*<br/>
关联的值。

### <a name="return-value"></a>返回值

如果成功添加键和值，则返回 TRUE，否则为 FALSE。

### <a name="remarks"></a>备注

每个键和值对都添加会导致映射数组内存被释放和重新分配，以确保每个键的数据始终连续存储。 也就是说，第二个关键元素始终直接遵循内存中的第一个关键元素等。

## <a name="csimplemap_arrayelementtype"></a><a name="_arrayelementtype"></a>CSimpleMap：_ArrayElementType

键类型的类型。

```
typedef TVal _ArrayElementType;
```

## <a name="csimplemap_arraykeytype"></a><a name="_arraykeytype"></a>C简单映射：_ArrayKeyType

值类型的类型。

```
typedef TKey _ArrayKeyType;
```

## <a name="csimplemapcsimplemap"></a><a name="csimplemap"></a>简单映射：：C简单映射

构造函数。

```
CSimpleMap();
```

### <a name="remarks"></a>备注

初始化数据成员。

## <a name="csimplemapcsimplemap"></a><a name="dtor"></a>简单映射：：_C 简单映射

析构函数。

```
~CSimpleMap();
```

### <a name="remarks"></a>备注

释放所有分配的资源。

## <a name="csimplemapfindkey"></a><a name="findkey"></a>简单映射：：查找密钥

查找特定键。

```
int FindKey(const TKey& key) const;
```

### <a name="parameters"></a>参数

*键*<br/>
要搜索的键。

### <a name="return-value"></a>返回值

如果找到密钥的索引，则返回 -1。

## <a name="csimplemapfindval"></a><a name="findval"></a>简单映射：：查找Val

查找特定值。

```
int FindVal(const TVal& val) const;
```

### <a name="parameters"></a>参数

*瓦尔*<br/>
要搜索的值。

### <a name="return-value"></a>返回值

如果找到值，则返回该值的索引，否则返回 -1。

## <a name="csimplemapgetkeyat"></a><a name="getkeyat"></a>简单映射：：获取键

在指定的索引处检索密钥。

```
TKey& GetKeyAt(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要返回的键的索引。

### <a name="return-value"></a>返回值

返回*nIndex*引用的键 。

### <a name="remarks"></a>备注

*nIndex*传递的索引必须有效，才能使返回值有意义。

## <a name="csimplemapgetsize"></a><a name="getsize"></a>C简单映射：：获取大小

返回映射数组中的条目数。

```
int GetSize() const;
```

### <a name="return-value"></a>返回值

返回映射数组中的条目数（键和值是一个条目）。

## <a name="csimplemapgetvalueat"></a><a name="getvalueat"></a>简单映射：：获取价值

检索特定索引处的值。

```
TVal& GetValueAt(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要返回的值的索引。

### <a name="return-value"></a>返回值

返回*nIndex*引用的值。

### <a name="remarks"></a>备注

*nIndex*传递的索引必须有效，才能使返回值有意义。

## <a name="csimplemaplookup"></a><a name="lookup"></a>C简单映射：：查找

返回与给定键关联的值。

```
TVal Lookup(const TKey& key) const;
```

### <a name="parameters"></a>参数

*键*<br/>
键。

### <a name="return-value"></a>返回值

返回关联的值。 如果未找到匹配的密钥，则返回 NULL。

## <a name="csimplemapremove"></a><a name="remove"></a>简单映射：：删除

删除键和匹配值。

```
BOOL Remove(const TKey& key);
```

### <a name="parameters"></a>参数

*键*<br/>
键。

### <a name="return-value"></a>返回值

如果成功删除键和匹配值，则返回 TRUE，否则为 FALSE。

## <a name="csimplemapremoveall"></a><a name="removeall"></a>简单映射：：删除所有

删除所有键和值。

```cpp
void RemoveAll();
```

### <a name="remarks"></a>备注

从映射数组对象中删除所有键和值。

## <a name="csimplemapremoveat"></a><a name="removeat"></a>简单映射：：删除 AT

删除指定索引处的键和关联的值。

```
BOOL RemoveAt(int nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要删除的键和相关值的索引。

### <a name="return-value"></a>返回值

如果指定的索引无效，则在成功时返回 TRUE，则 FALSE。

## <a name="csimplemapreverselookup"></a><a name="reverselookup"></a>C简单映射：：反向查找

返回与给定值关联的键。

```
TKey ReverseLookup(const TVal& val) const;
```

### <a name="parameters"></a>参数

*瓦尔*<br/>
值。

### <a name="return-value"></a>返回值

返回关联的密钥。 如果未找到匹配的密钥，则返回 NULL。

## <a name="csimplemapsetat"></a><a name="setat"></a>简单映射：：Setat

设置与给定键关联的值。

```
BOOL SetAt(const TKey& key, const TVal& val);
```

### <a name="parameters"></a>参数

*键*<br/>
键。

*瓦尔*<br/>
要分配的新值。

### <a name="return-value"></a>返回值

如果找到密钥，并且该值已成功更改，则返回 TRUE，否则为 FALSE。

## <a name="csimplemapsetatindex"></a><a name="setatindex"></a>简单映射：：设置Atindex

在指定的索引处设置键和值。

```
BOOL SetAtIndex(
    int nIndex,
    const TKey& key,
    const TVal& val);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
索引，引用要更改的键和值配对。

*键*<br/>
新键。

*瓦尔*<br/>
新值。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE;如果索引无效，则返回 FALSE。

### <a name="remarks"></a>备注

更新*nIndex*指向的键和值。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
