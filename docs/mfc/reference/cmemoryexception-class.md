---
title: "CMemoryException Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMemoryException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C++ 异常处理, 内存"
  - "CMemoryException class"
  - "异常, memory type"
  - "memory exceptions"
  - "内存, 异常处理"
ms.assetid: 9af0ed57-d12a-45ca-82b5-c910a60f7edf
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CMemoryException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示内存不足异常的条件。  
  
## 语法  
  
```  
class CMemoryException : public CSimpleException  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMemoryException::CMemoryException](../Topic/CMemoryException::CMemoryException.md)|构造 `CMemoryException` 对象。|  
  
## 备注  
 进一步评估不需要或可能的。  内存异常。**new**自动引发。  如果您编写记忆函数，使用 `malloc`，例如，则负责内存引发异常。  
  
 有关 `CMemoryException`的更多信息，请参见文章 [异常处理\(MFC\)](../../mfc/exception-handling-in-mfc.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CMemoryException`  
  
## 要求  
 **Header:** afx.h  
  
## 请参阅  
 [CException Class](../../mfc/reference/cexception-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)