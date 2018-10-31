---
title: 记录集： 添加记录大容量 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC recordsets, adding records
- recordsets, adding records
- bulk record additions to recordsets
ms.assetid: 4685f656-14b9-4f10-a1c5-147b2b89a0b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 53daf818b0ba17848723e3cad233452146d1c891
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50062569"
---
# <a name="recordset-adding-records-in-bulk-odbc"></a>记录集：批量添加记录 (ODBC)

本主题适用于 MFC ODBC 类。

MFC [CRecordset](../../mfc/reference/crecordset-class.md)类具有了新的优化，当向表中大容量添加新记录时，提高了效率。

> [!NOTE]
> 本主题适用于对象派生自`CRecordset`中的批量行提取尚未实现。 如果使用批量行提取，请参阅[记录集： 提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

新选项*dwOptions*参数[crecordset:: Open](../../mfc/reference/crecordset-class.md#open)成员函数`optimizeBulkAdd`，可以提高性能，而不会调用连续添加多个记录时`Requery`或`Close`。 脏之前第一个字段`Update`调用标记为已更新的后续`AddNew` / `Update`调用。

如果正在使用数据库类才能利用`::SQLSetPos`ODBC API 函数用于添加、 编辑和删除记录，此优化是不必要。

如果加载 ODBC 游标库或 ODBC 驱动程序不支持添加、 编辑和删除通过`::SQLSetPos`，这种优化应提高大容量增加了性能。 若要启用这种优化，设置*dwOptions*中的参数`Open`调用到以下记录集：

```
appendOnly | optimizeBulkAdd
```

## <a name="see-also"></a>请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[记录集：添加、更新和删除记录 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)<br/>
[记录集：锁定记录 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)