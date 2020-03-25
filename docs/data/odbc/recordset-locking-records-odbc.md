---
title: 记录集：锁定记录 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- locks [C++], recordsets
- optimistic locking
- pessimistic locking in ODBC
- recordsets [C++], locking records
- optimistic locking, ODBC
- ODBC recordsets [C++], locking records
- data [C++], locking
ms.assetid: 8fe8fcfe-b55a-41a8-9136-94a7cd1e4806
ms.openlocfilehash: d4e80816a131c997e9f5bfaa34f025394b05a358
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212857"
---
# <a name="recordset-locking-records-odbc"></a>记录集：锁定记录 (ODBC)

本主题适用于 MFC ODBC 类。

本主题介绍：

- [可用的记录锁定种类](#_core_record.2d.locking_modes)。

- [如何在更新过程中锁定记录集中的记录](#_core_locking_records_in_your_recordset)。

当您使用记录集更新数据源上的记录时，您的应用程序可以锁定该记录，使其他用户不能同时更新记录。 如果系统不能保证两个用户不能同时更新记录，则不会定义两个用户同时更新的记录的状态。

> [!NOTE]
>  本主题适用于从 `CRecordset` 派生的对象，其中尚未实现批量提取行。 如果已实现批量行提取，则某些信息不适用。 例如，您不能调用 `Edit` 和 `Update` 成员函数。 有关批量行提取的详细信息，请参阅[记录集：批量提取记录（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

##  <a name="record-locking-modes"></a><a name="_core_record.2d.locking_modes"></a>记录锁定模式

数据库类提供两种[记录锁定模式](../../mfc/reference/crecordset-class.md#setlockingmode)：

- 开放式锁定（默认值）

- 悲观锁定

更新记录分为三个步骤：

1. 您可以通过调用[Edit](../../mfc/reference/crecordset-class.md#edit)成员函数来开始操作。

1. 您更改了当前记录的相应字段。

1. 可以通过调用[更新](../../mfc/reference/crecordset-class.md#update)成员函数结束操作（并通常提交更新）。

乐观锁定仅在 `Update` 调用期间锁定数据源上的记录。 如果在多用户环境中使用开放式锁定，则应用程序应处理 `Update` 故障条件。 在调用 `Edit` 时，保守式锁定会立即锁定记录，并且在调用 `Update` 之前不会将其释放（失败通过 `CDBException` 机制指示，而不是由 `Update`返回的 FALSE 值表示）。 对于其他用户，保守式锁定可能会造成性能下降，因为对同一记录的并发访问可能必须等待，直到应用程序的 `Update` 进程完成。

##  <a name="locking-records-in-your-recordset"></a><a name="_core_locking_records_in_your_recordset"></a>锁定记录集中的记录

如果要从默认值更改记录集对象的[锁定模式](#_core_record.2d.locking_modes)，则必须在调用 `Edit`之前更改该模式。

#### <a name="to-change-the-current-locking-mode-for-your-recordset"></a>更改记录集的当前锁定模式

1. 调用[SetLockingMode](../../mfc/reference/crecordset-class.md#setlockingmode)成员函数，同时指定 `CRecordset::pessimistic` 或 `CRecordset::optimistic`。

新的锁定模式始终有效，直到再次更改或记录集关闭。

> [!NOTE]
>  目前相对较少的 ODBC 驱动程序支持悲观锁定。

## <a name="see-also"></a>另请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[记录集：执行联接 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)<br/>
[记录集：添加、更新和删除记录 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)
