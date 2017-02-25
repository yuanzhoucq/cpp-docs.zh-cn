---
title: "CException Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CArchiveException class, 基类"
  - "CDaoException class, 基类"
  - "CDBException class, 基类"
  - "CException class"
  - "CFileException class, 基类"
  - "CInternetException class, 基类"
  - "CMemoryException class, 基类"
  - "CNotSupportedException class, 基类"
  - "COleDispatchException class, 基类"
  - "COleException class, 基类"
  - "CResourceException class, 基类"
  - "CUserException class"
  - "异常, classes for"
  - "宏, 异常处理"
ms.assetid: cfacf14d-bfe4-4666-a5c7-38b800512920
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

所有异常的基类在Microsoft基础选件类库中。  
  
## 语法  
  
```  
class AFX_NOVTABLE CException : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CException::CException](../Topic/CException::CException.md)|构造 `CException` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CException::Delete](../Topic/CException::Delete.md)|删除 `CException` 对象。|  
|[CException::ReportError](../Topic/CException::ReportError.md)|在消息框中显示一条错误信息向用户报告。|  
  
## 备注  
 由于 `CException` 是抽象基类不能直接创建 `CException` 对象;必须创建派生类对象。  如果您需要创建自己的 `CException`样式选件类，请使用作为设计列出的上述派生类之一。  确保您的派生类也使用 `IMPLEMENT_DYNAMIC`。  
  
 派生类及其说明下面所列:  
  
|||  
|-|-|  
|[CSimpleException](../../mfc/reference/csimpleexception-class.md)|资源重要MFC异常的基类|  
|[CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md)|无效参数异常条件|  
|[CMemoryException](../../mfc/reference/cmemoryexception-class.md)|内存不足异常|  
|[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)|要求不支持的操作|  
|[CArchiveException](../../mfc/reference/carchiveexception-class.md)|存档特定异常|  
|[CFileException](../../mfc/reference/cfileexception-class.md)|文件特定异常|  
|[CResourceException](../../mfc/reference/cresourceexception-class.md)|无法创建Windows的资源未找到或|  
|[COleException](../../mfc/reference/coleexception-class.md)|OLE异常|  
|[CDBException](../../mfc/reference/cdbexception-class.md)|数据库异常\(即提供对MFC数据库选件类的异常条件基于了开放式数据库连接\)|  
|[COleDispatchException](../../mfc/reference/coledispatchexception-class.md)|计划\(OLE自动化\)异常|  
|[CUserException](../../mfc/reference/cuserexception-class.md)|一个异常找不到资源|  
|[CDaoException](../../mfc/reference/cdaoexception-class.md)|数据访问对象异常\(即提供对DAO选件类\)的异常条件|  
|[CInternetException](../../mfc/reference/cinternetexception-class.md)|Internet异常\(即为对于Internet选件类\)的异常条件。|  
  
 这些异常主要用于 [引发](../Topic/THROW%20\(MFC\).md)、 [THROW\_LAST](../Topic/THROW_LAST.md)、 [尝试](../Topic/TRY.md)、 ["CATCH"](../Topic/CATCH.md)，[AND\_CATCH](../Topic/AND_CATCH.md)和 [END\_CATCH](../Topic/END_CATCH.md) 宏。  有关异常的更多信息，请参见 [异常处理](../../mfc/reference/exception-processing.md)或看得到文章 [异常处理\(MFC\)](../../mfc/exception-handling-in-mfc.md)。  
  
 要捕捉特定异常，请使用适当的派生类。  捕获异常的所有类型，请使用 `CException`，然后使用 [CObject::IsKindOf](../Topic/CObject::IsKindOf.md) 在 `CException`派生类中区分。  请注意 `CObject::IsKindOf` 仅工作选件类的声明与 [IMPLEMENT\_DYNAMIC](../Topic/IMPLEMENT_DYNAMIC.md) 宏，为了利用动态类型检查。  任何 `CException`\-要创建的派生类应使用 `IMPLEMENT_DYNAMIC` 宏，也是。  
  
 您可以将有关异常的详细信息向用户报告通过调用 [GetErrorMessage](../Topic/CFileException::GetErrorMessage.md) 或 [ReportError](../Topic/CException::ReportError.md)，与任何`CException`的派生类的两个成员函数。  
  
 如果异常是由一个宏来捕获，`CException` 会自动删除对象;不要将其删除您。  使用 **"Catch"** 关键字，如果捕获到异常，它不会自动被删除。  在参见中的文章 [异常处理\(MFC\)](../../mfc/exception-handling-in-mfc.md) 有关删除exeption对象的更多信息。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CException`  
  
## 要求  
 **Header:** afx.h  
  
## 请参阅  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [异常处理](../../mfc/reference/exception-processing.md)   
 [如何:我创建"我的自定义异常选件类?](http://go.microsoft.com/fwlink/?LinkId=128045)