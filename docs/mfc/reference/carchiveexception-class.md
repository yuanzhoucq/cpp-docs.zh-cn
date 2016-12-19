---
title: "CArchiveException Class | Microsoft Docs"
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
  - "CArchiveException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "archive exceptions [C++]"
  - "CArchiveException class"
  - "exceptions [C++], archive"
  - "exceptions [C++], 序列化"
  - "序列化 [C++], 异常"
ms.assetid: da31a127-e86c-41d1-b0b6-bed0865b1b49
caps.latest.revision: 21
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CArchiveException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示序列化异常条件  
  
## 语法  
  
```  
class CArchiveException : public CException  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CArchiveException::CArchiveException](../Topic/CArchiveException::CArchiveException.md)|构造 `CArchiveException` 对象。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CArchiveException::m\_cause](../Topic/CArchiveException::m_cause.md)|指示异常原因。|  
|[CArchiveException::m\_strFileName](../Topic/CArchiveException::m_strFileName.md)|为此异常条件指定文件的名称。|  
  
## 备注  
 `CArchiveException` 选件类包含指示异常原因的一个公共数据成员。  
  
 `CArchiveException` 对象构造和引发的内部 [CArchive](../../mfc/reference/carchive-class.md) 成员函数。  在 **"CATCH"** 表达式的范围内，您可以访问这些对象。  原因代码是操作系统无关。  有关异常处理的更多信息，请参见 [异常处理\(MFC\)](../../mfc/exception-handling-in-mfc.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CArchiveException`  
  
## 要求  
 **Header:** afx.h  
  
## 请参阅  
 [CException Class](../../mfc/reference/cexception-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CArchive Class](../../mfc/reference/carchive-class.md)   
 [AfxThrowArchiveException](../Topic/AfxThrowArchiveException.md)   
 [异常处理](../../mfc/reference/exception-processing.md)