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
ms.openlocfilehash: 0deb21a43ff17ca94efe29bdec37db7611331a86
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615808"
---
# <a name="transaction-odbc"></a>事务 (ODBC)

本主题适用于 MFC ODBC 类。

事务是一种方法进行分组或批处理中的更新的一系列[数据源](../../data/odbc/data-source-odbc.md)，以便所有更改同时提交，或如果回滚事务，则不提交。 如果不使用事务，则自动提交而不按需提交更改数据源。

> [!NOTE]
>  并非所有 ODBC 数据库驱动程序都支持的事务。 调用`CanTransact`成员函数在[CDatabase](../../mfc/reference/cdatabase-class.md)或[CRecordset](../../mfc/reference/crecordset-class.md)对象，以确定您的驱动程序是否支持给定数据库的事务。 请注意，`CanTransact`不会告知你的数据源是否提供了完整的事务支持。 你还必须调用`CDatabase::GetCursorCommitBehavior`并`CDatabase::GetCursorRollbackBehavior`后`CommitTrans`并`Rollback`检查对打开的事务影响`CRecordset`对象。

调用`AddNew`并`Edit`的成员函数`CRecordset`对象的数据源时调用立即影响`Update`。 `Delete` 调用还会立即生效。 与此相反，可以使用包含的多个调用的事务`AddNew`， `Edit`， `Update`，和`Delete`，这是执行但尚未提交直到您调用`CommitTrans`显式。 通过建立一个事务，可以保留回滚它们的功能的同时执行一系列的此类调用。 如果关键资源不可用或某些其他条件阻止完成整个事务，可以回滚而不是提交事务。 在这种情况下，任何属于该事务的更改不影响数据源。

> [!NOTE]
>  目前，类`CRecordset`不支持对数据源的更新，如果已实现批量行提取。 这意味着不能进行到调用`AddNew`， `Edit`， `Delete`，或`Update`。 但是，您可以编写自己的函数来执行更新，然后调用给定的事务中的这些函数。 有关批量行提取的详细信息，请参阅[记录集： 提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

> [!NOTE]
>  除了会影响您的记录集，事务会影响，只要您使用 ODBC 直接执行的 SQL 语句**HDBC**与关联您`CDatabase`对象或 ODBC **HSTMT**基于该**HDBC**。

当有多个必须同时更新的记录时，事务是特别有用。 在这种情况下，你想要避免半完成事务，例如，如果之前的最后一个更新已引发了异常可能会发生这种情况。 将这些更新组成一个事务允许恢复 （回滚） 所做的更改，并返回记录到事务前状态。 例如，如果银行将资金从帐户 A 转移到帐户 B，同时和存入 B 的取款必须成功才能正确处理款项，否则整个事务必须失败。

在数据库类中，您将执行通过交易`CDatabase`对象。 一个`CDatabase`对象表示与数据源的连接和一个或多个记录集相关联的`CDatabase`对象对记录集成员函数通过对数据库的表。

> [!NOTE]
>  只有一个级别的事务支持。 不能嵌套事务，也不能跨多个数据库对象。

以下主题提供有关如何执行事务的详细信息：

- [事务：在记录集中执行事务 (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)

- [事务：事务如何影响更新 (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)

## <a name="see-also"></a>请参阅

[开放式数据库连接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)