---
title: CRBMap 类
ms.date: 11/04/2016
f1_keywords:
- CRBMap
- ATLCOLL/ATL::CRBMap
- ATLCOLL/ATL::CRBMap::CRBMap
- ATLCOLL/ATL::CRBMap::Lookup
- ATLCOLL/ATL::CRBMap::RemoveKey
- ATLCOLL/ATL::CRBMap::SetAt
helpviewer_keywords:
- CRBMap class
ms.assetid: 658e94dc-e835-4356-aed1-1513e1f66969
ms.openlocfilehash: 9e367ccc875eedf63e4f47018598662af2dfcf7d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331394"
---
# <a name="crbmap-class"></a>CRBMap 类

此类表示映射结构，使用红黑二进制树。

## <a name="syntax"></a>语法

```
template <typename K,
          typename V,
          class KTraits = CElementTraits<K>,
          class VTraits = CElementTraits<V>>
class CRBMap : public CRBTree<K, V, KTraits, VTraits>
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
|[CRBMap：CRBMap](#crbmap)|构造函数。|
|[CRBMap：*CRBMap](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CRBMap：：查找](#lookup)|调用此方法以查找对象中的`CRBMap`键或值。|
|[CRBMap：：删除键](#removekey)|调用此方法以在给定键的情况下从`CRBMap`对象中删除元素。|
|[CRBMap：setat](#setat)|调用此方法以将元素对插入到地图中。|

## <a name="remarks"></a>备注

`CRBMap`支持任何给定类型的映射数组，管理按顺序排列的关键元素数组及其关联值。 每个键只能有一个关联的值。 元素（由键和值组成）使用[CRBMap：setAt](#setat)方法存储在二进制树结构中。 可以使用[CRBMap：：removeKey](#removekey)方法删除元素，该方法使用给定的键值删除元素。

使用[CRBTree：：获取头位置](../../atl/reference/crbtree-class.md#getheadposition)[、CRBTree：getNext](../../atl/reference/crbtree-class.md#getnext)和[CRBTree：getNextValue](../../atl/reference/crbtree-class.md#getnextvalue)等方法可以遍历树。

*KTraits*和*VTraits*参数是包含复制或移动元素所需的任何补充代码的特征类。

`CRBMap`派生自[CRBTree](../../atl/reference/crbtree-class.md)，它使用红黑算法实现二进制树。 [CRBMultiMap](../../atl/reference/crbmultimap-class.md)是一种变体，它允许每个键有多个值。 它也是从`CRBTree`派生的，因此与`CRBMap`共享许多功能。

和 由`CRBMap``CRBMultiMap`[CAtlMap](../../atl/reference/catlmap-class.md)类提供的替代方法。 当只需要存储少量元素时，请考虑改用[CSimpleMap](../../atl/reference/csimplemap-class.md)类。

有关各种集合类及其特性和性能特征的更完整的讨论，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CRBTree](../../atl/reference/crbtree-class.md)

`CRBMap`

## <a name="requirements"></a>要求

**标题：** atlcoll.h

## <a name="crbmapcrbmap"></a><a name="crbmap"></a>CRBMap：CRBMap

构造函数。

```
explicit CRBMap(size_t nBlockSize = 10) throw();
```

### <a name="parameters"></a>参数

*nBlockSize*<br/>
块大小。

### <a name="remarks"></a>备注

*nBlockSize*参数是需要新元素时分配的内存量的度量。 较大的块大小减少了对内存分配例程的调用，但使用的资源更多。 默认值将一次为 10 个元素分配空间。

有关其他可用方法的信息，请参阅基类[CRBTree](../../atl/reference/crbtree-class.md)的文档。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#81](../../atl/codesnippet/cpp/crbmap-class_1.cpp)]

## <a name="crbmapcrbmap"></a><a name="dtor"></a>CRBMap：*CRBMap

析构函数。

```
~CRBMap() throw();
```

### <a name="remarks"></a>备注

释放任何分配的资源。

有关其他可用方法的信息，请参阅基类[CRBTree](../../atl/reference/crbtree-class.md)的文档。

## <a name="crbmaplookup"></a><a name="lookup"></a>CRBMap：：查找

调用此方法以查找对象中的`CRBMap`键或值。

```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const throw(...);
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```

### <a name="parameters"></a>参数

*关键*<br/>
指定标识要备份的元素的键。

*value*<br/>
接收上值的变量。

### <a name="return-value"></a>返回值

如果找到键，则方法的第一种形式返回 true，否则为 false。 第二个和第三个窗体返回指向[CPair](crbtree-class.md#cpair_class)的指针。

### <a name="remarks"></a>备注

有关其他可用方法的信息，请参阅基类[CRBTree](../../atl/reference/crbtree-class.md)的文档。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#82](../../atl/codesnippet/cpp/crbmap-class_2.cpp)]

## <a name="crbmapremovekey"></a><a name="removekey"></a>CRBMap：：删除键

调用此方法以在给定键的情况下从`CRBMap`对象中删除元素。

```
bool RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>参数

*关键*<br/>
与要删除的元素对对应的键。

### <a name="return-value"></a>返回值

如果找到并删除该键，则返回 true，在失败时为 false。

### <a name="remarks"></a>备注

有关其他可用方法的信息，请参阅基类[CRBTree](../../atl/reference/crbtree-class.md)的文档。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#83](../../atl/codesnippet/cpp/crbmap-class_3.cpp)]

## <a name="crbmapsetat"></a><a name="setat"></a>CRBMap：setat

调用此方法以将元素对插入到地图中。

```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value) throw(...);
```

### <a name="parameters"></a>参数

*关键*<br/>
要添加到`CRBMap`对象的键值。

*value*<br/>
要添加到对象的值`CRBMap`。

### <a name="return-value"></a>返回值

返回键/值元素对在对象中`CRBMap`的位置。

### <a name="remarks"></a>备注

`SetAt`如果找到匹配的键，则替换现有元素。 如果未找到该键，则创建新的键/值对。

有关其他可用方法的信息，请参阅基类[CRBTree](../../atl/reference/crbtree-class.md)的文档。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#84](../../atl/codesnippet/cpp/crbmap-class_4.cpp)]

## <a name="see-also"></a>另请参阅

[CRBTree 类](../../atl/reference/crbtree-class.md)<br/>
[CAtlMap 类](../../atl/reference/catlmap-class.md)<br/>
[CRBMultiMap 类](../../atl/reference/crbmultimap-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
