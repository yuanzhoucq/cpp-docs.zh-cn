---
title: "CSimpleException Class | Microsoft Docs"
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
  - "CSimpleException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSimpleException class"
ms.assetid: be0eb8ef-e5b9-47d6-b0fb-efaff2d1e666
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSimpleException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类是资源重要MFC异常的基类。  
  
## 语法  
  
```  
  
class AFX_NOVTABLE CSimpleException : public CException  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CSimpleException::CSimpleException](../Topic/CSimpleException::CSimpleException.md)|构造函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CSimpleException::GetErrorMessage](../Topic/CSimpleException::GetErrorMessage.md)|提供有关发生的错误的文本。|  
  
## 备注  
 `CSimpleException` 是资源重要MFC异常并处理的错误消息的基类这种所有权和初始化。  下面选件类使用 `CSimpleException` 作为其基类:  
  
|||  
|-|-|  
|[CMemoryException选件类](../../mfc/reference/cmemoryexception-class.md)|内存不足异常|  
|[CNotSupportedException选件类](../../mfc/reference/cnotsupportedexception-class.md)|要求不支持的操作|  
|[CResourceException选件类](../../mfc/reference/cresourceexception-class.md)|无法创建Windows的资源未找到或|  
|[CUserException选件类](../../mfc/reference/cuserexception-class.md)|指示一个资源的异常找不到|  
|[CInvalidArgException选件类](../../mfc/reference/cinvalidargexception-class.md)|指示无效参数的异常|  
  
 由于 `CSimpleException` 是抽象基类，不能直接声明 `CSimpleException` 对象。  相反，您必须声明派生的对象如上表中。  如果声明您的派生类，请使用上一选件类作为模型。  
  
 有关更多信息，请参见 [CException选件类](../../mfc/reference/cexception-class.md) 主题和 [异常处理\(MFC\)](../../mfc/exception-handling-in-mfc.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CSimpleException`  
  
## 要求  
 **Header:** afx.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CException Class](../../mfc/reference/cexception-class.md)   
 [异常处理](../../mfc/exception-handling-in-mfc.md)