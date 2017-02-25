---
title: "CRBMultiMap Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CRBMultiMap"
  - "ATL.CRBMultiMap"
  - "ATL::CRBMultiMap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRBMultiMap class"
ms.assetid: 94d3ec0c-3e30-4ab7-a101-d8da4fb8add3
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CRBMultiMap Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类表示使用红色黑色二叉树，允许每个键可以与多个值，将映射机制。  
  
## 语法  
  
```  
  
      template<  
   typename K,  
   typename V,  
   class KTraits = CElementTraits< K >,  
   class VTraits = CElementTraits< V >  
> class CRBMultiMap : public CRBTree< K, V, KTraits, VTraits >  
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
|[CRBMultiMap::CRBMultiMap](../Topic/CRBMultiMap::CRBMultiMap.md)|构造函数。|  
|[CRBMultiMap::~CRBMultiMap](../Topic/CRBMultiMap::~CRBMultiMap.md)|该析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CRBMultiMap::FindFirstWithKey](../Topic/CRBMultiMap::FindFirstWithKey.md)|调用此方法可查找第一个元素的位置与特定键的。|  
|[CRBMultiMap::GetNextValueWithKey](../Topic/CRBMultiMap::GetNextValueWithKey.md)|调用此方法获取该值与特定键，并更新位置值。|  
|[CRBMultiMap::GetNextWithKey](../Topic/CRBMultiMap::GetNextWithKey.md)|调用此方法获取元素与特定键，并更新位置值。|  
|[CRBMultiMap::Insert](../Topic/CRBMultiMap::Insert.md)|调用此方法将一对元素添加到映射中插入。|  
|[CRBMultiMap::RemoveKey](../Topic/CRBMultiMap::RemoveKey.md)|调用此方法会移除所有特定键的键\/值元素。|  
  
## 备注  
 `CRBMultiMap` 提供用于映射的一些任何给定类型的支持，管理经过排序的关键元素和值。  不同 [CRBMap](../../atl/reference/crbmap-class.md) 选件类，每个键可以与多个值。  
  
 元素\(其中包括注册表项和值\)使用 [CRBMultiMap::Insert](../Topic/CRBMultiMap::Insert.md) 方法，在二进制树结构存储。  使用 [CRBMultiMap::RemoveKey](../Topic/CRBMultiMap::RemoveKey.md) 方法，元素可以将其移除，删除任何元素满足给定键。  
  
 遍历树使得对方法\(如 [CRBTree::GetHeadPosition](../Topic/CRBTree::GetHeadPosition.md)、 [CRBTree::GetNext](../Topic/CRBTree::GetNext.md)和 [CRBTree::GetNextValue](../Topic/CRBTree::GetNextValue.md)。  访问可能会一键多值使用 [CRBMultiMap::FindFirstWithKey](../Topic/CRBMultiMap::FindFirstWithKey.md)、 [CRBMultiMap::GetNextValueWithKey](../Topic/CRBMultiMap::GetNextValueWithKey.md)和 [CRBMultiMap::GetNextWithKey](../Topic/CRBMultiMap::GetNextWithKey.md) 方法是可能的。  在本插图中的 [CRBMultiMap::CRBMultiMap](../Topic/CRBMultiMap::CRBMultiMap.md) 实际上参见示例。  
  
 `KTraits` 和 `VTraits` 参数是包含必需的全部将代码复制或移动元素的特征选件类。  
  
 `CRBMultiMap` 从 [CRBTree](../../atl/reference/crbtree-class.md)派生，使用红色黑色算法，实现二叉树。  [CAtlMap](../../atl/reference/catlmap-class.md) 选件类提供对 `CRBMultiMap` 和 `CRBMap` 的替代方法。  当需要存储时只有少量元素，请考虑使用 [CSimpleMap](../../atl/reference/csimplemap-class.md) 选件类。  
  
 有关各种集合选件类及其功能和性能特征的更完整的讨论，请参见 [ATL 集合选件类](../../atl/atl-collection-classes.md)。  
  
## 继承层次结构  
 [CRBTree](../../atl/reference/crbtree-class.md)  
  
 `CRBMultiMap`  
  
## 要求  
 **Header:** atlcoll.h  
  
## 请参阅  
 [CRBTree Class](../../atl/reference/crbtree-class.md)   
 [CAtlMap Class](../../atl/reference/catlmap-class.md)   
 [CRBMap Class](../../atl/reference/crbmap-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)