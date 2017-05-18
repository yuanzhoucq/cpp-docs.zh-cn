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
caps.latest.revision: 18
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 7b1cd9e54a18746e26929e9768a990bbe0ba6553
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="crbmap-class"></a>CRBMap 类
此类表示一个映射结构中，使用红黑二进制树。  
  
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
 用于复制或移动关键元素的代码。 请参阅[CElementTraits 类](../../atl/reference/celementtraits-class.md)的更多详细信息。  
  
 `VTraits`  
 用于复制或移动值元素的代码。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CRBMap::CRBMap](#crbmap)|构造函数。|  
|[CRBMap:: ~ CRBMap](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CRBMap::Lookup](#lookup)|调用此方法来查找键或值的`CRBMap`对象。|  
|[CRBMap::RemoveKey](#removekey)|调用此方法来删除从元素`CRBMap`给定键的对象。|  
|[CRBMap::SetAt](#setat)|调用此方法来插入到映射的元素对。|  
  
## <a name="remarks"></a>备注  
 `CRBMap`为管理有序的数组关键元素及其关联的任何的值给定类型的映射数组提供支持。 每个键可以只有一个相关联的值。 元素 （包含一个键和值） 存储在二进制树的结构，使用[CRBMap::SetAt](#setat)方法。 可以使用删除元素[CRBMap::RemoveKey](#removekey)方法，这将删除具有给定键的值的元素。  
  
 遍历树可使用方法如[CRBTree::GetHeadPosition](../../atl/reference/crbtree-class.md#getheadposition)， [CRBTree::GetNext](../../atl/reference/crbtree-class.md#getnext)，和[CRBTree::GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue)。  
  
 `KTraits`和`VTraits`参数是包含复制或移动元素所需的任何补充代码的特征类。  
  
 `CRBMap`派生自[CRBTree](../../atl/reference/crbtree-class.md)，用来实现使用红黑算法的二进制树。 [CRBMultiMap](../../atl/reference/crbmultimap-class.md)是允许多个值对于每个键的变体。 它太派生自`CRBTree`，并因此共享许多功能与`CRBMap`。  
  
 替代这两`CRBMap`和`CRBMultiMap`提供的[CAtlMap](../../atl/reference/catlmap-class.md)类。 当只是少数元素需要存储时，请考虑使用[CSimpleMap](../../atl/reference/csimplemap-class.md)类。  
  
 有关更完整的各种集合类及其功能和性能特征的讨论，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CRBTree](../../atl/reference/crbtree-class.md)  
  
 `CRBMap`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcoll.h  
  
##  <a name="crbmap"></a>CRBMap::CRBMap  
 构造函数。  
  
```
explicit CRBMap(size_t nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>参数  
 `nBlockSize`  
 块大小。  
  
### <a name="remarks"></a>备注  
 `nBlockSize`参数是分配一个新元素时所需的内存量的度量值。 更大的块大小减少对内存分配例程的调用，但使用更多的资源。 一次，默认值将为 10 个元素分配空间。  
  
 请参阅的文档的基类[CRBTree](../../atl/reference/crbtree-class.md)有关可用的其他方法的信息。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&81;](../../atl/codesnippet/cpp/crbmap-class_1.cpp)]  
  
##  <a name="dtor"></a>CRBMap:: ~ CRBMap  
 析构函数。  
  
```
~CRBMap() throw();
```  
  
### <a name="remarks"></a>备注  
 释放任何已分配的资源。  
  
 请参阅的文档的基类[CRBTree](../../atl/reference/crbtree-class.md)有关可用的其他方法的信息。  
  
##  <a name="lookup"></a>CRBMap::Lookup  
 调用此方法来查找键或值的`CRBMap`对象。  
  
```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const throw(...);
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>参数  
 `key`  
 指定用于标识要查找的元素的键。  
  
 *值*  
 接收查阅到值的变量。  
  
### <a name="return-value"></a>返回值  
 该方法的第一种形式返回如果找到了项，否则为 false，则返回 true。 第二个和第三个窗体返回一个指向[CPair](crbtree-class.md#cpair_class)。  
  
### <a name="remarks"></a>备注  
 请参阅的文档的基类[CRBTree](../../atl/reference/crbtree-class.md)有关可用的其他方法的信息。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&82;](../../atl/codesnippet/cpp/crbmap-class_2.cpp)]  
  
##  <a name="removekey"></a>CRBMap::RemoveKey  
 调用此方法来删除从元素`CRBMap`给定键的对象。  
  
```
bool RemoveKey(KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>参数  
 `key`  
 你想要删除键相对应的元素对。  
  
### <a name="return-value"></a>返回值  
 如果键是找到并移除，则 false 失败，则返回 true。  
  
### <a name="remarks"></a>备注  
 请参阅的文档的基类[CRBTree](../../atl/reference/crbtree-class.md)有关可用的其他方法的信息。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&83;](../../atl/codesnippet/cpp/crbmap-class_3.cpp)]  
  
##  <a name="setat"></a>CRBMap::SetAt  
 调用此方法来插入到映射的元素对。  
  
```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `key`  
 要添加到密钥值`CRBMap`对象。  
  
 *值*  
 要添加到值`CRBMap`对象。  
  
### <a name="return-value"></a>返回值  
 返回的位置中的键/值元素对`CRBMap`对象。  
  
### <a name="remarks"></a>备注  
 `SetAt`如果找到匹配项，将替换现有元素。 如果未找到该键，则创建新的键/值对。  
  
 请参阅的文档的基类[CRBTree](../../atl/reference/crbtree-class.md)有关可用的其他方法的信息。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&84;](../../atl/codesnippet/cpp/crbmap-class_4.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [CRBTree 类](../../atl/reference/crbtree-class.md)   
 [CAtlMap 类](../../atl/reference/catlmap-class.md)   
 [CRBMultiMap 类](../../atl/reference/crbmultimap-class.md)   
 [类概述](../../atl/atl-class-overview.md)

