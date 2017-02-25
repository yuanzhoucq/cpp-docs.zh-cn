---
title: "CPtrList Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CPtrList"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPtrList class"
  - "generic lists"
  - "列表, generic"
ms.assetid: 4139a09c-4338-4f42-9eea-51336120b43c
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CPtrList Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

支持某些 void 指针列表。  
  
## 语法  
  
```  
class CPtrList : public CObject  
```  
  
## 成员  
 `CPtrList` 的成员函数类似于类 [CObList](../../mfc/reference/coblist-class.md)的成员函数。  由于相似性，你可以使用 `CObList` 参考文档成员函数。  无论在哪里看见 `CObject` 指针作为函数参数或返回值，替换指为 `void`。  
  
 `CObject*& CObList::GetHead() const;`  
  
 例如，转换为  
  
 `void*& CPtrList::GetHead() const;`  
  
## 备注  
 `CPtrList` 合并 `IMPLEMENT_DYNAMIC` 宏来支持运行时类型访问和转储到 `CDumpContext` 对象。  如果需要单独指针转储列表元素，则必须设置转储上下文的深度为 1 或更大。  
  
 指针列表不能序列化。  
  
 当 `CPtrList` 对象被删除，或者，当元素被移除，只有这些指针被移除，而不是他们应用的实体。  
  
 有关使用 `CPtrList` 的更多信息，请参见文章[Collections](../../mfc/collections.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CPtrList`  
  
## 要求  
 **Header:** afxcoll.h  
  
## 请参阅  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CObList Class](../../mfc/reference/coblist-class.md)