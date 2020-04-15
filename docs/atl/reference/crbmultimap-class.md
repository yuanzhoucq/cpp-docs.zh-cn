---
title: CRBMultiMap 类
ms.date: 11/04/2016
f1_keywords:
- CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap::CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap::FindFirstWithKey
- ATLCOLL/ATL::CRBMultiMap::GetNextValueWithKey
- ATLCOLL/ATL::CRBMultiMap::GetNextWithKey
- ATLCOLL/ATL::CRBMultiMap::Insert
- ATLCOLL/ATL::CRBMultiMap::RemoveKey
helpviewer_keywords:
- CRBMultiMap class
ms.assetid: 94d3ec0c-3e30-4ab7-a101-d8da4fb8add3
ms.openlocfilehash: 1e36bc267b3a539d2d1d4bf370b9cdc33828c760
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331421"
---
# <a name="crbmultimap-class"></a>CRBMultiMap 类

此类表示一个映射结构，允许每个键可以使用红黑二进制树与多个值关联。

## <a name="syntax"></a>语法

```
template<typename K,
         typename V,
         class KTraits = CElementTraits<K>,
         class VTraits = CElementTraits<V>>
class CRBMultiMap : public CRBTree<K, V, KTraits, VTraits>
```

#### <a name="parameters"></a>参数

*K*<br/>
键元素类型。

*五*<br/>
值元素类型。

*克瓦次克*<br/>
用于复制或移动关键元素的代码。 有关详细信息[，请参阅 CElementTraits 类](../../atl/reference/celementtraits-class.md)。

