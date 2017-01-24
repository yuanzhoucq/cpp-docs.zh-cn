---
title: "CFileException Class | Microsoft Docs"
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
  - "CFileException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFile class, exceptions of"
  - "CFileException class"
  - "异常, file type"
ms.assetid: f6491bb9-bfbc-42fd-a952-b33f9b62323f
caps.latest.revision: 20
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CFileException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示一个文件相关的异常条件。  
  
## 语法  
  
```  
class CFileException : public CException  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CFileException::CFileException](../Topic/CFileException::CFileException.md)|构造 `CFileException` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CFileException::ErrnoToException](../Topic/CFileException::ErrnoToException.md)|返回原因代码与一个运行时错误号相对应。|  
|[CFileException::GetErrorMessage](../Topic/CFileException::GetErrorMessage.md)|检索描述异常消息。|  
|[CFileException::OsErrorToException](../Topic/CFileException::OsErrorToException.md)|返回原因代码与操作系统错误代码相对应。|  
|[CFileException::ThrowErrno](../Topic/CFileException::ThrowErrno.md)|引发根据运行时错误号的文件异常。|  
|[CFileException::ThrowOsError](../Topic/CFileException::ThrowOsError.md)|引发基于操作系统错误号的文件异常。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CFileException::m\_cause](../Topic/CFileException::m_cause.md)|包含可移植代码与异常原因对应。|  
|[CFileException::m\_lOsError](../Topic/CFileException::m_lOsError.md)|包含相关操作系统的错误号。|  
|[CFileException::m\_strFileName](../Topic/CFileException::m_strFileName.md)|包含文件名称的此异常的。|  
  
## 备注  
 `CFileException` 选件类包含一个可移植的原因代码和运行SYSTEM特定错误号的公共数据成员。  选件类还提供静态成员函数用于引发的异常文件以及用于返回两个操作系统的错误和C运行时错误的原因代码。  
  
 `CFileException` 构造对象。将引发。`CFile` 成员函数并在派生类中的成员函数。  在 **"CATCH"** 表达式的范围内，您可以访问这些对象。  对于可移植性，仅使用原因代码捕获异常的原因。  有关异常的更多信息，请参见文章 [异常处理\(MFC\)](../../mfc/exception-handling-in-mfc.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CFileException`  
  
## 要求  
 **Header:** afx.h  
  
## 请参阅  
 [CException Class](../../mfc/reference/cexception-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [异常处理](../../mfc/reference/exception-processing.md)