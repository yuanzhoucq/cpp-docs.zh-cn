---
title: 记录集： 锁定记录 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- locks [C++], recordsets
- optimistic locking
- pessimistic locking in ODBC
- recordsets [C++], locking records
- optimistic locking, ODBC
- ODBC recordsets [C++], locking records
- data [C++], locking
ms.assetid: 8fe8fcfe-b55a-41a8-9136-94a7cd1e4806
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 51c84014786b8c27def7a568b85da316079c2bc1
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50066326"
---
# <a name="recordset-locking-records-odbc"></a>记录集：锁定记录 (ODBC)

本主题适用于 MFC ODBC 类。

本主题说明：

- [类型的记录锁定可用](#_core_record.2d.locking_modes)。

- [如何在更新过程中锁定记录集中的记录集](#_core_locking_records_in_your_recordset)。

当使用记录集来更新数据源上的记录时，你的应用程序可以锁定记录，这样没有其他用户可以在同一时间更新的记录。 除非系统可以保证两个用户不能同时更新的记录，记录在同一时间更新两个用户的状态为未定义。

> [!NOTE]
>  本主题适用于对象派生自`CRecordset`中的批量行提取尚未实现。 如果已实现批量行提取，某些信息不适用。 例如，不能调用`Edit`和`Update`成员函数。 有关批量行提取的详细信息，请参阅[记录集： 提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

##  <a name="_core_record.2d.locking_modes"></a> 记录锁定模式

数据库类提供两个[记录锁定模式](../../mfc/reference/crecordset-class.md#setlockingmode):

- 乐观锁定 （默认值）

- 保守式锁定

更新记录发生在三个步骤：

1. 通过调用开始操作[编辑](../../mfc/reference/crecordset-class.md#edit)成员函数。

1. 更改当前记录的相应字段。

1. 结束操作，并通常提交更新 — 通过调用[更新](../../mfc/reference/crecordset-class.md#update)成员函数。

仅在对数据源的记录进行乐观锁定锁定`Update`调用。 如果您使用乐观锁定在多用户环境中，应用程序应处理`Update`失败条件。 保守式锁定调用时立即锁定记录`Edit`并不会释放它直到您调用`Update`(通过指示故障`CDBException`机制，不是由值为 FALSE 返回`Update`)。 保守式锁定有其他用户，对潜在性能产生负面影响，因为对同一条记录的并发访问可能需要等待完成的应用程序的`Update`过程。

##  <a name="_core_locking_records_in_your_recordset"></a> 锁定记录集中的记录

如果你想要更改记录集对象的[锁定模式](#_core_record.2d.locking_modes)从默认情况下，您必须更改此模式，然后再调用`Edit`。

#### <a name="to-change-the-current-locking-mode-for-your-recordset"></a>若要更改您记录集的当前锁定模式

1. 调用[SetLockingMode](../../mfc/reference/crecordset-class.md#setlockingmode)成员函数，指定`CRecordset::pessimistic`或`CRecordset::optimistic`。

新的锁定模式保持有效，直到你再次更改或关闭记录集。

> [!NOTE]
>  当前，相对较少的 ODBC 驱动程序支持悲观锁定。

## <a name="see-also"></a>请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[记录集：执行联接 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)<br/>
[记录集：添加、更新和删除记录 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)