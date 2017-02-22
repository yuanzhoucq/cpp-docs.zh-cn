---
title: "记录字段交换函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DAO（数据访问对象）, 记录字段交换 (DFX)"
  - "ODBC, 批量 RFX 数据交换函数"
  - "RFX（记录字段交换）, ODBC 类"
  - "DFX（DAO 记录字段交换）, 数据交换函数"
  - "DFX 函数"
  - "批量 RFX 函数"
  - "DAO 记录字段交换 (DFX)"
  - "RFX（记录字段交换）, DAO 类"
  - "ODBC, RFX"
  - "RFX（记录字段交换）, 数据交换函数"
  - "记录字段交换 (RFX)"
ms.assetid: 6e4c5c1c-acb7-4c18-bf51-bf7959a696cd
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# 记录字段交换函数
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题列出了记录字段交换（[RFX](#_mfc_rfx_functions_.28.odbc.29)、[Bulk RFX](#_mfc_bulk_rfx_functions_.28.odbc.29) 和 [DFX](#_mfc_dfx_functions_.28.dao.29)）函数，这些函数用于在记录集对象与其数据源之间自动传输数据以及对数据执行其他操作。  
  
 如果正在使用基于 ODBC 的类，并且已实现批量行提取，则必须为与数据源列对应的每个数据成员调用批量 RFX 函数，以便手动重写 `CRecordset` 的 `DoBulkFieldExchange` 成员函数。  
  
 如果尚未在基于 ODBC 的类中实现批量行提取，或者如果正在使用基于 DAO 的类，ClassWizard 将通过为记录集中的每个字段数据成员调用 RFX 函数（对于 ODBC 类）或 DFX 函数（对于 DAO 类），来重写 `CRecordset` 或 `CDaoRecordset` 的 `DoFieldExchange` 成员函数。  
  
 记录字段交换函数在框架每次调用 `DoFieldExchange` 或 `DoBulkFieldExchange` 时传输数据。 每个函数传输一种特定的数据类型。  
  
 有关如何使用这些函数的详细信息，请参阅[记录字段交换：RFX 的工作方式 \(ODBC\)](../../data/odbc/record-field-exchange-how-rfx-works.md) 一文。 有关批量行提取的详细信息，请参阅[记录集：批量提取记录 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) 一文。  
  
 对于动态绑定的数据列，你还可以自行调用 RFX 或 DFX 函数，如[记录集：动态绑定数据列 \(ODBC\)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md) 一文中所述。 此外，你还可以编写自己的自定义 RFX 或 DFX 例程，如技术说明 [43](../../mfc/tn043-rfx-routines.md)（针对 ODBC）和技术说明 [53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md)（针对 DAO）中所述。  
  
 有关出现在 `DoFieldExchange` 和 `DoBulkFieldExchange` 函数中的 RFX 和批量 RFX 函数的示例，请参阅 [RFX\_Text](../Topic/RFX_Text.md) 和 [RFX\_Text\_Bulk](../Topic/RFX_Text_Bulk.md)。 DFX 函数与 RFX 函数非常类似。  
  
### RFX 函数 \(ODBC\)  
  
|||  
|-|-|  
|[RFX\_Binary](../Topic/RFX_Binary.md)|传输 [CByteArray](../../mfc/reference/cbytearray-class.md) 类型的字节数组。|  
|[RFX\_Bool](../Topic/RFX_Bool.md)|传输布尔数据。|  
|[RFX\_Byte](../Topic/RFX_Byte.md)|传输单字节数据。|  
|[RFX\_Date](../Topic/RFX_Date.md)|使用 [CTime](../../atl-mfc-shared/reference/ctime-class.md) 或 **TIMESTAMP\_STRUCT** 传输时间和日期数据。|  
|[RFX\_Double](../Topic/RFX_Double.md)|传输双精度浮点数据。|  
|[RFX\_Int](../Topic/RFX_Int.md)|传输整型数据。|  
|[RFX\_Long](../Topic/RFX_Long.md)|传输长整型数据。|  
|[RFX\_LongBinary](../Topic/RFX_LongBinary.md)|使用 [CLongBinary](../../mfc/reference/clongbinary-class.md) 类的对象传输二进制大型对象 \(BLOB\) 数据。|  
|[RFX\_Single](../Topic/RFX_Single.md)|传输浮点数据。|  
|[RFX\_Text](../Topic/RFX_Text.md)|传输字符串数据。|  
  
### 批量 RFX 函数 \(ODBC\)  
  
|||  
|-|-|  
|[RFX\_Binary\_Bulk](../Topic/RFX_Binary_Bulk.md)|传输字节数据数组。|  
|[RFX\_Bool\_Bulk](../Topic/RFX_Bool_Bulk.md)|传输布尔数据数组。|  
|[RFX\_Byte\_Bulk](../Topic/RFX_Byte_Bulk.md)|传输单字节数组。|  
|[RFX\_Date\_Bulk](../Topic/RFX_Date_Bulk.md)|传输 **TIMESTAMP\_STRUCT** 类型的数据数组。|  
|[RFX\_Double\_Bulk](../Topic/RFX_Double_Bulk.md)|传输双精度浮点数据数组。|  
|[RFX\_Int\_Bulk](../Topic/RFX_Int_Bulk.md)|传输整型数据数组。|  
|[RFX\_Long\_Bulk](../Topic/RFX_Long_Bulk.md)|传输长整型数据数组。|  
|[RFX\_Single\_Bulk](../Topic/RFX_Single_Bulk.md)|传输浮点数据数组。|  
|[RFX\_Text\_Bulk](../Topic/RFX_Text_Bulk.md)|传输 **LPSTR** 类型的数据数组。|  
  
### DFX 函数 \(DAO\)  
  
|||  
|-|-|  
|[DFX\_Binary](../Topic/DFX_Binary.md)|传输 [CByteArray](../../mfc/reference/cbytearray-class.md) 类型的字节数组。|  
|[DFX\_Bool](../Topic/DFX_Bool.md)|传输布尔数据。|  
|[DFX\_Byte](../Topic/DFX_Byte.md)|传输单字节数据。|  
|[DFX\_Currency](../Topic/DFX_Currency.md)|传输 [COleCurrency](../../mfc/reference/colecurrency-class.md) 类型的货币数据。|  
|[DFX\_DateTime](../Topic/DFX_DateTime.md)|传输 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) 类型的时间和日期数据。|  
|[DFX\_Double](../Topic/DFX_Double.md)|传输双精度浮点数据。|  
|[DFX\_Long](../Topic/DFX_Long.md)|传输长整型数据。|  
|[DFX\_LongBinary](../Topic/DFX_LongBinary.md)|使用 `CLongBinary` 类的对象传输二进制大型对象 \(BLOB\) 数据。 对于 DAO，建议改用 [DFX\_Binary](../Topic/DFX_Binary.md)。|  
|[DFX\_Short](../Topic/DFX_Short.md)|传输短整型数据。|  
|[DFX\_Single](../Topic/DFX_Single.md)|传输浮点数据。|  
|[DFX\_Text](../Topic/DFX_Text.md)|传输字符串数据。|  
  
## 请参阅  
 [MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)   
 [CRecordset::DoFieldExchange](../Topic/CRecordset::DoFieldExchange.md)   
 [CRecordset::DoBulkFieldExchange](../Topic/CRecordset::DoBulkFieldExchange.md)   
 [CDaoRecordset::DoFieldExchange](../Topic/CDaoRecordset::DoFieldExchange.md)