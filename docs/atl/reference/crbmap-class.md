---
title: "CRBMap Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CRBMap"
  - "CRBMap"
  - "ATL::CRBMap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRBMap class"
ms.assetid: 658e94dc-e835-4356-aed1-1513e1f66969
caps.latest.revision: 18
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRBMap Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用红色黑色二叉树，此选件类表示一个映射的结构。  
  
## 语法  
  
```  
  
      template<   
   typename K,  
   typename V,  
   class KTraits = CElementTraits< K >,  
   class VTraits = CElementTraits< V >   
> class CRBMap : public CRBTree< K, V, KTraits, VTraits >  
```  
  
#### 参数  
 `K`  
 关键元素类型。  
  
 *V*  
 值元素类型。  
  
 `KTraits`  
 用于的代码复制或移动关键元素。  有关详细信息 [CElementTraits选件类](../../atl/reference/celementtraits-class.md) 参见。  
  
 `VTraits`  
 用于的代码复制或移动值元素。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CRBMap::CRBMap](../Topic/CRBMap::CRBMap.md)|构造函数。|  
|[CRBMap::~CRBMap](../Topic/CRBMap::~CRBMap.md)|该析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CRBMap::Lookup](../Topic/CRBMap::Lookup.md)|调用此方法查找键或值。`CRBMap` 对象。|  
|[CRBMap::RemoveKey](../Topic/CRBMap::RemoveKey.md)|调用此方法从 `CRBMap` 对象中移除元素命名键。|  
|[CRBMap::SetAt](../Topic/CRBMap::SetAt.md)|调用此方法将一对元素添加到映射中插入。|  
  
## 备注  
 `CRBMap` 提供用于映射的一些任何给定类型的支持，管理经过排序的关键元素及其关联的值。  每个键只能有一个关联的值。  元素\(其中包括注册表项和值\)使用 [CRBMap::SetAt](../Topic/CRBMap::SetAt.md) 方法，在二进制树结构存储。  使用 [CRBMap::RemoveKey](../Topic/CRBMap::RemoveKey.md) 方法，元素可以将其移除，删除与特定的值的元素。  
  
 遍历树使得对方法\(如 [CRBTree::GetHeadPosition](../Topic/CRBTree::GetHeadPosition.md)、 [CRBTree::GetNext](../Topic/CRBTree::GetNext.md)和 [CRBTree::GetNextValue](../Topic/CRBTree::GetNextValue.md)。  
  
 `KTraits` 和 `VTraits` 参数是包含必需的全部将代码复制或移动元素的特征选件类。  
  
 `CRBMap` 从 [CRBTree](../../atl/reference/crbtree-class.md)派生，使用红色黑色算法，实现二叉树。  [CRBMultiMap](../../atl/reference/crbmultimap-class.md) 是允许每个键的多个值的变体。  它还 `CRBTree`从派生并使用 `CRBMap`共享许多功能。  
  
 [CAtlMap](../../atl/reference/catlmap-class.md) 选件类提供对两 `CRBMap` 和 `CRBMultiMap` 的替代方法。  当需要存储时只有少量元素，请考虑使用 [CSimpleMap](../../atl/reference/csimplemap-class.md) 选件类。  
  
 有关各种集合选件类及其功能和性能特征的更完整的讨论，请参见 [ATL 集合选件类](../../atl/atl-collection-classes.md)。  
  
## 继承层次结构  
 [CRBTree](../../atl/reference/crbtree-class.md)  
  
 `CRBMap`  
  
## 要求  
 **Header:** atlcoll.h  
  
## 请参阅  
 [CRBTree Class](../../atl/reference/crbtree-class.md)   
 [CAtlMap Class](../../atl/reference/catlmap-class.md)   
 [CRBMultiMap Class](../../atl/reference/crbmultimap-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)