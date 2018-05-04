---
title: CRBMultiMap 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap::CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap::FindFirstWithKey
- ATLCOLL/ATL::CRBMultiMap::GetNextValueWithKey
- ATLCOLL/ATL::CRBMultiMap::GetNextWithKey
- ATLCOLL/ATL::CRBMultiMap::Insert
- ATLCOLL/ATL::CRBMultiMap::RemoveKey
dev_langs:
- C++
helpviewer_keywords:
- CRBMultiMap class
ms.assetid: 94d3ec0c-3e30-4ab7-a101-d8da4fb8add3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6ec016df268b702fd8b26d742d702ac38b95fa06
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="crbmultimap-class"></a>CRBMultiMap 类
此类表示允许每个键可以是使用多个值，使用红色黑色二进制树关联的映射结构。  
  
## <a name="syntax"></a>语法  
  
```
template<typename K,
         typename V, 
         class KTraits = CElementTraits<K>, 
         class VTraits = CElementTraits<V>>  
class CRBMultiMap : public CRBTree<K, V, KTraits, VTraits>
```    
  
#### <a name="parameters"></a>参数  
 `K`  
 键的元素类型。  
  
 *V*  
 值的元素类型。  
  
 `KTraits`  
 用于复制或移动关键元素的代码。 请参阅[CElementTraits 类](../../atl/reference/celementtraits-class.md)有关详细信息。  
  
 `VTraits`  
 用于复制或移动值元素的代码。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CRBMultiMap::CRBMultiMap](#crbmultimap)|构造函数。|  
|[CRBMultiMap:: ~ CRBMultiMap](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CRBMultiMap::FindFirstWithKey](#findfirstwithkey)|调用此方法以查找与给定键的第一个元素的位置。|  
|[CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey)|调用此方法以获取给定键，与关联的值并更新位置值。|  
|[CRBMultiMap::GetNextWithKey](#getnextwithkey)|调用此方法以获取给定键，与关联的元素，并更新位置值。|  
|[CRBMultiMap::Insert](#insert)|调用此方法以插入到映射的元素对。|  
|[CRBMultiMap::RemoveKey](#removekey)|调用此方法以删除所有给定键的键/值元素。|  
  
## <a name="remarks"></a>备注  
 `CRBMultiMap` 为管理密钥的元素和值的有序的数组任何给定类型的映射数组提供支持。 与不同[CRBMap](../../atl/reference/crbmap-class.md)类，每个键可以是与多个值相关联。  
  
 元素 （包含的键和值） 存储在二进制树的结构，使用[CRBMultiMap::Insert](#insert)方法。 可以使用删除元素[CRBMultiMap::RemoveKey](#removekey)方法，从而会删除与给定的键匹配的所有元素。  
  
 树的遍历可使用方法如[CRBTree::GetHeadPosition](../../atl/reference/crbtree-class.md#getheadposition)， [CRBTree::GetNext](../../atl/reference/crbtree-class.md#getnext)，和[CRBTree::GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue)。 访问可能对每个键的多个值可能使用[CRBMultiMap::FindFirstWithKey](#findfirstwithkey)， [CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey)，和[CRBMultiMap::GetNextWithKey](#getnextwithkey)方法。 请参阅示例[CRBMultiMap::CRBMultiMap](#crbmultimap)有关此在实践中的图例。  
  
 `KTraits`和`VTraits`参数是包含复制或移动元素所需的任何补充代码的特征类。  
  
 `CRBMultiMap` 派生自[CRBTree](../../atl/reference/crbtree-class.md)，该类可实现二进制树使用红色黑色算法。 一种替代方法`CRBMultiMap`和`CRBMap`所提供的[CAtlMap](../../atl/reference/catlmap-class.md)类。 当只有少量的元素需要存储时，请考虑使用[CSimpleMap](../../atl/reference/csimplemap-class.md)类。  
  
 有关的各种集合类及其功能和性能特征的更完整讨论，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。  
  
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
 `nBlockSize`  
 块大小。  
  
### <a name="remarks"></a>备注  
 `nBlockSize`参数是分配需要一个新的元素时的内存量的度量值。 更大的块大小减少到内存分配例程的调用，但使用更多资源。 一次，默认值将为 10 个元素分配空间。  
  
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
 `key`  
 指定标识要找的元素的键。  
  
### <a name="return-value"></a>返回值  
 如果找到项，NULL 否则，请返回第一个键/值元素的位置。  
  
### <a name="remarks"></a>备注  
 中的键`CRBMultiMap`可以具有一个或多个关联的值。 此方法将提供与该特定键关联的位置值的第一个值 （它可能，事实上，是唯一的值）。 返回的位置值随后可用于[CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey)或[CRBMultiMap::GetNextWithKey](#getnextwithkey)若要获取的值并更新位置。  
  
 请参阅的文档的基类[CRBTree](../../atl/reference/crbtree-class.md)有关可用的其他方法的信息。  
  
### <a name="example"></a>示例  
 请参阅示例[CRBMultiMap::CRBMultiMap](#crbmultimap)。  
  
##  <a name="getnextvaluewithkey"></a>  CRBMultiMap::GetNextValueWithKey  
 调用此方法以获取与给定的键关联的值并更新位置值。  
  
```
const V& GetNextValueWithKey(
    POSITION& pos,
    KINARGTYPE key) const throw();
V& GetNextValueWithKey(
    POSITION& pos,
    KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>参数  
 `pos`  
 获取通过到调用的位置值[CRBMultiMap::FindFirstWithKey](#findfirstwithkey)或[CRBMultiMap::GetNextWithKey](#getnextwithkey)，或上次调用`GetNextValueWithKey`。  
  
 `key`  
 指定标识要找的元素的键。  
  
### <a name="return-value"></a>返回值  
 返回与给定的键关联的元素对。  
  
### <a name="remarks"></a>备注  
 位置值更新为指向与键关联的下一个值。 如果没有更多的值存在，则会将位置值设置为 NULL。  
  
 请参阅的文档的基类[CRBTree](../../atl/reference/crbtree-class.md)有关可用的其他方法的信息。  
  
### <a name="example"></a>示例  
 请参阅示例[CRBMultiMap::CRBMultiMap](#crbmultimap)。  
  
##  <a name="getnextwithkey"></a>  CRBMultiMap::GetNextWithKey  
 调用此方法以获取与给定的键关联的元素，并更新位置值。  
  
```
const CPair* GetNextWithKey(
    POSITION& pos,
    KINARGTYPE key) const throw();
CPair* GetNextWithKey(
    POSITION& pos,
    KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>参数  
 `pos`  
 获取通过到调用的位置值[CRBMultiMap::FindFirstWithKey](#findfirstwithkey)或[CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey)，或上次调用`GetNextWithKey`。  
  
 `key`  
 指定标识要找的元素的键。  
  
### <a name="return-value"></a>返回值  
 返回下一个[CRBTree::CPair 类](crbtree-class.md#cpair_class)与给定的键关联的元素。  
  
### <a name="remarks"></a>备注  
 位置值更新为指向与键关联的下一个值。 如果没有更多的值存在，则会将位置值设置为 NULL。  
  
 请参阅的文档的基类[CRBTree](../../atl/reference/crbtree-class.md)有关可用的其他方法的信息。  
  
##  <a name="insert"></a>  CRBMultiMap::Insert  
 调用此方法以插入到映射的元素对。  
  
```
POSITION Insert(KINARGTYPE key, VINARGTYPE value) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `key`  
 密钥的值将添加到`CRBMultiMap`对象。  
  
 *value*  
 要添加到值`CRBMultiMap`与关联的对象`key`。  
  
### <a name="return-value"></a>返回值  
 返回的位置中的键/值元素对`CRBMultiMap`对象。  
  
### <a name="remarks"></a>备注  
 请参阅的文档的基类[CRBTree](../../atl/reference/crbtree-class.md)有关可用的其他方法的信息。  
  
### <a name="example"></a>示例  
 请参阅示例[CRBMultiMap::CRBMultiMap](#crbmultimap)。  
  
##  <a name="removekey"></a>  CRBMultiMap::RemoveKey  
 调用此方法以删除所有给定键的键/值元素。  
  
```
size_t RemoveKey(KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>参数  
 `key`  
 指定标识要删除的元素的键。  
  
### <a name="return-value"></a>返回值  
 返回与给定的键关联的值的数目。  
  
### <a name="remarks"></a>备注  
 `RemoveKey` 删除所有具有匹配的键的键/值元素`key`。  
  
 请参阅的文档的基类[CRBTree](../../atl/reference/crbtree-class.md)有关可用的其他方法的信息。  
  
### <a name="example"></a>示例  
 请参阅示例[CRBMultiMap::CRBMultiMap](#crbmultimap)。  
  
## <a name="see-also"></a>请参阅  
 [CRBTree 类](../../atl/reference/crbtree-class.md)   
 [CAtlMap 类](../../atl/reference/catlmap-class.md)   
 [CRBMap 类](../../atl/reference/crbmap-class.md)   
 [类概述](../../atl/atl-class-overview.md)
