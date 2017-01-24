---
title: "CResourceException Class | Microsoft Docs"
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
  - "CResourceException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CResourceException class"
  - "异常, 资源"
  - "resource allocation exception"
  - "resource exceptions"
  - "资源 [C++], 分配"
ms.assetid: af6ae043-d124-4bfd-b35e-7bb0db67d289
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CResourceException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

生成，当Windows无法找到或分配请求的资源。  
  
## 语法  
  
```  
class CResourceException : public CSimpleException  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CResourceException::CResourceException](../Topic/CResourceException::CResourceException.md)|构造 `CResourceException` 对象。|  
  
## 备注  
 进一步评估不需要或可能的。  
  
 有关使用 `CResourceException`的更多信息，请参见文章 [异常处理\(MFC\)](../../mfc/exception-handling-in-mfc.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CResourceException`  
  
## 要求  
 **标头：**afxwin.h  
  
## 请参阅  
 [CException Class](../../mfc/reference/cexception-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)