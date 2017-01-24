---
title: "CDaoException Class | Microsoft Docs"
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
  - "CDaoException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoException class"
  - "集合, DAO 错误"
  - "DAO（数据访问对象）, 异常"
  - "错误 [C++], DAO"
  - "Errors collection, DAO"
  - "异常, in MFC DAO classes"
ms.assetid: b2b01fa9-7ce2-42a1-842e-40f13dc50da4
caps.latest.revision: 24
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDaoException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示显示从MFC数据库选件类的异常条件根据数据访问对象\(DAO）。  
  
## 语法  
  
```  
class CDaoException : public CException  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CDaoException::CDaoException](../Topic/CDaoException::CDaoException.md)|构造 `CDaoException` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CDaoException::GetErrorCount](../Topic/CDaoException::GetErrorCount.md)|返回错误数。数据库引擎的错误集合。|  
|[CDaoException::GetErrorInfo](../Topic/CDaoException::GetErrorInfo.md)|返回有关特定错误对象的错误信息在错误集合。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CDaoException::m\_nAfxDaoError](../Topic/CDaoException::m_nAfxDaoError.md)|在MFC DAO选件类包含所有错误的一个扩展的错误代码。|  
|[CDaoException::m\_pErrorInfo](../Topic/CDaoException::m_pErrorInfo.md)|为\)包含有关DAO错误对象的信息的 [CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md) 对象的指针。|  
|[CDaoException::m\_scode](../Topic/CDaoException::m_scode.md)|[SCODE](../Topic/CDaoException::m_scode.md) 值与错误。|  
  
## 备注  
 选件类包含可用于确定异常原因的公共数据成员。  `CDaoException` 对象由DAO数据库选件类的成员函数构造并引发。  
  
> [!NOTE]
>  DAO数据库选件类根据了开放式数据库连接的MFC数据库选件类都一目了然\(odbc）。  所有DAO数据库类名具有“CDao”前缀。  您仍然可以访问使用DAO选件类的ODBC数据源。  通常，基于DAO的MFC选件类与基于ODBC的MFC选件类能够;基于DAO的选件类可以访问数据访问，包括通过ODBC驱动程序，将它们的数据库引擎。  基于DAO的选件类通过选件类还支持数据定义语言\(DDL\)操作，例如添加表，而不必直接调用DAO。  有关ODBC选件类引发的异常的信息，请参见 [CDBException](../../mfc/reference/cdbexception-class.md)。  
  
 在 ["CATCH"](../Topic/CATCH.md) 表达式的范围内，您可以访问异常对象。  还可以引发从代码中 `CDaoException` 对象与 [AfxThrowDaoException](../Topic/AfxThrowDaoException.md) 全局函数。  
  
 在MFC中，所有DAO错误表示为异常，类型 `CDaoException`。  在捕捉此类型的异常时，可以使用 `CDaoException` 成员函数从数据库引擎的错误集合中存储的所有DAO错误对象检索信息。  在每个错误，一个或多个错误对象在错误集合中。  （集合仅通常包含错误对象;如果使用ODBC数据源，则更为可能发生多个错误对象。）在另一个DAO操作生成错误时，更正错误，集合，并且新的错误对象在错误集合中。  不生成错误的DAO操作没有为false集合的效果。  
  
 有关DAO错误代码，请参见文件DAOERR.H。  有关相关信息，请参见主题“Trappable数据访问错误” DAO帮助。  
  
 有关通常，异常处理的更多信息或者有关 `CDaoException` 对象，请参见位于 [异常处理\(MFC\)](../../mfc/exception-handling-in-mfc.md) 和 [异常:数据库异常](../../mfc/exceptions-database-exceptions.md)。  第二个文章包含声明异常处理DAO的代码示例。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CDaoException`  
  
## 要求  
 **Header:** afxdao.h  
  
## 请参阅  
 [CException Class](../../mfc/reference/cexception-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CException Class](../../mfc/reference/cexception-class.md)