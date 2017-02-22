---
title: "CFieldExchange Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CFieldExchange"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFieldExchange class"
  - "数据类型 [C++], 自定义"
  - "enum FieldType"
  - "enum FieldType, CFieldExchange"
  - "FieldType enumeration"
  - "RFX (record field exchange) [C++]"
  - "RFX (record field exchange) [C++], classes for"
ms.assetid: 24c5c0b3-06a6-430e-9b6f-005a2c65e29f
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CFieldExchange Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

支持记录字段交换\(rfx\)，并且该数据库使用的批量记录字段交换\(bulk RFX\)实例类别。  
  
## 语法  
  
```  
  
class CFieldExchange  
  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CFieldExchange::IsFieldType](../Topic/CFieldExchange::IsFieldType.md)|如果当前操作的字段的类型为适当的更新，返回非零。|  
|[CFieldExchange::SetFieldType](../Topic/CFieldExchange::SetFieldType.md)|指定记录集以下所有—列或参数—表示的数据成员的类型调用RFX函数，直到下调用 `SetFieldType`。|  
  
## 备注  
 `CFieldExchange` 没有基类。  
  
 请使用此选件类，如果您为自定义数据类型编写数据交换的实例，在实现批量取行时;否则，可能不会直接使用此选件类。  RFX和批量RFX交换数据的记录集对象的字段数据成员和当前记录之间的相应字段。数据源。  
  
> [!NOTE]
>  如果您使用的是数据访问使用否决\(DAO\)选件类而不是开放式数据库连接\(odbc\)选件类，使用选件类 [CDaoFieldExchange](../../mfc/reference/cdaofieldexchange-class.md)。  有关更多信息，请参见文章 [概述: 数据库编程](../../data/data-access-programming-mfc-atl.md)。  
  
 `CFieldExchange` 对象用于记录字段交换或批量记录字段交换提供所需的上下文信息发生。  `CFieldExchange` 对象支持许多操作，包括内置参数和字段数据成员并在当前记录的字段的各个标志。  RFX和批量RFX操作在 `enum`定义的类型的记录集类的数据成员执行**FieldType** 在 `CFieldExchange`。  可能的 **FieldType** 值为:  
  
-   字段数据成员的**CFieldExchange::outputColumn**。  
  
-   **CFieldExchange::inputParam** 或 **CFieldExchange::param** 输入参数数据成员。  
  
-   输出参数数据成员的**CFieldExchange::outputParam**。  
  
-   输入\/输出参数数据成员的**CFieldExchange::inoutParam**。  
  
 大多数选件类的成员函数和数据成员了编写自定义RFX实例提供。  您经常使用 `SetFieldType`。  有关更多信息，请参见位于 [记录字段交换\(rfx\)](../../data/odbc/record-field-exchange-rfx.md) 和 [记录集\(odbc\)](../../data/odbc/recordset-odbc.md)。  有关批量取行的信息，请参见文章 [记录集:获取记录\(odbc\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  有关RFX和"批量RFX全局函数的详细信息，请参见本的MFC宏和Globals部分的 [记录字段交换函数](../../mfc/reference/record-field-exchange-functions.md) 引用。  
  
## 继承层次结构  
 `CFieldExchange`  
  
## 要求  
 **Header:** afxdb.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)