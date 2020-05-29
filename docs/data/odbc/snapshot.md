---
title: 快照
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC cursor library [ODBC], snapshots
- cursors [ODBC], static
- recordsets, snapshots
- snapshots, support in ODBC
- static cursors
- ODBC recordsets, snapshots
- cursor library [ODBC], snapshots
- snapshots
ms.assetid: b5293a52-0657-43e9-bd71-fe3785b21c7e
ms.openlocfilehash: e487b5abcc5eee4e3f4b1941100980eac4a040c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366910"
---
# <a name="snapshot"></a>快照

快照是一个记录集，反映创建快照时存在的数据的静态视图。 当您打开快照并移动到所有记录时，它包含的记录集及其值不会更改，直到通过调用`Requery`重新生成快照。

> [!NOTE]
> 本主题适用于 MFC ODBC 类。 如果使用 MFC DAO 类而不是 MFC ODBC 类，请参阅[CDaoRecordset：：打开](../../mfc/reference/cdaorecordset-class.md#open)以说明快照类型的记录集。

您可以使用数据库类创建可更新或只读快照。 与动态集不同，可更新的快照不反映其他用户对记录值所做的更改，但它确实反映了程序所做的更新和删除。 添加到快照的记录在调用`Requery`之前不会对快照可见。

> [!TIP]
> 快照是 ODBC 静态光标。 在滚动到该记录之前，静态游标实际上不会获取一行数据。 为了确保立即检索所有记录，可以滚动到记录集的末尾，然后滚动到要查看的第一个记录。 但是请注意，滚动到末尾需要额外的开销，并且会降低性能。

当您需要数据在操作期间保持固定时（如生成报表或执行计算时）时，快照最有价值。 即便如此，数据源也可能与快照有很大差异，因此您可能需要不时重建它。

快照支持基于 ODBC 游标库，该库为任何级别 1 驱动程序提供静态游标和定位更新（更新性需要）。 必须将游标库 DLL 加载到内存中才能获得此支持。 构造`CDatabase`对象并调用其`OpenEx`成员函数时，必须指定*dwOptions* `CDatabase::useCursorLib`参数的选项。 如果调用`Open`成员函数，则默认情况下将加载游标库。 如果使用动态集而不是快照，则不希望导致加载游标库。

仅当构建`CDatabase`对象时加载了 ODBC 游标库或您使用的 ODBC 驱动程序支持静态游标时，快照才可用。

> [!NOTE]
> 对于某些 ODBC 驱动程序，快照（静态游标）可能无法更新。 检查驱动程序文档，了解支持的游标类型及其支持的并发类型。 为了保证可更新的快照，请确保在创建对象时将游标库加载到内存中`CDatabase`。 有关详细信息，请参阅[ODBC：ODBC 光标库](../../data/odbc/odbc-the-odbc-cursor-library.md)。

> [!NOTE]
> 如果要同时使用快照和动态集，则必须将它们基于两个不同的`CDatabase`对象（两个不同的连接）。

有关快照共享所有记录集的属性的详细信息，请参阅[记录集 （ODBC）。](../../data/odbc/recordset-odbc.md) 有关 ODBC 和快照的详细信息（包括 ODBC 光标库），请参阅[ODBC](../../data/odbc/odbc-basics.md)。

## <a name="see-also"></a>另请参阅

[开放数据库连接 （ODBC）](../../data/odbc/open-database-connectivity-odbc.md)
