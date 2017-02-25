---
title: "CInvalidArgException Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CInvalidArgException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CInvalidArgException class"
ms.assetid: e43d7c67-1157-47f8-817a-804083e8186e
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# CInvalidArgException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类表示一个无效参数异常条件。  
  
## 语法  
  
```  
  
class CInvalidArgException : public CSimpleException  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CInvalidArgException::CInvalidArgException](../Topic/CInvalidArgException::CInvalidArgException.md)|构造函数。|  
  
## 备注  
 `CInvalidArgException` 对象表示无效参数异常条件。  
  
 有关异常处理的更多信息，请参见 [CException选件类](../../mfc/reference/cexception-class.md) 主题和 [异常处理\(MFC\)](../../mfc/exception-handling-in-mfc.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CInvalidArgException`  
  
## 要求  
 **Header:** afx.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CSimpleException Class](../../mfc/reference/csimpleexception-class.md)