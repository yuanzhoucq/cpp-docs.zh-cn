---
title: "CNotSupportedException Class | Microsoft Docs"
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
  - "CNotSupportedException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CNotSupportedException class"
  - "异常, not supported"
  - "unsupported features"
ms.assetid: e517391b-eb94-4c39-ae32-87b45bf7d624
caps.latest.revision: 20
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CNotSupportedException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示对的结果将不支持的功能的异常。  
  
## 语法  
  
```  
class CNotSupportedException : public CSimpleException  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CNotSupportedException::CNotSupportedException](../Topic/CNotSupportedException::CNotSupportedException.md)|构造 `CNotSupportedException` 对象。|  
  
## 备注  
 进一步评估不需要或可能的。  
  
 有关使用 `CNotSupportedException`的更多信息，请参见文章 [异常处理\(MFC\)](../../mfc/exception-handling-in-mfc.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CNotSupportedException`  
  
## 要求  
 **Header:** afx.h  
  
## 请参阅  
 [CException Class](../../mfc/reference/cexception-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)