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
ms.openlocfilehash: abd5f817ad321241df2d8565bd6bf346c0792088
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366961"
---
# <a name="recordset-locking-records-odbc"></a>记录集：锁定记录 (ODBC)

本主题适用于 MFC ODBC 类。

本主题介绍：

- [可用的记录锁定类型](#_core_record.2d.locking_modes)。

- [如何在更新期间锁定记录集中的记录](#_core_locking_records_in_your_recordset)。

当您使用记录集更新数据源上的记录时，应用程序可以锁定该记录，以便其他用户无法同时更新记录。 除非系统可以保证两个用户不能同时更新记录，否则两个用户同时更新的记录的状态未定义。

> [!NOTE]
> 本主题适用于从 `CRecordset` 派生的对象，其中尚未实现批量提取行。 如果已实现批量行提取，则某些信息不适用。 例如，不能调用 和`Edit``Update`成员函数。 有关批量行提取的详细信息，请参阅[记录集：批量提取记录 （ODBC）。](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

## <a name="record-locking-modes"></a><a name="_core_record.2d.locking_modes"></a>记录锁定模式

数据库类提供两[种记录锁定模式](../../mfc/reference/crecordset-class.md#setlockingmode)：

- 乐观锁定（默认值）

- 悲观锁定

更新记录分三个步骤进行：

1. 通过调用["编辑](../../mfc/reference/crecordset-class.md#edit)"成员函数开始操作。

1. 更改当前记录的相应字段。

1. 通过调用[Update](../../mfc/reference/crecordset-class.md#update)成员函数，结束操作（通常提交更新）。

乐观锁定仅在`Update`调用期间锁定数据源上的记录。 如果在多用户环境中使用乐观锁定，则应用程序应处理`Update`故障情况。 悲观锁定`Edit`在调用时立即锁定记录，并且在调用`Update`之前不会释放它（故障通过`CDBException`机制指示，而不是由`Update`返回的 FALSE 值指示）。 悲观锁定对其他用户可能具有性能损失，因为对同一记录的并发访问可能必须等到应用程序`Update`的进程完成。

## <a name="locking-records-in-your-recordset"></a><a name="_core_locking_records_in_your_recordset"></a>在记录集中锁定记录

如果要从默认值更改记录集对象的[锁定模式](#_core_record.2d.locking_modes)，则必须在调用`Edit`之前更改该模式。

#### <a name="to-change-the-current-locking-mode-for-your-recordset"></a>更改记录集的当前锁定模式

1. 调用[SetLockingMode](../../mfc/reference/crecordset-class.md#setlockingmode)成员函数，指定`CRecordset::pessimistic``CRecordset::optimistic`或 。

新的锁定模式保持有效，直到您再次更改它或关闭记录集。

> [!NOTE]
> 目前支持悲观锁定的 ODBC 驱动程序相对较少。

## <a name="see-also"></a>另请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[记录集：执行联接 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)<br/>
[记录集：添加、更新和删除记录 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)
