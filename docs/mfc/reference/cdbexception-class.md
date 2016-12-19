---
title: "CDBException Class | Microsoft Docs"
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
  - "CDBException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDBException class"
  - "database exceptions [C++]"
  - "错误 [C++], 数据库"
  - "exceptions [C++], 数据库"
  - "ODBC 类 [C++], 异常"
ms.assetid: eb9e1119-89f5-49a7-b9d4-b91cee1ccc82
caps.latest.revision: 23
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDBException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示显示从数据库选件类的异常条件。  
  
## 语法  
  
```  
  
class CDBException : public CException  
  
```  
  
## 成员  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CDBException::m\_nRetCode](../Topic/CDBException::m_nRetCode.md)|包含开放式数据库连接\(odbc\)返回代码中，类型 **RETCODE**。|  
|[CDBException::m\_strError](../Topic/CDBException::m_strError.md)|包含描述错误的字母数字术语的字符串。|  
|[CDBException::m\_strStateNativeOrigin](../Topic/CDBException::m_strStateNativeOrigin.md)|包含描述错误的字符串基于ODBC返回的错误代码。|  
  
## 备注  
 选件类包含可用于确定异常的原因或显示描述异常的文本消息的两个公共数据成员。  `CDBException` 对象由数据库选件类的成员函数构造并引发。  
  
> [!NOTE]
>  此选件类是一个MFC的开放式数据库连接\(odbc\)选件类。  如果使用较新的数据访问弃用\(DAO\)选件类，使用 [CDaoException](../../mfc/reference/cdaoexception-class.md)。  所有DAO类名具有“CDao”为前缀。  有关更多信息，请参见文章 [概述:数据库编程](../../data/data-access-programming-mfc-atl.md)。  
  
 异常是异常执行涉及程序控件外的用例条件，例如数据源或网络I\/O错误。  在执行程序的路由可能希望看到的错误通常不被视为异常。  
  
 在 **"CATCH"** 表达式的范围内，您可以访问这些对象。  还可以引发从代码中 `CDBException` 对象与 `AfxThrowDBException` 全局函数。  
  
 有关通常，异常处理的更多信息或者有关 `CDBException` 对象，请参见位于 [异常处理\(MFC\)](../../mfc/exception-handling-in-mfc.md) 和 [异常:数据库异常](../../mfc/exceptions-database-exceptions.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CDBException`  
  
## 要求  
 **Header:** afxdb.h  
  
## 请参阅  
 [CException Class](../../mfc/reference/cexception-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDatabase Class](../../mfc/reference/cdatabase-class.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)   
 [CFieldExchange Class](../../mfc/reference/cfieldexchange-class.md)   
 [AfxThrowDBException](../Topic/AfxThrowDBException.md)   
 [CRecordset::Update](../Topic/CRecordset::Update.md)   
 [CRecordset::Delete](../Topic/CRecordset::Delete.md)   
 [CException Class](../../mfc/reference/cexception-class.md)