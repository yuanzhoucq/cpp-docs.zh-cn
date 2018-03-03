---
title: "CRBMap 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3cfa4d6fff6b46341f01b4d5ce18d9ec418738bf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="crbmap-class"></a>CRBMap 类
此类表示一个映射结构中，使用红色黑色二进制树。  
  
## <a name="syntax"></a>语法  
  
```
template <typename K,
          typename V, 
          class KTraits = CElementTraits<K>, 
          class VTraits = CElementTraits<V>> 
class CRBMap : public CRBTree<K, V, KTraits, VTraits>
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
|[CRBMap::CRBMap](#crbmap)|构造函数。|  
|[CRBMap:: ~ CRBMap](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CRBMap::Lookup](#lookup)|调用此方法以查找密钥或中的值`CRBMap`对象。|  
|[CRBMap::RemoveKey](#removekey)|调用此方法以删除从元素`CRBMap`给定键的对象。|  
|[CRBMap::SetAt](#setat)|调用此方法以插入到映射的元素对。|  
  
## <a name="remarks"></a>备注  
 `CRBMap`为管理密钥的元素及其关联的值的有序的数组任何给定类型的映射数组提供支持。 每个密钥可以只有一个关联的值。 元素 （包含的键和值） 存储在二进制树的结构，使用[CRBMap::SetAt](#setat)方法。 可以使用删除元素[CRBMap::RemoveKey](#removekey)方法，从而会删除具有给定的密钥值的元素。  
  
 树的遍历可使用方法如[CRBTree::GetHeadPosition](../../atl/reference/crbtree-class.md#getheadposition)， [CRBTree::GetNext](../../atl/reference/crbtree-class.md#getnext)，和[CRBTree::GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue)。  
  
 `KTraits`和`VTraits`参数是包含复制或移动元素所需的任何补充代码的特征类。  
  
 `CRBMap`派生自[CRBTree](../../atl/reference/crbtree-class.md)，该类可实现二进制树使用红色黑色算法。 [CRBMultiMap](../../atl/reference/crbmultimap-class.md)是允许每个键的多个值的变化形式。 它太派生自`CRBTree`，并因此共享许多功能与`CRBMap`。  
  
 替代这两`CRBMap`和`CRBMultiMap`所提供的[CAtlMap](../../atl/reference/catlmap-class.md)类。 当只有少量的元素需要存储时，请考虑使用[CSimpleMap](../../atl/reference/csimplemap-class.md)类。  
  
 有关的各种集合类及其功能和性能特征的更完整讨论，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CRBTree](../../atl/reference/crbtree-class.md)  
  
 `CRBMap`  
  
## <a name="requirements"></a>惠?  
 **标头：** atlcoll.h  
  
##  <a name="crbmap"></a>CRBMap::CRBMap  
 构造函数。  
  
```
explicit CRBMap(size_t nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>参数  
 `nBlockSize`  
 块大小。  
  
### <a name="remarks"></a>备注  
 `nBlockSize`参数是分配需要一个新的元素时的内存量的度量值。 更大的块大小减少到内存分配例程的调用，但使用更多资源。 一次，默认值将为 10 个元素分配空间。  
  
 请参阅的文档的基类[CRBTree](../../atl/reference/crbtree-class.md)有关可用的其他方法的信息。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#81](../../atl/codesnippet/cpp/crbmap-class_1.cpp)]  
  
##  <a name="dtor"></a>CRBMap:: ~ CRBMap  
 析构函数。  
  
```
~CRBMap() throw();
```  
  
### <a name="remarks"></a>备注  
 释放任何已分配的资源。  
  
 请参阅的文档的基类[CRBTree](../../atl/reference/crbtree-class.md)有关可用的其他方法的信息。  
  
##  <a name="lookup"></a>CRBMap::Lookup  
 调用此方法以查找密钥或中的值`CRBMap`对象。  
  
```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const throw(...);
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>参数  
 `key`  
 指定标识要查找的元素的键。  
  
 *值*  
 接收的查阅到值的变量。  
  
### <a name="return-value"></a>返回值  
 第一种形式的方法返回 true，如果找到项，否则为 false。 第二个和第三个窗体返回一个指向[CPair](crbtree-class.md#cpair_class)。  
  
### <a name="remarks"></a>备注  
 请参阅的文档的基类[CRBTree](../../atl/reference/crbtree-class.md)有关可用的其他方法的信息。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#82](../../atl/codesnippet/cpp/crbmap-class_2.cpp)]  
  
##  <a name="removekey"></a>CRBMap::RemoveKey  
 调用此方法以删除从元素`CRBMap`给定键的对象。  
  
```
bool RemoveKey(KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>参数  
 `key`  
 你想要删除的元素对相应的密钥。  
  
### <a name="return-value"></a>返回值  
 如果找到并移除，false 失败该键，则返回 true。  
  
### <a name="remarks"></a>备注  
 请参阅的文档的基类[CRBTree](../../atl/reference/crbtree-class.md)有关可用的其他方法的信息。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#83](../../atl/codesnippet/cpp/crbmap-class_3.cpp)]  
  
##  <a name="setat"></a>CRBMap::SetAt  
 调用此方法以插入到映射的元素对。  
  
```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `key`  
 密钥的值将添加到`CRBMap`对象。  
  
 *值*  
 要添加到值`CRBMap`对象。  
  
### <a name="return-value"></a>返回值  
 返回的位置中的键/值元素对`CRBMap`对象。  
  
### <a name="remarks"></a>备注  
 `SetAt`如果找到匹配的键，将替换现有元素。 如果未找到项，都要创建新的键/值对。  
  
 请参阅的文档的基类[CRBTree](../../atl/reference/crbtree-class.md)有关可用的其他方法的信息。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#84](../../atl/codesnippet/cpp/crbmap-class_4.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [CRBTree 类](../../atl/reference/crbtree-class.md)   
 [CAtlMap 类](../../atl/reference/catlmap-class.md)   
 [CRBMultiMap 类](../../atl/reference/crbmultimap-class.md)   
 [类概述](../../atl/atl-class-overview.md)
