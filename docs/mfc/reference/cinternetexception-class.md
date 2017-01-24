---
title: "CInternetException Class | Microsoft Docs"
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
  - "CInternetException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CInternetException class"
  - "异常处理, Internet operations"
  - "异常, Internet"
ms.assetid: 44fb3cbe-523e-4754-8843-a77909990b14
caps.latest.revision: 22
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CInternetException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示异常条件与Internet操作相关。  
  
## 语法  
  
```  
class CInternetException : public CException  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CInternetException::CInternetException](../Topic/CInternetException::CInternetException.md)|构造 `CInternetException` 对象。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CInternetException::m\_dwContext](../Topic/CInternetException::m_dwContext.md)|上下文关联的值导致异常的操作。|  
|[CInternetException::m\_dwError](../Topic/CInternetException::m_dwError.md)|导致异常的错误。|  
  
## 备注  
 `CInternetException` 选件类包含两个公共数据成员:一对错误代码负都具有关联的异常，同时，其他保留Internet应用程序的上下文标识符与该错误。  
  
 有关Internet应用程序的上下文标识符的更多信息，请参见文章 [编程时WinInet的Internet](../../mfc/win32-internet-extensions-wininet.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CInternetException`  
  
## 要求  
 **Header:** afxinet.h  
  
## 请参阅  
 [CException Class](../../mfc/reference/cexception-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CException Class](../../mfc/reference/cexception-class.md)