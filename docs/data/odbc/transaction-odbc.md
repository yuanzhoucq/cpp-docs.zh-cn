---
title: 事务 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets [C++], updating
- transactions [C++], MFC ODBC classes
- ODBC [C++], transactions
- recordsets [C++], updating
- databases [C++], transactions
- recordsets [C++], transactions
- ODBC recordsets [C++], transactions
ms.assetid: a2ec0995-2029-45f2-8092-6efd6f2a77f4
ms.openlocfilehash: 56629f8c5ff74aff4e0df589cda1e7b988fb5fd3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376417"
---
# <a name="transaction-odbc"></a>事务 (ODBC)

本主题适用于 MFC ODBC 类。

事务是一种对[数据源](../../data/odbc/data-source-odbc.md)的一系列更新进行分组或批处理的方法，以便在回滚事务时一次提交所有更新，或者不提交任何更新。 如果不使用事务，则会自动提交对数据源的更改，而不是按需提交。

> [!NOTE]
> 并非所有 ODBC 数据库驱动程序都支持事务。 调用`CanTransact`[CDatabase](../../mfc/reference/cdatabase-class.md)或[CRecordset](../../mfc/reference/crecordset-class.md)对象的成员函数，以确定驱动程序是否支持给定数据库的事务。 请注意，`CanTransact`不会告诉您数据源是否提供完整的事务支持。 您还必须`CDatabase::GetCursorCommitBehavior`调用 和`CDatabase::GetCursorRollbackBehavior``CommitTrans`后`Rollback`，并检查事务对打开`CRecordset`对象的影响。

调用`CRecordset`对象的`AddNew``Edit`和 成员函数在调用`Update`时会立即影响数据源。 `Delete`呼叫也会立即生效。 相反`AddNew`，可以使用由对 、`Edit`和`Update``Delete`的多个调用组成的事务，这些调用在显式调用`CommitTrans`之前执行但不提交。 通过建立事务，您可以执行一系列此类调用，同时保持回滚这些调用的能力。 如果关键资源不可用或某些其他条件阻止完成整个事务，则可以回滚事务，而不是提交该事务。 在这种情况下，属于事务的更改都不会影响数据源。

> [!NOTE]
> 目前，如果`CRecordset`已实现批量行提取，类不支持对数据源的更新。 `AddNew`这意味着您不能对`Edit`、 或`Delete``Update`进行调用。 但是，您可以编写自己的函数来执行更新，然后在给定事务中调用这些函数。 有关批量行提取的详细信息，请参阅[记录集：批量提取记录 （ODBC）。](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

> [!NOTE]
> 除了`CDatabase`影响记录集之外，事务会影响您直接执行的 SQL 语句，只要您使用与对象关联的 ODBC **HDBC**或基于该**HDBC**的 ODBC **HSTMT。**

当您有多个必须同时更新的记录时，事务特别有用。 在这种情况下，您希望避免半已完成的事务，例如，如果在上次更新之前引发异常，则可能发生异常。 将此类更新分组到事务中允许从更改中恢复（回滚）并将记录返回到事务前状态。 例如，如果银行将资金从账户 A 转移到帐户 B，则从 A 取款和存款到 B 都必须成功正确处理资金，否则整个交易必须失败。

在数据库类中，通过`CDatabase`对象执行事务。 对象`CDatabase`表示与数据源的连接，与该`CDatabase`对象关联的一个或多个记录集通过记录集成员函数对数据库的表进行操作。

> [!NOTE]
> 仅支持一个级别的事务。 不能嵌套事务，也不能跨多个数据库对象。

以下主题提供有关如何执行事务的详细信息：

- [事务：在记录集中执行事务 (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)

- [事务：事务如何影响更新 (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)

## <a name="see-also"></a>另请参阅

[开放数据库连接 （ODBC）](../../data/odbc/open-database-connectivity-odbc.md)
