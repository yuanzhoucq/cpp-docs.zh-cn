---
title: CRBMap 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CRBMap
- ATLCOLL/ATL::CRBMap
- ATLCOLL/ATL::CRBMap::CRBMap
- ATLCOLL/ATL::CRBMap::Lookup
- ATLCOLL/ATL::CRBMap::RemoveKey
- ATLCOLL/ATL::CRBMap::SetAt
dev_langs:
- C++
helpviewer_keywords:
- CRBMap class
ms.assetid: 658e94dc-e835-4356-aed1-1513e1f66969
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 41b4bf9678f2382c124bcfef484d0becf687f530
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50072702"
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
|[CRBMap::CRBMap](#crbmap)|构造函数。|
|[CRBMap:: ~ CRBMap](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CRBMap::Lookup](#lookup)|调用此方法来查找键或值中的`CRBMap`对象。|
|[CRBMap::RemoveKey](#removekey)|调用此方法来删除从元素`CRBMap`给定键的对象。|
|[CRBMap::SetAt](#setat)|调用此方法要插入到映射的元素对。|

## <a name="remarks"></a>备注

`CRBMap` 为管理键的元素和相关联的值的有序的数组任意给定类型的映射数组提供支持。 每个密钥可以有一个关联的值。 存储二进制树 （由一个键和值组成） 的元素的结构，使用[CRBMap::SetAt](#setat)方法。 可以使用删除元素[CRBMap::RemoveKey](#removekey)方法，删除具有给定密钥值的元素。

遍历树伤害与方法如[CRBTree::GetHeadPosition](../../atl/reference/crbtree-class.md#getheadposition)， [CRBTree::GetNext](../../atl/reference/crbtree-class.md#getnext)，并[CRBTree::GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue)。

*KTraits*并*VTraits*参数是包含要复制或移动元素所需的任何补充代码的特征类。

`CRBMap` 派生自[CRBTree](../../atl/reference/crbtree-class.md)，它可实现使用红黑算法的二进制树。 [CRBMultiMap](../../atl/reference/crbmultimap-class.md)允许多个值，每个键的变体。 它也派生自`CRBTree`，并因此共享许多功能与`CRBMap`。

替代这两`CRBMap`并`CRBMultiMap`提供了[CAtlMap](../../atl/reference/catlmap-class.md)类。 如果只有少量的元素需要存储，请考虑使用[CSimpleMap](../../atl/reference/csimplemap-class.md)类。

有关更完整的各种集合类及其功能和性能特征的讨论，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CRBTree](../../atl/reference/crbtree-class.md)

`CRBMap`

## <a name="requirements"></a>要求

**标头：** atlcoll.h

##  <a name="crbmap"></a>  CRBMap::CRBMap

构造函数。

```
explicit CRBMap(size_t nBlockSize = 10) throw();
```

### <a name="parameters"></a>参数

*nBlockSize*<br/>
块大小。

### <a name="remarks"></a>备注

*NBlockSize*参数是分配新元素时所需的内存量的度量值。 更大的块大小降低对内存分配例程的调用，但使用更多的资源。 一次，默认值将为 10 个元素分配空间。

请参阅的文档的基类[CRBTree](../../atl/reference/crbtree-class.md)有关可用的其他方法的信息。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#81](../../atl/codesnippet/cpp/crbmap-class_1.cpp)]

##  <a name="dtor"></a>  CRBMap:: ~ CRBMap

析构函数。

```
~CRBMap() throw();
```

### <a name="remarks"></a>备注

释放任何已分配的资源。

请参阅的文档的基类[CRBTree](../../atl/reference/crbtree-class.md)有关可用的其他方法的信息。

##  <a name="lookup"></a>  CRBMap::Lookup

调用此方法来查找键或值中的`CRBMap`对象。

```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const throw(...);
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```

### <a name="parameters"></a>参数

*key*<br/>
指定用于标识要查找的元素的键。

*value*<br/>
未接收到查找值的变量。

### <a name="return-value"></a>返回值

第一种形式的方法返回 true，如果找到键，否则为 false。 第二个和第三个窗体返回一个指向[CPair](crbtree-class.md#cpair_class)。

### <a name="remarks"></a>备注

请参阅的文档的基类[CRBTree](../../atl/reference/crbtree-class.md)有关可用的其他方法的信息。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#82](../../atl/codesnippet/cpp/crbmap-class_2.cpp)]

##  <a name="removekey"></a>  CRBMap::RemoveKey

调用此方法来删除从元素`CRBMap`给定键的对象。

```
bool RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>参数

*key*<br/>
你想要删除键相对应的元素对。

### <a name="return-value"></a>返回值

如果键是找到并移除，false 失败，则返回 true。

### <a name="remarks"></a>备注

请参阅的文档的基类[CRBTree](../../atl/reference/crbtree-class.md)有关可用的其他方法的信息。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#83](../../atl/codesnippet/cpp/crbmap-class_3.cpp)]

##  <a name="setat"></a>  CRBMap::SetAt

调用此方法要插入到映射的元素对。

```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value) throw(...);
```

### <a name="parameters"></a>参数

*key*<br/>
要添加到密钥值`CRBMap`对象。

*value*<br/>
要添加到值`CRBMap`对象。

### <a name="return-value"></a>返回值

返回的位置中的键/值元素对`CRBMap`对象。

### <a name="remarks"></a>备注

`SetAt` 如果找到匹配项，将替换现有元素。 如果未找到该键，则创建新的键/值对。

请参阅的文档的基类[CRBTree](../../atl/reference/crbtree-class.md)有关可用的其他方法的信息。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#84](../../atl/codesnippet/cpp/crbmap-class_4.cpp)]

## <a name="see-also"></a>请参阅

[CRBTree 类](../../atl/reference/crbtree-class.md)<br/>
[CAtlMap 类](../../atl/reference/catlmap-class.md)<br/>
[CRBMultiMap 类](../../atl/reference/crbmultimap-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
