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
ms.openlocfilehash: 03a9639e8b0b3d11a414e5db0ce874d7ca8f2d45
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62278132"
---
# <a name="crbmultimap-class"></a>CRBMultiMap 类

此类表示允许每个键可以是使用多个值，使用红黑二进制树关联的映射结构。

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
Key 元素类型。

*V*<br/>
值元素类型。

*KTraits*<br/>
用于复制或移动关键元素的代码。 请参阅[CElementTraits 类](../../atl/reference/celementtraits-class.md)的更多详细信息。

*VTraits*<br/>
用于复制或移动值元素的代码。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CRBMultiMap::CRBMultiMap](#crbmultimap)|构造函数。|
|[CRBMultiMap::~CRBMultiMap](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CRBMultiMap::FindFirstWithKey](#findfirstwithkey)|调用此方法以查找与给定键的第一个元素的位置。|
|[CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey)|调用此方法以获取与给定键关联的值并更新位置值。|
|[CRBMultiMap::GetNextWithKey](#getnextwithkey)|调用此方法以获取与给定键关联的元素和更新位置值。|
|[CRBMultiMap::Insert](#insert)|调用此方法要插入到映射的元素对。|
|[CRBMultiMap::RemoveKey](#removekey)|调用此方法以删除所有给定键的键/值元素。|

## <a name="remarks"></a>备注

`CRBMultiMap` 为管理键的元素和值的有序的数组任意给定类型的映射数组提供支持。 与不同[CRBMap](../../atl/reference/crbmap-class.md)类，每个键可以与多个值相关联。

存储二进制树 （由一个键和值组成） 的元素的结构，使用[CRBMultiMap::Insert](#insert)方法。 可以使用删除元素[CRBMultiMap::RemoveKey](#removekey)方法，这将删除与给定的键匹配的所有元素。

遍历树伤害与方法如[CRBTree::GetHeadPosition](../../atl/reference/crbtree-class.md#getheadposition)， [CRBTree::GetNext](../../atl/reference/crbtree-class.md#getnext)，并[CRBTree::GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue)。 访问可能会对每个键的多个值可能使用[CRBMultiMap::FindFirstWithKey](#findfirstwithkey)， [CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey)，和[CRBMultiMap::GetNextWithKey](#getnextwithkey)方法。 有关示例，请参阅[CRBMultiMap::CRBMultiMap](#crbmultimap)有关此在实践中的图例。

*KTraits*并*VTraits*参数是包含要复制或移动元素所需的任何补充代码的特征类。

`CRBMultiMap` 派生自[CRBTree](../../atl/reference/crbtree-class.md)，它可实现使用红黑算法的二进制树。 一种替代方法`CRBMultiMap`并`CRBMap`提供了[CAtlMap](../../atl/reference/catlmap-class.md)类。 如果只有少量的元素需要存储，请考虑使用[CSimpleMap](../../atl/reference/csimplemap-class.md)类。

有关更完整的各种集合类及其功能和性能特征的讨论，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CRBTree](../../atl/reference/crbtree-class.md)

`CRBMultiMap`

## <a name="requirements"></a>要求

**标头：** atlcoll.h

##  <a name="crbmultimap"></a>  CRBMultiMap::CRBMultiMap

构造函数。

```
explicit CRBMultiMap(size_t nBlockSize = 10) throw();
```

### <a name="parameters"></a>参数

*nBlockSize*<br/>
块大小。

### <a name="remarks"></a>备注

*NBlockSize*参数是分配新元素时所需的内存量的度量值。 更大的块大小降低对内存分配例程的调用，但使用更多的资源。 一次，默认值将为 10 个元素分配空间。

请参阅的文档的基类[CRBTree](../../atl/reference/crbtree-class.md)有关可用的其他方法的信息。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#85](../../atl/codesnippet/cpp/crbmultimap-class_1.cpp)]

##  <a name="dtor"></a>  CRBMultiMap:: ~ CRBMultiMap

析构函数。

```
~CRBMultiMap() throw();
```

### <a name="remarks"></a>备注

释放任何已分配的资源。

请参阅的文档的基类[CRBTree](../../atl/reference/crbtree-class.md)有关可用的其他方法的信息。

##  <a name="findfirstwithkey"></a>  CRBMultiMap::FindFirstWithKey

调用此方法以查找与给定键的第一个元素的位置。

```
POSITION FindFirstWithKey(KINARGTYPE key) const throw();
```

### <a name="parameters"></a>参数

*key*<br/>
指定用于标识要查找的元素的键。

### <a name="return-value"></a>返回值

如果找到键，NULL 否则，返回第一个键/值元素的位置。

### <a name="remarks"></a>备注

中的键`CRBMultiMap`可以有一个或多个关联的值。 此方法将提供与该特定键相关联的第一个值 （它可能，实际上，是唯一的值） 的位置值。 返回的位置值随后可用于[CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey)或[CRBMultiMap::GetNextWithKey](#getnextwithkey)获取值并更新位置。

请参阅的文档的基类[CRBTree](../../atl/reference/crbtree-class.md)有关可用的其他方法的信息。

### <a name="example"></a>示例

有关示例，请参阅[CRBMultiMap::CRBMultiMap](#crbmultimap)。

##  <a name="getnextvaluewithkey"></a>  CRBMultiMap::GetNextValueWithKey

调用此方法以获取与给定键关联的值并更新位置值。

```
const V& GetNextValueWithKey(
    POSITION& pos,
    KINARGTYPE key) const throw();
V& GetNextValueWithKey(
    POSITION& pos,
    KINARGTYPE key) throw();
```

### <a name="parameters"></a>参数

*pos*<br/>
获取到调用的位置值[CRBMultiMap::FindFirstWithKey](#findfirstwithkey)或[CRBMultiMap::GetNextWithKey](#getnextwithkey)，或以前调用`GetNextValueWithKey`。

*key*<br/>
指定用于标识要查找的元素的键。

### <a name="return-value"></a>返回值

返回与给定键关联的元素对。

### <a name="remarks"></a>备注

位置值更新为指向下一个与键关联的值。 如果没有更多的值存在，则将位置值设置为 NULL。

请参阅的文档的基类[CRBTree](../../atl/reference/crbtree-class.md)有关可用的其他方法的信息。

### <a name="example"></a>示例

有关示例，请参阅[CRBMultiMap::CRBMultiMap](#crbmultimap)。

##  <a name="getnextwithkey"></a>  CRBMultiMap::GetNextWithKey

调用此方法以获取与给定键关联的元素和更新位置值。

```
const CPair* GetNextWithKey(
    POSITION& pos,
    KINARGTYPE key) const throw();
CPair* GetNextWithKey(
    POSITION& pos,
    KINARGTYPE key) throw();
```

### <a name="parameters"></a>参数

*pos*<br/>
获取到调用的位置值[CRBMultiMap::FindFirstWithKey](#findfirstwithkey)或[CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey)，或以前调用`GetNextWithKey`。

*key*<br/>
指定用于标识要查找的元素的键。

### <a name="return-value"></a>返回值

返回下一步[CRBTree::CPair 类](crbtree-class.md#cpair_class)与给定键关联的元素。

### <a name="remarks"></a>备注

位置值更新为指向下一个与键关联的值。 如果没有更多的值存在，则将位置值设置为 NULL。

请参阅的文档的基类[CRBTree](../../atl/reference/crbtree-class.md)有关可用的其他方法的信息。

##  <a name="insert"></a>  CRBMultiMap::Insert

调用此方法要插入到映射的元素对。

```
POSITION Insert(KINARGTYPE key, VINARGTYPE value) throw(...);
```

### <a name="parameters"></a>参数

*key*<br/>
要添加到密钥值`CRBMultiMap`对象。

*值*<br/>
要添加到值`CRBMultiMap`与相关联的对象*密钥*。

### <a name="return-value"></a>返回值

返回的位置中的键/值元素对`CRBMultiMap`对象。

### <a name="remarks"></a>备注

请参阅的文档的基类[CRBTree](../../atl/reference/crbtree-class.md)有关可用的其他方法的信息。

### <a name="example"></a>示例

有关示例，请参阅[CRBMultiMap::CRBMultiMap](#crbmultimap)。

##  <a name="removekey"></a>  CRBMultiMap::RemoveKey

调用此方法以删除所有给定键的键/值元素。

```
size_t RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>参数

*key*<br/>
指定用于标识要删除的元素的键。

### <a name="return-value"></a>返回值

返回与给定键关联的值的数目。

### <a name="remarks"></a>备注

`RemoveKey` 将删除所有拥有匹配的键的键/值元素*密钥*。

请参阅的文档的基类[CRBTree](../../atl/reference/crbtree-class.md)有关可用的其他方法的信息。

### <a name="example"></a>示例

有关示例，请参阅[CRBMultiMap::CRBMultiMap](#crbmultimap)。

## <a name="see-also"></a>请参阅

[CRBTree 类](../../atl/reference/crbtree-class.md)<br/>
[CAtlMap 类](../../atl/reference/catlmap-class.md)<br/>
[CRBMap 类](../../atl/reference/crbmap-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
