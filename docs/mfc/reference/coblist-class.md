---
title: "CObList Class | Microsoft Docs"
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
  - "CObList"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CObList class"
  - "列表, 对象"
  - "对象 [C++], lists of"
ms.assetid: 80699c93-33d8-4f8b-b8cf-7b58aeab64ca
caps.latest.revision: 20
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CObList Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

支持可访问按顺序排序的列表不唯一的 `CObject` 的指针或通过指针值。  
  
## 语法  
  
```  
class CObList : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CObList::CObList](../Topic/CObList::CObList.md)|构造null用作 `CObject` 指针列表。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CObList::AddHead](../Topic/CObList::AddHead.md)|添加一个元素\(或在其他元素中的所有元素列表\)添加到列表的开头\(用于新头）。|  
|[CObList::AddTail](../Topic/CObList::AddTail.md)|添加一个元素\(或在其他元素中的所有元素列表\)添加到列表尾\(提交新的尾）。|  
|[CObList::Find](../Topic/CObList::Find.md)|获取指针值指定元素的位置。|  
|[CObList::FindIndex](../Topic/CObList::FindIndex.md)|获取从零开始的索引指定元素的位置。|  
|[CObList::GetAt](../Topic/CObList::GetAt.md)|获取元素在特定位置。|  
|[CObList::GetCount](../Topic/CObList::GetCount.md)|中返回元素数列表。|  
|[CObList::GetHead](../Topic/CObList::GetHead.md)|返回列表的head元素\(不能为空）。|  
|[CObList::GetHeadPosition](../Topic/CObList::GetHeadPosition.md)|返回列表的head元素的位置。|  
|[CObList::GetNext](../Topic/CObList::GetNext.md)|获取重复的下一个元素。|  
|[CObList::GetPrev](../Topic/CObList::GetPrev.md)|获取重复上一个元素。|  
|[CObList::GetSize](../Topic/CObList::GetSize.md)|中返回元素数列表。|  
|[CObList::GetTail](../Topic/CObList::GetTail.md)|返回列表尾元素\(不能为空）。|  
|[CObList::GetTailPosition](../Topic/CObList::GetTailPosition.md)|返回列表尾元素的位置。|  
|[CObList::InsertAfter](../Topic/CObList::InsertAfter.md)|插入到特定位置之后的一个新的元素。|  
|[CObList::InsertBefore](../Topic/CObList::InsertBefore.md)|插入到特定位置之前的一个新的元素。|  
|[CObList::IsEmpty](../Topic/CObList::IsEmpty.md)|测试空列表情况\(而不是元素）。|  
|[CObList::RemoveAll](../Topic/CObList::RemoveAll.md)|从此移除所有元素的列表。|  
|[CObList::RemoveAt](../Topic/CObList::RemoveAt.md)|从此移除元素列表，指定的位置。|  
|[CObList::RemoveHead](../Topic/CObList::RemoveHead.md)|从列表的开头移除元素。|  
|[CObList::RemoveTail](../Topic/CObList::RemoveTail.md)|从列表尾移除元素。|  
|[CObList::SetAt](../Topic/CObList::SetAt.md)|将该元素在特定位置。|  
  
## 备注  
 `CObList` 列表的行为，如二进制文件链接列表。  
  
 类型 **POSITION** 的变量是列表的密钥。  可以使用 **POSITION** 变量作为迭代器按顺序遍历和作为书签保存位置。  但是位置不相同。索引。  
  
 插入元素非常快地在列表中前面，在尾和在已知的 **POSITION**。  一个顺序搜索需要按值或索引查找元素。  如果列表很长，此搜索可能会很慢。  
  
 `CObList` 合并 `IMPLEMENT_SERIAL` 宏支持序列化和转储其元素。  如果 `CObject` 指针列表存储到存档，与重载、运算符或与 `Serialize` 成员函数，而后者又序列化每个 `CObject` 元素。  
  
 如果您在列表中需要各个 `CObject` 元素转储，必须将转储上下文的深度为1或更大。  
  
 当 `CObList` 对象被删除，或者，如果移除元素，因此，只有这些引用移除的 `CObject` 指针，而不是对象。  
  
 可以从 `CObList`派生您的选件类。  在新列表选件类，用于存储指针从 `CObject`派生的对象，添加新数据成员和新成员函数。  请注意结果列表不是严格类型安全，因为它允许所有 `CObject` 指针的插入。  
  
> [!NOTE]
>  因此，如果您希望序列化列表，则在派生类中实现必须使用 [IMPLEMENT\_SERIAL](../Topic/IMPLEMENT_SERIAL.md) 宏。  
  
 有关使用 `CObList`的更多信息，请参见文章 [集合](../../mfc/collections.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CObList`  
  
## 要求  
 **Header:** afxcoll.h  
  
## 请参阅  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CStringList Class](../../mfc/reference/cstringlist-class.md)   
 [CPtrList Class](../../mfc/reference/cptrlist-class.md)