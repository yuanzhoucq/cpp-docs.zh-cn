---
title: "异常处理 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros.exceptions"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DAO（数据访问对象）, 异常"
  - "异常宏"
  - "异常, MFC 引发函数"
  - "异常, 处理"
  - "宏, 异常处理"
  - "MFC, 异常"
  - "OLE 异常, MFC 函数"
  - "终止函数, MFC"
ms.assetid: 26d4457c-8350-48f5-916e-78f919787c30
caps.latest.revision: 16
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 异常处理
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在程序执行时，称为“异常”大量异常状况和错误可以发生。  这些可包括内存不足、资源分配错误和查找文件失败。  
  
 Microsoft 基础类库使用严格在 C\+\+ 的 ANSI 标准委员会的建议版本之后建模的异常处理方案。  异常处理程序必须在调用可能遇到一种异常情况的函数之前设置。  如果函数遇到异常状况，会引发异常，而控件传递给异常处理程序。  
  
 Microsoft 基础类库中包含的一些类将建立异常处理程序。  其他一些全局函数帮助引发特定的异常并终止程序，如有必要。  这些宏和全局函数分为以下几个类别：  
  
-   [异常宏](#_mfc_exception_macros)，结构化异常处理程序。  
  
-   [异常抛出函数](#_mfc_exception.2d.throwing_functions)，生成特定类型的异常。  
  
-   [函数终止](#_mfc_termination_functions)，导致程序终止。  
  
 有关示例和更多详细信息，请参见 [异常](../../mfc/exception-handling-in-mfc.md)文章。  
  
### 异常宏  
  
|||  
|-|-|  
|[TRY](../Topic/TRY.md)|指定异常处理的代码块。|  
|[CATCH](../Topic/CATCH.md)|指定代码块捕捉来自上述 **TRY** 块的异常。|  
|[CATCH\_ALL](../Topic/CATCH_ALL.md)|指定代码块捕捉来自上述 **TRY** 块的所有异常。|  
|[AND\_CATCH](../Topic/AND_CATCH.md)|指定代码块捕捉来自上述 **TRY** 块的额外的异常类型。|  
|[AND\_CATCH\_ALL](../Topic/AND_CATCH_ALL.md)|指定代码块用于捕捉前面的 **TRY** 块引发的其他额外的异常类型。|  
|[END\_CATCH](../Topic/END_CATCH.md)|关闭一 **CATCH** 或 `AND_CATCH` 的代码块。|  
|[END\_CATCH\_ALL](../Topic/END_CATCH_ALL.md)|关闭最后`CATCH_ALL` 代码块。|  
|[THROW](../Topic/THROW%20\(MFC\).md)|引发特定的异常。|  
|[THROW\_LAST](../Topic/THROW_LAST.md)|抛出当前处理的异常给下一个外部处理程序。|  
  
### 异常抛出函数  
  
|||  
|-|-|  
|[AfxThrowArchiveException](../Topic/AfxThrowArchiveException.md)|抛出存档异常。|  
|[AfxThrowFileException](../Topic/AfxThrowFileException.md)|抛出文件异常。|  
|[AfxThrowMemoryException](../Topic/AfxThrowMemoryException.md)|抛出内存异常。|  
|[AfxThrowNotSupportedException](../Topic/AfxThrowNotSupportedException.md)|抛出不受支持异常|  
|[AfxThrowResourceException](../Topic/AfxThrowResourceException.md)|抛出窗口查找不到资源的异常。|  
|[AfxThrowUserException](../Topic/AfxThrowUserException.md)|在用户启动程序操作中抛出异常。|  
  
 MFC 专门为 OLE 异常提供两个异常抛出函数：  
  
### OLE 异常函数  
  
|||  
|-|-|  
|[AfxThrowOleDispatchException](../Topic/AfxThrowOleDispatchException.md)|在 OLE 自动化的函数内抛出异常。|  
|[AfxThrowOleException](../Topic/AfxThrowOleException.md)|抛出一个OLE异常。|  
  
 为了支持数据库异常，数据库类提供两个异常类、`CDBException` 和 `CDaoException`全局函数支持异常类型：  
  
### DAO 异常函数  
  
|||  
|-|-|  
|[AfxThrowDAOException](../Topic/AfxThrowDaoException.md)|从自己的代码中抛出[CDao异常](../../mfc/reference/cdaoexception-class.md)|  
|[AfxThrowDBException](../Topic/AfxThrowDBException.md)|从自己的代码中抛出[CDBE异常](../../mfc/reference/cdbexception-class.md)|  
  
 MFC 提供下列终止函数：  
  
### 终止函数  
  
|||  
|-|-|  
|[AfxAbort](../Topic/AfxAbort.md)|当发生错误时调用终止应用程序。|  
  
## 请参阅  
 [MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)   
 [CException Class](../../mfc/reference/cexception-class.md)