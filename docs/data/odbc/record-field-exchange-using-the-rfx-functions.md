---
title: "记录字段交换：使用 RFX 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "数据类型 [C++], ODBC 记录字段交换"
  - "DoFieldExchange 方法, 和 RFX 函数"
  - "函数调用, RFX 函数"
  - "ODBC [C++], 数据类型"
  - "ODBC [C++], RFX"
  - "RFX (ODBC) [C++], 数据类型"
  - "RFX (ODBC) [C++], 函数语法和参数"
ms.assetid: c594300b-5a29-4119-a68b-e7ca32def696
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 记录字段交换：使用 RFX 函数
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题说明如何使用组成 `DoFieldExchange` 重写体的 RFX 函数调用。  
  
> [!NOTE]
>  本主题适用于从 [CRecordset](../../mfc/reference/crecordset-class.md) 派生的类，这些类中尚未实现批量取行。  如果使用的是批量取行，则实现批量记录字段交换 \(Bulk RFX\)。  Bulk RFX 与 RFX 类似。  若要了解其中的差别，请参见[记录集：批量获取记录 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 RFX 全局函数在数据源上的列和记录集中的字段数据成员之间交换数据。  在记录集的 [DoFieldExchange](../Topic/CRecordset::DoFieldExchange.md) 成员函数中写 RFX 函数调用。  本主题简要描述这些函数并显示可对其使用 RFX 函数的数据类型。  [技术说明 43](../../mfc/tn043-rfx-routines.md) 描述如何为其他数据类型编写自己的 RFX 函数。  
  
##  <a name="_core_rfx_function_syntax"></a> RFX 函数语法  
 每个 RFX 函数采用三个参数（有些 RFX 函数采用第四个或第五个可选参数）：  
  
-   指向 [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) 对象的指针。  您只需顺着传递到 `DoFieldExchange` 的 `pFX` 指针进行传递。  
  
-   列在数据源上出现时的名称。  
  
-   记录集类中相应的字段数据成员或参数数据成员的名称。  
  
-   （可选）在一些函数中，所传输的字符串或数组的最大长度。  默认为 255 个字节，但您可能需要更改它。  最大大小基于 `CString` 对象的最大大小（**INT\_MAX** \(2,147,483,647\) 字节），但在达到该大小前可能会遇到驱动程序限制。  
  
-   （可选）在 `RFX_Text` 函数中，有时使用第五个参数来指定列的数据类型。  
  
 有关更多信息，请参见 Class Library Reference 中[宏和全局](../Topic/Macros,%20Global%20Functions,%20and%20Global%20Variables.md)下的 RFX 函数。  有关参数特殊用法的示例，请参见 [记录集：获取 SUM 及其他聚合结果 \(ODBC\)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)。  
  
##  <a name="_core_rfx_data_types"></a> RFX 数据类型  
 类库提供了用于在数据源和记录集之间传输多种不同数据类型的 RFX 函数。  下表按数据类型总结了 RFX 函数。  如果您必须自行编写 RFX 函数调用，则可以按数据类型从这些函数中进行选择。  
  
|功能|数据类型|  
|--------|----------|  
|`RFX_Bool`|**BOOL**|  
|`RFX_Byte`|**BYTE**|  
|`RFX_Binary`|`CByteArray`|  
|`RFX_Double`|**double**|  
|`RFX_Single`|**float**|  
|`RFX_Int`|`int`|  
|`RFX_Long`|**long**|  
|`RFX_LongBinary`|`CLongBinary`|  
|`RFX_Text`|`CString`|  
|`RFX_Date`|`CTime`|  
  
 有关更多信息，请参见 Class Library Reference 中[宏和全局](../Topic/Macros,%20Global%20Functions,%20and%20Global%20Variables.md)下的 RFX 函数文档。  有关 C\+\+ 数据类型如何映射到 SQL 数据类型的信息，请参见 [SQL：SQL 和 C\+\+ 数据类型 \(ODBC\)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md) 中的表“映射到 C\+\+ 数据类型的 ANSI SQL 数据类型”。  
  
## 请参阅  
 [记录字段交换 \(RFX\)](../../data/odbc/record-field-exchange-rfx.md)   
 [记录字段交换：RFX 的工作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)   
 [记录集：参数化记录集 \(ODBC\)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)   
 [记录集：动态绑定数据列 \(ODBC\)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)   
 [CFieldExchange Class](../../mfc/reference/cfieldexchange-class.md)