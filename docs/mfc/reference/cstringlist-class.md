---
title: "CStringList Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CStringList"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStringList class"
  - "列表, string"
  - "字符串 [C++], 集合"
  - "字符串 [C++], 列表"
ms.assetid: 310a7edb-263c-4bd2-ac43-0bfbfddc5a33
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# CStringList Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

支持列表 `CString` 对象。  
  
## 语法  
  
```  
class CStringList : public CObject  
```  
  
## 成员  
 `CStringList` 的成员函数类似于选件类 [CObList](../../mfc/reference/coblist-class.md)的成员函数。  因此相似性，可以使用 `CObList` 引用成员函数特定的文档。  无论在何处参见 `CObject` 指针，则返回值，并 `CString` \(不是 `CString` 指针）。  无论在何处参见 `CObject` 指针作为函数参数，请替换 `LPCTSTR`。  
  
 `CObject*& CObList::GetHead() const;`  
  
 例如，转换  
  
 `CString& CStringList::GetHead() const;`  
  
 和  
  
 `POSITION AddHead( CObject* <newElement> );`  
  
 转换  
  
 `POSITION AddHead( LPCTSTR <newElement> );`  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CObList::CObList](../Topic/CObList::CObList.md)|构造空列表。|  
  
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
 所有比较的值完成，这意味着在字符串的字符进行比较而不是字符串的地址。  
  
 `CStringList` 合并 `IMPLEMENT_SERIAL` 宏支持序列化和转储其元素。  如果 `CString` 对象列表存储到存档，与重载、运算符或与 `Serialize` 成员函数，而后者又序列化每个 `CString` 元素。  
  
 如果需要各个 `CString` 元素转储，必须将转储上下文的深度为1或更大。  
  
 有关使用 `CStringList`的更多信息，请参见文章 [集合](../../mfc/collections.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CStringList`  
  
## 要求  
 **Header:** afxcoll.h  
  
## 请参阅  
 [MFC示例集合](../../top/visual-cpp-samples.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)