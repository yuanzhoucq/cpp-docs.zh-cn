---
title: 记录集：批量添加记录 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets, adding records
- recordsets, adding records
- bulk record additions to recordsets
ms.assetid: 4685f656-14b9-4f10-a1c5-147b2b89a0b4
ms.openlocfilehash: f561cb0275933a973e97ef0518148e81e14a0234
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213013"
---
# <a name="recordset-adding-records-in-bulk-odbc"></a>记录集：批量添加记录 (ODBC)

本主题适用于 MFC ODBC 类。

MFC [CRecordset](../../mfc/reference/crecordset-class.md)类提供了一种新的优化，可在将新记录批量添加到表时提高效率。

> [!NOTE]
> 本主题适用于从 `CRecordset` 派生的对象，其中尚未实现批量提取行。 如果使用批量取行，请参阅[记录集：批量提取记录（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

当你在不调用 `Requery` 或 `Close`的情况下连续添加多条记录时，为[CRecordset：： Open](../../mfc/reference/crecordset-class.md#open)成员函数 `optimizeBulkAdd`的*dwOptions*参数提供了一个新选项。 只有在第一次 `Update` 调用之前已更新的字段将被标记为 "已更新"，之后 `AddNew`/`Update` 调用。

如果使用数据库类来利用 `::SQLSetPos` ODBC API 函数来添加、编辑和删除记录，则不需要此优化。

如果已加载 ODBC 游标库，或者 ODBC 驱动程序不支持通过 `::SQLSetPos`添加、编辑和删除，则此优化应该会提高大容量添加性能。 若要启用此优化，请将 `Open` 调用中的*dwOptions*参数设置为以下内容：

```
appendOnly | optimizeBulkAdd
```

## <a name="see-also"></a>另请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[记录集：添加、更新和删除记录 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)<br/>
[记录集：锁定记录 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
