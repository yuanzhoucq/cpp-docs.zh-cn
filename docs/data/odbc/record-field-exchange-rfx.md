---
title: "记录字段交换 (RFX) | Microsoft Docs"
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
  - "数据 [MFC]"
  - "数据 [MFC], 在源和记录集之间移动"
  - "数据库类 [C++], RFX"
  - "ODBC [C++], RFX"
  - "RFX (ODBC) [C++]"
ms.assetid: f5ddfbf0-2901-48d7-9848-4fb84de3c7ee
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 记录字段交换 (RFX)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

MFC ODBC 数据库类使数据源与 [Recordset](../../data/odbc/recordset-odbc.md) 对象之间的数据移动自动进行。  如果从 [CRecordset](../../mfc/reference/crecordset-class.md) 派生一个类并且不使用批量取行，则数据传输遵从记录字段交换 \(record field exchange, RFX\) 机制。  
  
> [!NOTE]
>  如果已在派生的 `CRecordset` 类中实现了批量取行，则框架使用批量记录字段交换 \(Bulk RFX\) 机制来传输数据。  有关更多信息，请参见[记录集：批量获取记录 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 RFX 类似于对话框数据交换 \(dialog data exchange, DDX\)。  在数据源和记录集的字段数据成员之间移动数据要求多次调用记录集的 [DoFieldExchange](../Topic/CRecordset::DoFieldExchange.md) 函数，同时要求框架和 [ODBC](../../data/odbc/odbc-basics.md) 之间有大量的交互。  RFX 机制是类型安全的，并且免去了调用 ODBC 函数（如 **::SQLBindCol**）的工作。  有关 DDX 的更多信息，请参见 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
 RFX 对您来说几乎是透明的。  如果您使用“MFC 应用程序向导”或“添加类”（详见 [添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)中的介绍）来声明记录集类，RFX 会自动内置到这些类中。  您的记录集类必须从框架所提供的 `CRecordset` 基类中派生。  “MFC 应用程序向导”使您得以创建初始记录集类。  “添加类”使您可以在需要时添加其他记录集类。  有关更多信息和示例，请参见 [添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)。  
  
 当需要执行下列三种操作时，必须手动添加少量的 RFX 代码：  
  
-   使用参数化查询。  有关更多信息，请参见[记录集：参数化记录集 \(ODBC\)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。  
  
-   执行联接（将一个记录集用于两个或更多表中的列）。  有关更多信息，请参见[记录集：执行联接 \(ODBC\)](../../data/odbc/recordset-performing-a-join-odbc.md)。  
  
-   动态绑定数据列。  这不如参数化通用。  有关更多信息，请参见[记录集：动态绑定数据列 \(ODBC\)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。  
  
 如果要进一步了解 RFX，请参见 [记录字段交换：RFX 的工作机制](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 以下主题说明有关使用记录集对象的详细信息：  
  
-   [记录字段交换：使用 RFX](../../data/odbc/record-field-exchange-using-rfx.md)  
  
-   [记录字段交换：使用 RFX 函数](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)  
  
-   [记录字段交换：RFX 的工作机制](../../data/odbc/record-field-exchange-how-rfx-works.md)  
  
## 请参阅  
 [开放式数据库连接 \(ODBC\)](../../data/odbc/open-database-connectivity-odbc.md)   
 [记录集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [MFC ODBC 使用](../../mfc/reference/adding-an-mfc-odbc-consumer.md)   
 [MFC 应用程序向导的数据库支持](../../mfc/reference/database-support-mfc-application-wizard.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)