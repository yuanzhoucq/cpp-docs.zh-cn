---
title: "记录字段交换：使用 RFX | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RFX (ODBC), 实现"
ms.assetid: ada8f043-37e6-4d41-9db3-92c997a61957
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 记录字段交换：使用 RFX
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题说明为使用 RFX 您和框架分别要执行哪些操作。  
  
> [!NOTE]
>  本主题适用于从 [CRecordset](../../mfc/reference/crecordset-class.md) 派生的类，这些类中尚未实现批量取行。  如果使用的是批量取行，则实现批量记录字段交换 \(Bulk RFX\)。  Bulk RFX 与 RFX 类似。  若要了解其中的差别，请参见[记录集：批量获取记录 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 以下主题包含相关信息：  
  
-   [记录字段交换：处理向导代码](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md)介绍 RFX 的主要组件，并解释“MFC 应用程序向导”和“添加类”（详见[添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)中的介绍）为支持 RFX 而编写的代码，同时还介绍了如何修改这些向导代码。  
  
-   [记录字段交换：使用 RFX 函数](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)解释如何在 `DoFieldExchange` 重写中编写对 RFX 函数的调用。  
  
 下表分别列出您的职责和框架为您执行的操作。  
  
### 使用 RFX：您和框架  
  
|你|框架|  
|-------|--------|  
|用向导声明记录集类。  指定字段数据成员的名称和数据类型。|向导派生一个 `CRecordset` 类，并为您写一个 [DoFieldExchange](../Topic/CRecordset::DoFieldExchange.md) 重写，其中包括每个字段数据成员的 RFX 函数调用。|  
|（可选）将所需要的任何参数数据成员手动添加到类中。  手动将 RFX 函数调用添加到每个参数数据成员的 `DoFieldExchange`，为参数组添加一个 [CFieldExchange::SetFieldType](../Topic/CFieldExchange::SetFieldType.md) 调用，并指定 [m\_nParams](../Topic/CRecordset::m_nParams.md) 中的参数总数。  请参见[记录集：参数化记录集 \(ODBC\)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。||  
|（可选）手动将其他列绑定到字段数据成员。  手动增加 [m\_nFields](../Topic/CRecordset::m_nFields.md)。  请参见[记录集：动态绑定数据列 \(ODBC\)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。||  
|构造记录集类的对象。  在使用该对象前，设置它的参数数据成员的值（如果有的话）。|为提高效率，框架使用 ODBC 预绑定参数。  当您传递参数值时，框架将参数值传递到数据源。  除非排序和\/或筛选字符串已更改，否则只发送用于再次查询的参数值。|  
|使用 [CRecordset::Open](../Topic/CRecordset::Open.md) 打开记录集对象。|执行记录集的查询，将列绑定到记录集的字段数据成员，并调用 `DoFieldExchange` 在第一个选定记录和记录集的字段数据成员之间交换数据。|  
|使用 [CRecordset::Move](../Topic/CRecordset::Move.md) 或者菜单或工具栏命令在记录集中滚动。|调用 `DoFieldExchange` 将数据从新的当前记录传输到字段数据成员。|  
|添加、更新和删除记录。|调用 `DoFieldExchange` 将数据传输到数据源。|  
  
## 请参阅  
 [记录字段交换 \(RFX\)](../../data/odbc/record-field-exchange-rfx.md)   
 [记录字段交换：RFX 的工作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)   
 [记录集：获取 SUM 及其他聚合结果 \(ODBC\)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)   
 [CFieldExchange Class](../../mfc/reference/cfieldexchange-class.md)   
 [宏、全局函数和全局变量](../Topic/Macros,%20Global%20Functions,%20and%20Global%20Variables.md)