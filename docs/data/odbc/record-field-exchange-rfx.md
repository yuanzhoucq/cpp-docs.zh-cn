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
ms.openlocfilehash: 8630fab11728b0c0cd16eee5035df028a8382706
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59032214"
---
# <a name="record-field-exchange-rfx"></a>记录字段交换 (RFX)

MFC ODBC 数据库类自动执行数据源之间移动数据和一个[记录集](../../data/odbc/recordset-odbc.md)对象。 当您从派生类[CRecordset](../../mfc/reference/crecordset-class.md)并且未使用批量行提取，数据传输的记录字段交换 (RFX) 机制。

> [!NOTE]
>  如果已实现批量行提取在派生`CRecordset`类，框架将使用批量记录字段交换 (Bulk RFX) 机制将数据传输。 有关详细信息，请参阅[记录集：(ODBC) 批量提取记录](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

RFX 是类似于对话框数据交换 (DDX)。 数据源和记录集的字段数据成员之间移动数据时，需要对记录集的多个调用[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) framework 之间的函数和很大程度的交互和[ODBC](../../data/odbc/odbc-basics.md). RFX 机制是类型安全的将保存您的工作是调用 ODBC 函数如`::SQLBindCol`。 有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

RFX 主要是透明的。 如果您声明您使用 MFC 应用程序向导的记录集类或**添加类**(如中所述[添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md))，RFX 自动内置到它们。 记录集类必须派生自的基类`CRecordset`框架所提供的。 MFC 应用程序向导允许您创建一个初始的记录集类。 **将类添加**，可以根据需要添加其他记录集类。 有关详细信息和示例，请参阅[添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)。

根据需要，则必须手动添加在三种情况下，少量的 RFX 代码：

- 使用参数化的查询。 有关详细信息，请参阅[记录集：参数化记录集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。

- 执行联接 （使用一个记录集适用于两个或多个表中的列）。 有关详细信息，请参阅[记录集：执行联接 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)。

- 动态绑定数据列。 这是不太常用于参数化。 有关详细信息，请参阅[记录集：动态绑定数据列 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。

如果你需要一个更高级的 RFX 了解，请参阅[记录字段交换：RFX 的工作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

以下主题介绍使用记录集对象的详细信息：

- [记录字段交换：使用 RFX](../../data/odbc/record-field-exchange-using-rfx.md)

- [记录字段交换：使用 RFX 函数](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)

- [记录字段交换：RFX 的工作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)

## <a name="see-also"></a>请参阅

[开放式数据库连接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[MFC ODBC 使用](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[MFC 应用程序向导的数据库支持](../../mfc/reference/database-support-mfc-application-wizard.md)<br/>
[CRecordset 类](../../mfc/reference/crecordset-class.md)