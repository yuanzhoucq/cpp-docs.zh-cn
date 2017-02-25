---
title: "CTypedPtrList Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CTypedPtrList"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTypedPtrList class"
  - "linked lists [C++]"
  - "lists [C++]"
  - "pointer lists"
  - "template classes, CTypedPtrList class"
  - "type-safe collections"
ms.assetid: c273096e-1756-4340-864b-4a08b674a65e
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CTypedPtrList Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

为选件类提供类型安全的“包装” `CPtrList`对象。  
  
## 语法  
  
```  
template< class BASE_CLASS, class TYPE >  
class CTypedPtrList : public BASE_CLASS  
```  
  
#### 参数  
 `BASE_CLASS`  
 类型化指针的基类列表选件类;必须是指向列表选件类\(`CObList` 或 `CPtrList`）。  
  
 `TYPE`  
 在基类存储元素的类型的列表。  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CTypedPtrList::AddHead](../Topic/CTypedPtrList::AddHead.md)|添加一个元素\(或在其他元素中的所有元素列表\)添加到列表的开头\(用于新头）。|  
|[CTypedPtrList::AddTail](../Topic/CTypedPtrList::AddTail.md)|添加一个元素\(或在其他元素中的所有元素列表\)添加到列表尾\(提交新的尾）。|  
|[CTypedPtrList::GetAt](../Topic/CTypedPtrList::GetAt.md)|获取元素在特定位置。|  
|[CTypedPtrList::GetHead](../Topic/CTypedPtrList::GetHead.md)|返回列表的head元素\(不能为空）。|  
|[CTypedPtrList::GetNext](../Topic/CTypedPtrList::GetNext.md)|获取重复的下一个元素。|  
|[CTypedPtrList::GetPrev](../Topic/CTypedPtrList::GetPrev.md)|获取重复上一个元素。|  
|[CTypedPtrList::GetTail](../Topic/CTypedPtrList::GetTail.md)|返回列表尾元素\(不能为空）。|  
|[CTypedPtrList::RemoveHead](../Topic/CTypedPtrList::RemoveHead.md)|从列表的开头移除元素。|  
|[CTypedPtrList::RemoveTail](../Topic/CTypedPtrList::RemoveTail.md)|从列表尾移除元素。|  
|[CTypedPtrList::SetAt](../Topic/CTypedPtrList::SetAt.md)|将该元素在特定位置。|  
  
## 备注  
 当您使用 `CTypedPtrList` 而不是 `CObList` 或 `CPtrList`时，类型检查计算机帮助的C\+\+消除不匹配的指针类型引起的错误。  
  
 此外，`CTypedPtrList` 包装执行所需的大部分强制转换是否使用了 `CObList` 或 `CPtrList`。  
  
 由于所有 `CTypedPtrList` 函数内联，该模板的使用不显着影响您的代码的大小或速度。  
  
 列出从 `CObList` 派生的可序列化，但是，从 `CPtrList` 派生的那些不可以。  
  
 当 `CTypedPtrList` 对象被删除，或者，如果移除元素，因此，只有这些引用移除的指针，而不是实体。  
  
 有关使用 `CTypedPtrList`的更多信息，请参见位于 [集合](../../mfc/collections.md) 和 [基于模板的选件类](../../mfc/template-based-classes.md)。  
  
## 示例  
 此示例创建 `CTypedPtrList`实例，添加一个对象，序列化列表到磁盘，然后删除对象:  
  
 [!code-cpp[NVC_MFCCollections#110](../../mfc/codesnippet/CPP/ctypedptrlist-class_1.cpp)]  
  
 [!code-cpp[NVC_MFCCollections#111](../../mfc/codesnippet/CPP/ctypedptrlist-class_2.cpp)]  
  
## 继承层次结构  
 `BASE_CLASS`  
  
 `_CTypedPtrList`  
  
 `CTypedPtrList`  
  
## 要求  
 **Header:** afxtempl.h  
  
## 请参阅  
 [MFC示例集合](../../top/visual-cpp-samples.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CPtrList Class](../../mfc/reference/cptrlist-class.md)   
 [CObList Class](../../mfc/reference/coblist-class.md)