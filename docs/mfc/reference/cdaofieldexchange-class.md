---
title: "CDaoFieldExchange Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDaoFieldExchange"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoFieldExchange class"
  - "DAO（数据访问对象）, record field exchange (DFX)"
  - "DAO 记录字段交换 (DFX)"
  - "DAO 记录字段交换 (DFX), DAO Record Field Exchange"
  - "exchanging data between databases and recordsets"
  - "field exchange"
  - "field exchange, record for DAO classes"
  - "记录字段交换 (RFX)"
  - "记录字段交换 (RFX), DAO 类"
ms.assetid: 350a663e-92ff-44ab-ad53-d94efa2e5823
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CDaoFieldExchange Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

支持DAO数据库选件类使用的DAO记录字段交换\(DFX\)实例。  
  
## 语法  
  
```  
class CDaoFieldExchange  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CDaoFieldExchange::IsValidOperation](../Topic/CDaoFieldExchange::IsValidOperation.md)|如果当前操作的字段的类型为适当的更新，返回非零。|  
|[CDaoFieldExchange::SetFieldType](../Topic/CDaoFieldExchange::SetFieldType.md)|指定记录集所有列或参数—表示的数据成员的类型的后续调用DFX功能，直到下调用 `SetFieldType`。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CDaoFieldExchange::m\_nOperation](../Topic/CDaoFieldExchange::m_nOperation.md)|当前正在执行的DFX操作调用记录集的 `DoFieldExchange` 成员函数。|  
|[CDaoFieldExchange::m\_prs](../Topic/CDaoFieldExchange::m_prs.md)|对DFX操作的记录集的指针。|  
  
## 备注  
 `CDaoFieldExchange` 没有基类。  
  
 如果您为自定义数据类型，编写数据交换的实例中使用此选件类;否则，可能不会直接使用此选件类。  DFX在您的 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 对象的字段数据成员和当前记录之间的相应字段交换数据源中的。  DFX管理替换在两个方向，从数据源和给数据源。  有关编写自定义DFX实例的信息，请参见 [技术说明53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md)。  
  
> [!NOTE]
>  DAO数据库选件类根据了开放式数据库连接的MFC数据库选件类都一目了然\(odbc）。  所有DAO数据库类名具有“CDao”前缀。  您仍然可以访问使用DAO选件类的ODBC数据源。  通常，基于DAO的MFC选件类与基于ODBC的MFC选件类能够。  基于DAO的选件类可以访问数据访问，包括通过ODBC驱动程序，将它们的数据库引擎。  通过选件类还支持数据定义语言\(DDL\)操作，例如添加表而不必调用DAO。  
  
> [!NOTE]
>  DAO记录字段交换\(DFX\)非常类似于记录字段交换\(rfx\)在基于ODBC的MFC数据库选件类\(`CDatabase`，`CRecordset`）。  如果您了解RFX，您会发现它易于使用DFX。  
  
 `CDaoFieldExchange` 对象对DAO记录字段交换提供所需的上下文信息发生。  `CDaoFieldExchange` 对象支持许多操作，包括内置参数和字段数据成员并在当前记录的字段的各个标志。  DFX操作在 `enum`定义的类型的记录集类的数据成员执行**FieldType** 在 `CDaoFieldExchange`。  可能的 **FieldType** 值为:  
  
-   字段数据成员的**CDaoFieldExchange::outputColumn**。  
  
-   参数数据成员的**CDaoFieldExchange::param**。  
  
 [IsValidOperation](../Topic/CDaoFieldExchange::IsValidOperation.md) 成员函数用于编写您的自定义DFX实例提供。  您的 [CDaoRecordset::DoFieldExchange](../Topic/CDaoRecordset::DoFieldExchange.md) 功能经常使用 [SetFieldType](../Topic/CDaoFieldExchange::SetFieldType.md)。  有关DFX全局函数的详细信息，请参见 [记录字段交换函数](../../mfc/reference/record-field-exchange-functions.md)。  有关您的数据类型编写自定义DFX实例的信息，请参见 [技术说明53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md)。  
  
## 继承层次结构  
 `CDaoFieldExchange`  
  
## 要求  
 **Header:** afxdao.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDaoRecordset Class](../../mfc/reference/cdaorecordset-class.md)