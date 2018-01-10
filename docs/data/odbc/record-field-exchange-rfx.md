---
title: "记录字段交换 (RFX) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- RFX (ODBC) [C++]
- data [MFC], moving between sources and recordsets
- database classes [C++], RFX
- data [MFC]
- ODBC [C++], RFX
ms.assetid: f5ddfbf0-2901-48d7-9848-4fb84de3c7ee
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 50fc0aea1ef50124cd98b0d0498b767d1f00e5c0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="record-field-exchange-rfx"></a>记录字段交换 (RFX)
MFC ODBC 数据库类自动执行之间的数据源的数据移动和[记录集](../../data/odbc/recordset-odbc.md)对象。 当你从派生类[CRecordset](../../mfc/reference/crecordset-class.md)并且未使用批量行提取，记录字段交换 (RFX) 机制传输数据。  
  
> [!NOTE]
>  如果已实现批量行提取中派生`CRecordset`类，框架将使用批量记录字段交换 (Bulk RFX) 机制将数据传输。 有关详细信息，请参阅[记录集： 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 RFX 是类似于对话框数据交换 (DDX)。 数据源和记录集的字段数据成员之间移动数据时，需要对记录集的多个调用[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) framework 之间的函数和很大程度交互和[ODBC](../../data/odbc/odbc-basics.md). RFX 机制是类型安全的将你保存的工作成果如调用 ODBC 函数**:: SQLBindCol**。 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
 RFX 主要是透明的。 如果在声明您使用 MFC 应用程序向导的记录集类或**添加类**(中所述[添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md))，RFX 自动内置到它们。 记录集类必须派生自的基类`CRecordset`框架所提供的。 MFC 应用程序向导允许您创建一个初始的记录集类。 **添加类**允许您根据你的需要添加其他记录集类。 有关详细信息和示例，请参阅[添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)。  
  
 如果您希望，您必须手动添加在三种情况下，少量的 RFX 代码：  
  
-   使用参数化的查询。 有关详细信息，请参阅[记录集： 参数化记录集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。  
  
-   执行联接 （两个或多个表中的列使用一个记录集）。 有关详细信息，请参阅[记录集： 执行联接 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)。  
  
-   动态绑定数据列。 这是不太常用于参数化。 有关详细信息，请参阅[记录集： 动态绑定数据列 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。  
  
 如果你需要的 RFX 更深入的了解，请参阅[记录字段交换： RFX 的工作机制](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 以下主题说明了使用记录集对象的详细信息：  
  
-   [记录字段交换：使用 RFX](../../data/odbc/record-field-exchange-using-rfx.md)  
  
-   [记录字段交换：使用 RFX 函数](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)  
  
-   [记录字段交换：RFX 的工作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)  
  
## <a name="see-also"></a>请参阅  
 [开放式数据库连接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)   
 [记录集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [MFC ODBC 使用](../../mfc/reference/adding-an-mfc-odbc-consumer.md)   
 [数据库支持，MFC 应用程序向导](../../mfc/reference/database-support-mfc-application-wizard.md)   
 [CRecordset 类](../../mfc/reference/crecordset-class.md)