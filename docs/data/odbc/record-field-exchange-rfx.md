---
title: 记录字段交换 (RFX)
ms.date: 11/04/2016
helpviewer_keywords:
- RFX (ODBC) [C++]
- data [MFC], moving between sources and recordsets
- database classes [C++], RFX
- data [MFC]
- ODBC [C++], RFX
ms.assetid: f5ddfbf0-2901-48d7-9848-4fb84de3c7ee
ms.openlocfilehash: e1ba9f29ebf2cb3b1f94620e815882c850bbc7cc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213052"
---
# <a name="record-field-exchange-rfx"></a>记录字段交换 (RFX)

MFC ODBC 数据库类自动在数据源和[记录集](../../data/odbc/recordset-odbc.md)对象之间移动数据。 当从[CRecordset](../../mfc/reference/crecordset-class.md)派生类而不使用批量提取行时，数据将由记录字段交换（RFX）机制传输。

> [!NOTE]
>  如果已实现派生 `CRecordset` 类中的批量行提取，则该框架将使用批量记录字段交换（Bulk RFX）机制来传输数据。 有关详细信息，请参阅[记录集：批量获取记录（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

RFX 类似于对话框数据交换（DDX）。 在数据源与记录集的字段数据成员之间移动数据时，需要多次调用记录集的[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)函数，并在框架和[ODBC](../../data/odbc/odbc-basics.md)之间进行很大的交互。 RFX 机制为类型安全，并为您节省了调用 ODBC 函数（如 `::SQLBindCol`）的工作。 有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

RFX 对您而言是透明的。 如果使用 "MFC 应用程序向导" 或 "**添加类**" （如[添加 Mfc ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)中所述）声明记录集类，则会自动将 RFX 内置于其中。 记录集类必须从框架提供的基类 `CRecordset` 派生。 MFC 应用程序向导允许您创建初始记录集类。 **添加类**使你可以在需要时添加其他记录集类。 有关详细信息和示例，请参阅[添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)。

在以下三种情况下，你必须手动添加少量 RFX 代码：

- 使用参数化查询。 有关详细信息，请参阅[记录集：参数化记录集（ODBC）](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。

- 执行联接（对于两个或多个表中的列，使用一个记录集）。 有关详细信息，请参阅[记录集：执行联接（ODBC）](../../data/odbc/recordset-performing-a-join-odbc.md)。

- 动态绑定数据列。 这不如参数化常见。 有关详细信息，请参阅[记录集：动态绑定数据列（ODBC）](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。

如果需要更高级的 RFX 理解，请参阅[记录字段交换： RFX 的工作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

以下主题介绍使用 recordset 对象的详细信息：

- [记录字段交换：使用 RFX](../../data/odbc/record-field-exchange-using-rfx.md)

- [记录字段交换：使用 RFX 函数](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)

- [记录字段交换：RFX 的工作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)

## <a name="see-also"></a>另请参阅

[开放式数据库连接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[MFC ODBC 使用](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[MFC 应用程序向导的数据库支持](../../mfc/reference/database-support-mfc-application-wizard.md)<br/>
[CRecordset 类](../../mfc/reference/crecordset-class.md)
