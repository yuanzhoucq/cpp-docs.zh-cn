---
title: "CAtlList Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CAtlList"
  - "CAtlList"
  - "ATL::CAtlList"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlList class"
ms.assetid: 09e98053-64b2-4efa-99ab-d0542caaf981
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CAtlList Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类为创建和管理列表对象的方法。  
  
## 语法  
  
```  
  
      template<  
   typename E,  
   class ETraits = CElementTraits< E >  
>  
class CAtlList  
```  
  
#### 参数  
 `E`  
 元素类型。  
  
 `ETraits`  
 用于的代码复制或移动元素。  有关详细信息 [CElementTraits选件类](../../atl/reference/celementtraits-class.md) 参见。  
  
## 成员  
  
### 公共 Typedefs  
  
|名称|描述|  
|--------|--------|  
|[CAtlList::INARGTYPE](../Topic/CAtlList::INARGTYPE.md)||  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[CAtlList::CAtlList](../Topic/CAtlList::CAtlList.md)|构造函数。|  
|[CAtlList::~CAtlList](../Topic/CAtlList::~CAtlList.md)|该析构函数。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CAtlList::AddHead](../Topic/CAtlList::AddHead.md)|调用此方法将元素添加到列表的开头。|  
|[CAtlList::AddHeadList](../Topic/CAtlList::AddHeadList.md)|调用此方法将现有列表到列表的开头。|  
|[CAtlList::AddTail](../Topic/CAtlList::AddTail.md)|调用此方法将元素添加到此的尾列表。|  
|[CAtlList::AddTailList](../Topic/CAtlList::AddTailList.md)|调用此方法将现有列表。此的尾列表。|  
|[CAtlList::AssertValid](../Topic/CAtlList::AssertValid.md)|调用此方法确认列表是有效的。|  
|[CAtlList::Find](../Topic/CAtlList::Find.md)|调用此方法搜索列表所指定的元素。|  
|[CAtlList::FindIndex](../Topic/CAtlList::FindIndex.md)|调用此方法来获取元素的位置命名索引值。|  
|[CAtlList::GetAt](../Topic/CAtlList::GetAt.md)|调用此方法返回元素在列表中的指定位置。|  
|[CAtlList::GetCount](../Topic/CAtlList::GetCount.md)|调用此方法返回对象数列表中的。|  
|[CAtlList::GetHead](../Topic/CAtlList::GetHead.md)|调用此方法返回元素列表的开头。|  
|[CAtlList::GetHeadPosition](../Topic/CAtlList::GetHeadPosition.md)|调用此方法来获取列表的开头的位置。|  
|[CAtlList::GetNext](../Topic/CAtlList::GetNext.md)|调用此方法返回列表中的下一个元素。|  
|[CAtlList::GetPrev](../Topic/CAtlList::GetPrev.md)|调用此方法返回列表中的上一个元素。|  
|[CAtlList::GetTail](../Topic/CAtlList::GetTail.md)|调用此方法返回元素在列表尾。|  
|[CAtlList::GetTailPosition](../Topic/CAtlList::GetTailPosition.md)|调用此方法来获取列表尾的位置。|  
|[CAtlList::InsertAfter](../Topic/CAtlList::InsertAfter.md)|调用此方法将插入一个新元素到列表中在指定的位置之后。|  
|[CAtlList::InsertBefore](../Topic/CAtlList::InsertBefore.md)|调用此方法将插入一个新元素到列表中在指定的位置之前。|  
|[CAtlList::IsEmpty](../Topic/CAtlList::IsEmpty.md)|调用此方法来确定列表是否为空。|  
|[CAtlList::MoveToHead](../Topic/CAtlList::MoveToHead.md)|调用此方法将指定的元素移到列表的开头。|  
|[CAtlList::MoveToTail](../Topic/CAtlList::MoveToTail.md)|调用此方法将指定的元素移到列表尾。|  
|[CAtlList::RemoveAll](../Topic/CAtlList::RemoveAll.md)|调用此方法从列表中移除所有元素。|  
|[CAtlList::RemoveAt](../Topic/CAtlList::RemoveAt.md)|调用此方法从列表中移除一个元素。|  
|[CAtlList::RemoveHead](../Topic/CAtlList::RemoveHead.md)|调用此方法移除元素列表的开头。|  
|[CAtlList::RemoveHeadNoReturn](../Topic/CAtlList::RemoveHeadNoReturn.md)|调用此方法移除元素列表中的前面，而无需返回值。|  
|[CAtlList::RemoveTail](../Topic/CAtlList::RemoveTail.md)|调用此方法会移除该元素在列表尾。|  
|[CAtlList::RemoveTailNoReturn](../Topic/CAtlList::RemoveTailNoReturn.md)|调用此方法会移除该元素在列表尾，而不返回值。|  
|[CAtlList::SetAt](../Topic/CAtlList::SetAt.md)|调用此方法将该元素的值在列表的特定位置。|  
|[CAtlList::SwapElements](../Topic/CAtlList::SwapElements.md)|调用此方法交换列表中的元素。|  
  
## 备注  
 `CAtlList` 选件类支持可访问按顺序排序的列表不唯一的对象或通过值传递。  如双向链接列表，`CAtlList` 列表的行为方式。  每个列表包含头和尾，并且，新元素\(或在某些情况下列表\)可以添加到列表中的任何一个结尾或在特定元素之前或之后插入。  
  
 大多数 `CAtlList` 方法利用位置值。  方法使用该值来引用元素存储的物理内存位置，不应直接计算或预测。  如果访问需要列表中的 *第n个*元素，该方法 [CAtlList::FindIndex](../Topic/CAtlList::FindIndex.md) 将返回给定索引处开始的相应位置值。  方法 [CAtlList::GetNext](../Topic/CAtlList::GetNext.md) 和 [CAtlList::GetPrev](../Topic/CAtlList::GetPrev.md) 可用于遍历列表中的对象重复。  
  
 有关集合选件类的更多信息可用于ATL，请参见 [ATL集合选件类](../../atl/atl-collection-classes.md)。  
  
## 要求  
 **Header:** atlcoll.h  
  
## 请参阅  
 [CList Class](../../mfc/reference/clist-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)