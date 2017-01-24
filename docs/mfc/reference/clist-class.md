---
title: "CList Class | Microsoft Docs"
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
  - "CList"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CList class"
  - "列表"
  - "列表, base class for"
ms.assetid: 6f6273c3-c8f6-47f5-ac2a-0a950379ae5d
caps.latest.revision: 23
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CList Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

支持可访问按顺序排序的列表不唯一的对象或通过值传递。  
  
## 语法  
  
```  
template< class TYPE, class ARG_TYPE = const TYPE& >   
class CList : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CList::CList](../Topic/CList::CList.md)|构造空的有序列表。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CList::AddHead](../Topic/CList::AddHead.md)|添加一个元素\(或在其他元素中的所有元素列表\)添加到列表的开头\(用于新头）。|  
|[CList::AddTail](../Topic/CList::AddTail.md)|添加一个元素\(或在其他元素中的所有元素列表\)添加到列表尾\(提交新的尾）。|  
|[CList::Find](../Topic/CList::Find.md)|获取指针值指定元素的位置。|  
|[CList::FindIndex](../Topic/CList::FindIndex.md)|获取从零开始的索引指定元素的位置。|  
|[CList::GetAt](../Topic/CList::GetAt.md)|获取元素在特定位置。|  
|[CList::GetCount](../Topic/CList::GetCount.md)|中返回元素数列表。|  
|[CList::GetHead](../Topic/CList::GetHead.md)|返回列表的head元素\(不能为空）。|  
|[CList::GetHeadPosition](../Topic/CList::GetHeadPosition.md)|返回列表的head元素的位置。|  
|[CList::GetNext](../Topic/CList::GetNext.md)|获取重复的下一个元素。|  
|[CList::GetPrev](../Topic/CList::GetPrev.md)|获取重复上一个元素。|  
|[CList::GetSize](../Topic/CList::GetSize.md)|中返回元素数列表。|  
|[CList::GetTail](../Topic/CList::GetTail.md)|返回列表尾元素\(不能为空）。|  
|[CList::GetTailPosition](../Topic/CList::GetTailPosition.md)|返回列表尾元素的位置。|  
|[CList::InsertAfter](../Topic/CList::InsertAfter.md)|插入到特定位置之后的一个新的元素。|  
|[CList::InsertBefore](../Topic/CList::InsertBefore.md)|插入到特定位置之前的一个新的元素。|  
|[CList::IsEmpty](../Topic/CList::IsEmpty.md)|测试空列表情况\(而不是元素）。|  
|[CList::RemoveAll](../Topic/CList::RemoveAll.md)|从此移除所有元素的列表。|  
|[CList::RemoveAt](../Topic/CList::RemoveAt.md)|从此移除元素列表，指定的位置。|  
|[CList::RemoveHead](../Topic/CList::RemoveHead.md)|从列表的开头移除元素。|  
|[CList::RemoveTail](../Topic/CList::RemoveTail.md)|从列表尾移除元素。|  
|[CList::SetAt](../Topic/CList::SetAt.md)|将该元素在特定位置。|  
  
#### 参数  
 `TYPE`  
 在列表中存储的对象的类型。  
  
 `ARG` *\_* `TYPE`  
 使用的类型引用列表中存储的对象。  可以是引用。  
  
## 备注  
 `CList` 列表的行为，如二进制文件链接列表。  
  
 类型 **POSITION** 的变量是列表的密钥。  可以使用 **POSITION** 变量作为迭代器按顺序遍历和作为书签保存位置。  但是位置不相同。索引。  
  
 插入元素非常快地在列表中前面，在尾和在已知的 **POSITION**。  一个顺序搜索需要按值或索引查找元素。  如果列表很长，此搜索可能会很慢。  
  
 如果您在列表中需要各个元素转储，必须将转储上下文的深度为1或更大。  
  
 此选件类的某些成员函数调用必须自定义为 `CList` 选件类的大多数使用的全局helper函数。  请参见的“宏和Globals”部分中的 [集合选件帮助器类](../../mfc/reference/collection-class-helpers.md)。  
  
 有关使用 `CList`的更多信息，请参见文章 [集合](../../mfc/collections.md)。  
  
## 示例  
 [!code-cpp[NVC_MFCCollections#35](../../mfc/codesnippet/CPP/clist-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CList`  
  
## 要求  
 **Header:** afxtempl.h  
  
## 请参阅  
 [MFC示例集合](../../top/visual-cpp-samples.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CMap Class](../../mfc/reference/cmap-class.md)   
 [CArray Class](../../mfc/reference/carray-class.md)