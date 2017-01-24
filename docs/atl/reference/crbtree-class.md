---
title: "CRBTree Class | Microsoft Docs"
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
  - "ATL.CRBTree"
  - "CRBTree"
  - "ATL::CRBTree"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRBTree class"
ms.assetid: a1b1cb63-38e4-4fc2-bb28-f774d1721760
caps.latest.revision: 18
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRBTree Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类是创建和使用红色黑色树的方法。  
  
## 语法  
  
```  
  
      template<  
   typename K,  
   typename V,  
   class KTraits = CElementTraits< K >,  
   class VTraits = CElementTraits< V >  
> class CRBTree  
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
  
### 公共 Typedefs  
  
|名称|说明|  
|--------|--------|  
|[CRBTree::KINARGTYPE](../Topic/CRBTree::KINARGTYPE.md)|使用的类型的键，以将作为输入参数。|  
|[CRBTree::KOUTARGTYPE](../Topic/CRBTree::KOUTARGTYPE.md)|使用的类型，而该返回作为输出参数。|  
|[CRBTree::VINARGTYPE](../Topic/CRBTree::VINARGTYPE.md)|使用的类型，该值作为输入参数。|  
|[CRBTree::VOUTARGTYPE](../Topic/CRBTree::VOUTARGTYPE.md)|使用的类型，该值将作为输出参数。|  
  
### 公共类  
  
|名称|说明|  
|--------|--------|  
|[CRBTree::CPair Class](../Topic/CRBTree::CPair%20Class.md)|一个包含键和值的元素的选件类。|  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CRBTree::~CRBTree](../Topic/CRBTree::~CRBTree.md)|该析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CRBTree::FindFirstKeyAfter](../Topic/CRBTree::FindFirstKeyAfter.md)|调用此方法可查找使用下一个可用的关键元素的位置。|  
|[CRBTree::GetAt](../Topic/CRBTree::GetAt.md)|调用此方法获取元素在树中的特定位置。|  
|[CRBTree::GetCount](../Topic/CRBTree::GetCount.md)|调用此方法获取元素数在树的。|  
|[CRBTree::GetHeadPosition](../Topic/CRBTree::GetHeadPosition.md)|调用此方法获取元素的位置值在树的开头。|  
|[CRBTree::GetKeyAt](../Topic/CRBTree::GetKeyAt.md)|调用此方法获取给定位置的键在树。|  
|[CRBTree::GetNext](../Topic/CRBTree::GetNext.md)|调用此方法获取指向在 `CRBTree` 对象存储的元素，并使该位置到下一个元素。|  
|[CRBTree::GetNextAssoc](../Topic/CRBTree::GetNextAssoc.md)|调用此方法获取在将存储的元素的键和值和高级该位置到下一个元素。|  
|[CRBTree::GetNextKey](../Topic/CRBTree::GetNextKey.md)|调用此方法获取在树中存储的元素的键和高级该位置到下一个元素。|  
|[CRBTree::GetNextValue](../Topic/CRBTree::GetNextValue.md)|调用此方法获取在树中存储的元素的值和高级该位置到下一个元素。|  
|[CRBTree::GetPrev](../Topic/CRBTree::GetPrev.md)|调用此方法获取指向在 `CRBTree` 对象存储的组件，然后更新该位置到以前的元素。|  
|[CRBTree::GetTailPosition](../Topic/CRBTree::GetTailPosition.md)|调用此方法获取元素的位置值在树的尾。|  
|[CRBTree::GetValueAt](../Topic/CRBTree::GetValueAt.md)|调用此方法检索值存储在 `CRBTree` 对象的特定位置。|  
|[CRBTree::IsEmpty](../Topic/CRBTree::IsEmpty.md)|调用此方法测试空树对象。|  
|[CRBTree::RemoveAll](../Topic/CRBTree::RemoveAll.md)|调用此方法从 **CRBTree** 对象中移除所有元素。|  
|[CRBTree::RemoveAt](../Topic/CRBTree::RemoveAt.md)|调用此方法会移除该元素在 **CRBTree** 对象的特定位置。|  
|[CRBTree::SetValueAt](../Topic/CRBTree::SetValueAt.md)|调用此方法将值存储在 `CRBTree` 对象的特定位置。|  
  
## 备注  
 红色黑色树是使用多余位信息每个节点确保的二进制搜索树它保持“平衡，”即树高度不增大不均衡大并不会影响性能。  
  
 此模板选件类旨在 [CRBMap](../../atl/reference/crbmap-class.md) 和 [CRBMultiMap](../../atl/reference/crbmultimap-class.md)使用。  组成这些派生类 `CRBTree`提供方法的大部分。  
  
 有关各种集合选件类及其功能和性能特征的更完整的讨论，请参见 [ATL 集合选件类](../../atl/atl-collection-classes.md)。  
  
## 要求  
 **Header:** atlcoll.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)