*VTraits*<br/>
用于复制或移动值元素的代码。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CRB多映射：CRB多映射](#crbmultimap)|构造函数。|
|[CRB多映射：：*CRB多映射](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CRB多映射：：查找第一键](#findfirstwithkey)|调用此方法以查找具有给定键的第一个元素的位置。|
|[CRB多映射：获取下一个值与密钥](#getnextvaluewithkey)|调用此方法获取与给定键关联的值，并更新位置值。|
|[CRB多映射：：获取下一个与密钥](#getnextwithkey)|调用此方法获取与给定键关联的元素，并更新位置值。|
|[CRB多映射：插入](#insert)|调用此方法以将元素对插入到地图中。|
|[CRB多映射：：删除键](#removekey)|调用此方法以删除给定键的所有键/值元素。|

## <a name="remarks"></a>备注

`CRBMultiMap`支持任何给定类型的映射数组，管理键元素和值的有序数组。 与[CRBMap](../../atl/reference/crbmap-class.md)类不同，每个键可以与多个值相关联。

元素（由键和值组成）使用[CRBMultiMap：：插入](#insert)方法存储在二进制树结构中。 可以使用[CRBMultiMap：：删除Key](#removekey)方法删除元素，该方法删除与给定键匹配的所有元素。

使用[CRBTree：：获取头位置](../../atl/reference/crbtree-class.md#getheadposition)[、CRBTree：getNext](../../atl/reference/crbtree-class.md#getnext)和[CRBTree：getNextValue](../../atl/reference/crbtree-class.md#getnextvalue)等方法可以遍历树。 可以使用[CRBMultiMap：：查找第一个密钥](#findfirstwithkey)[、CRB 多映射：获取NextValue与密钥](#getnextvaluewithkey)和[CRB 多映射：获取NextNext与键](#getnextwithkey)方法，可以访问每个键的潜在多个值。 有关[CRBMultiMap 的示例：CRBMultiMap，](#crbmultimap)请参阅实际说明。

*KTraits*和*VTraits*参数是包含复制或移动元素所需的任何补充代码的特征类。

`CRBMultiMap`派生自[CRBTree](../../atl/reference/crbtree-class.md)，它使用红黑算法实现二进制树。 `CRBMultiMap` [CAtlMap](../../atl/reference/catlmap-class.md)类提供的替代方法`CRBMap`。 当只需要存储少量元素时，请考虑改用[CSimpleMap](../../atl/reference/csimplemap-class.md)类。

有关各种集合类及其特性和性能特征的更完整的讨论，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CRBTree](../../atl/reference/crbtree-class.md)

`CRBMultiMap`

## <a name="requirements"></a>要求

**标题：** atlcoll.h

## <a name="crbmultimapcrbmultimap"></a><a name="crbmultimap"></a>CRB多映射：CRB多映射

构造函数。

```
explicit CRBMultiMap(size_t nBlockSize = 10) throw();
```

### <a name="parameters"></a>参数

*nBlockSize*<br/>
块大小。

### <a name="remarks"></a>备注

*nBlockSize*参数是需要新元素时分配的内存量的度量。 较大的块大小减少了对内存分配例程的调用，但使用的资源更多。 默认值将一次为 10 个元素分配空间。

有关其他可用方法的信息，请参阅基类[CRBTree](../../atl/reference/crbtree-class.md)的文档。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#85](../../atl/codesnippet/cpp/crbmultimap-class_1.cpp)]

## <a name="crbmultimapcrbmultimap"></a><a name="dtor"></a>CRB多映射：：*CRB多映射

析构函数。

```
~CRBMultiMap() throw();
```

### <a name="remarks"></a>备注

释放任何分配的资源。

有关其他可用方法的信息，请参阅基类[CRBTree](../../atl/reference/crbtree-class.md)的文档。

## <a name="crbmultimapfindfirstwithkey"></a><a name="findfirstwithkey"></a>CRB多映射：：查找第一键

调用此方法以查找具有给定键的第一个元素的位置。

```
POSITION FindFirstWithKey(KINARGTYPE key) const throw();
```

### <a name="parameters"></a>参数

*关键*<br/>
指定标识要找到的元素的键。

### <a name="return-value"></a>返回值

如果找到键，则返回第一个键/值元素的位置，否则返回 NULL。

### <a name="remarks"></a>备注

中的键`CRBMultiMap`可以具有一个或多个关联的值。 此方法将提供与该特定键关联的第一个值（实际上可能是唯一的值）的位置值。 然后，返回的位置值可与[CRBMultiMap 一起使用：：获取NextValue与密钥](#getnextvaluewithkey)或[CRBMultiMap：：获取NextNextWithKey](#getnextwithkey)以获取值并更新位置。

有关其他可用方法的信息，请参阅基类[CRBTree](../../atl/reference/crbtree-class.md)的文档。

### <a name="example"></a>示例

请参阅[CRB 多映射的示例：：CRB多映射](#crbmultimap)。

## <a name="crbmultimapgetnextvaluewithkey"></a><a name="getnextvaluewithkey"></a>CRB多映射：获取下一个值与密钥

调用此方法获取与给定键关联的值并更新位置值。

```
const V& GetNextValueWithKey(
    POSITION& pos,
    KINARGTYPE key) const throw();
V& GetNextValueWithKey(
    POSITION& pos,
    KINARGTYPE key) throw();
```

### <a name="parameters"></a>参数

*Pos*<br/>
位置值，通过调用[CRBMultiMap 获得：查找第一与密钥](#findfirstwithkey)或[CRB 多映射：：获取NextNextWithKey，](#getnextwithkey)或以前调用`GetNextValueWithKey`。

*关键*<br/>
指定标识要找到的元素的键。

### <a name="return-value"></a>返回值

返回与给定键关联的元素对。

### <a name="remarks"></a>备注

位置值将更新以指向与键关联的下一个值。 如果不存在更多值，则位置值设置为 NULL。

有关其他可用方法的信息，请参阅基类[CRBTree](../../atl/reference/crbtree-class.md)的文档。

### <a name="example"></a>示例

请参阅[CRB 多映射的示例：：CRB多映射](#crbmultimap)。

## <a name="crbmultimapgetnextwithkey"></a><a name="getnextwithkey"></a>CRB多映射：：获取下一个与密钥

调用此方法获取与给定键关联的元素并更新位置值。

```
const CPair* GetNextWithKey(
    POSITION& pos,
    KINARGTYPE key) const throw();
CPair* GetNextWithKey(
    POSITION& pos,
    KINARGTYPE key) throw();
```

### <a name="parameters"></a>参数

*Pos*<br/>
位置值，通过调用[CRBMultiMap 获得：查找第一与密钥](#findfirstwithkey)或[CRB 多映射：：获取NextValue与密钥](#getnextvaluewithkey)，或以前调用`GetNextWithKey`。

*关键*<br/>
指定标识要找到的元素的键。

### <a name="return-value"></a>返回值

返回下一个[CRBTree：：CPair 类](crbtree-class.md#cpair_class)元素与给定键关联。

### <a name="remarks"></a>备注

位置值将更新以指向与键关联的下一个值。 如果不存在更多值，则位置值设置为 NULL。

有关其他可用方法的信息，请参阅基类[CRBTree](../../atl/reference/crbtree-class.md)的文档。

## <a name="crbmultimapinsert"></a><a name="insert"></a>CRB多映射：插入

调用此方法以将元素对插入到地图中。

```
POSITION Insert(KINARGTYPE key, VINARGTYPE value) throw(...);
```

### <a name="parameters"></a>参数

*关键*<br/>
要添加到`CRBMultiMap`对象的键值。

*value*<br/>
要添加到对象的值`CRBMultiMap`，与*键*相关联。

### <a name="return-value"></a>返回值

返回键/值元素对在对象中`CRBMultiMap`的位置。

### <a name="remarks"></a>备注

有关其他可用方法的信息，请参阅基类[CRBTree](../../atl/reference/crbtree-class.md)的文档。

### <a name="example"></a>示例

请参阅[CRB 多映射的示例：：CRB多映射](#crbmultimap)。

## <a name="crbmultimapremovekey"></a><a name="removekey"></a>CRB多映射：：删除键

调用此方法以删除给定键的所有键/值元素。

```
size_t RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>参数

*关键*<br/>
指定标识要删除的元素的键。

### <a name="return-value"></a>返回值

返回与给定键关联的值数。

### <a name="remarks"></a>备注

`RemoveKey`删除具有匹配*键*的键/值元素的所有键/值元素。

有关其他可用方法的信息，请参阅基类[CRBTree](../../atl/reference/crbtree-class.md)的文档。

### <a name="example"></a>示例

请参阅[CRB 多映射的示例：：CRB多映射](#crbmultimap)。

## <a name="see-also"></a>另请参阅

[CRBTree 类](../../atl/reference/crbtree-class.md)<br/>
[CAtlMap 类](../../atl/reference/catlmap-class.md)<br/>
[CRBMap 类](../../atl/reference/crbmap-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
