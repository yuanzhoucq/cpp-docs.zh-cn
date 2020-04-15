---
title: ODBC：ODBC 游标库
ms.date: 11/04/2016
helpviewer_keywords:
- cursor library [ODBC]
- snapshots, support in ODBC
- timestamps, ODBC timestamp columns
- ODBC cursor library [ODBC]
- static cursors
- ODBC drivers, Level 1
- ODBC drivers, cursor support
- positioned updates
- cursors, ODBC cursor library
- Level 1 ODBC drivers
- cursor library [ODBC], snapshots
- ODBC, timestamp
- positioning cursors
ms.assetid: 6608db92-82b1-4164-bb08-78153c227be3
ms.openlocfilehash: 13640dd2a8593057bef708a45dfc8471ba212563
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367179"
---
# <a name="odbc-the-odbc-cursor-library"></a>ODBC：ODBC 游标库

本主题介绍 ODBC 游标库，并说明如何使用它。 有关详细信息，请参阅：

- [光标库和 1 级 ODBC 驱动程序](#_core_the_cursor_library_and_level_1_odbc_drivers)

- [定位更新和时间戳列](#_core_positioned_updates_and_timestamp_columns)

- [使用光标库](#_core_using_the_cursor_library)

ODBC 光标库是一个动态链接库 （DLL），位于 ODBC 驱动程序管理器和驱动程序之间。 在 ODBC 术语中，驱动程序维护一个游标，以跟踪其在记录集中的位置。 光标标记您已滚动到的记录集中的位置 - 当前记录。

## <a name="cursor-library-and-level-1-odbc-drivers"></a><a name="_core_the_cursor_library_and_level_1_odbc_drivers"></a>光标库和 1 级 ODBC 驱动程序

ODBC 游标库为 1 级驱动程序提供了以下新功能：

- 向前和向后滚动。 级别 2 驱动程序不需要游标库，因为它们已经是可滚动的。

- 支持快照。 游标库管理包含快照记录的缓冲区。 此缓冲区反映程序对记录的删除和编辑，而不是其他用户的添加、删除或编辑。 因此，快照仅与游标库的缓冲区一样最新。 在调用`Requery`之前，缓冲区也不会反映您自己的添加。 动态集不使用游标库。

游标库为您提供快照（静态游标），即使驱动程序通常不支持快照也是如此。 如果驱动程序已支持静态游标，则无需加载游标库来获取快照支持。 如果使用游标库，则只能使用快照和仅转发记录集。 如果驱动程序支持动态集（KEYSET_DRIVEN游标），并且想要使用它们，则不得使用游标库。 如果要同时使用快照和动态集，则必须将它们基于两个不同的`CDatabase`对象（两个不同的连接），除非您的驱动程序支持这两个对象。

## <a name="positioned-updates-and-timestamp-columns"></a><a name="_core_positioned_updates_and_timestamp_columns"></a>定位更新和时间戳列

> [!NOTE]
> ODBC 数据源可通过 MFC ODBC 类（如本主题所述）或通过 MFC 数据访问对象 （DAO） 类访问。

> [!NOTE]
> 如果您的 ODBC 驱动程序`SQLSetPos`支持 MFC 使用（如果可用），则本主题不适用于您。

大多数 1 级驱动程序不支持定位更新。 此类驱动程序依赖于游标库来模拟 2 级驱动程序在这方面的功能。 游标库通过在不变的字段上执行搜索更新来模拟定位更新支持。

在某些情况下，记录集可能包含时间戳列作为这些不变字段之一。 使用包含时间戳列的表的 MFC 记录集会产生两个问题。

第一个问题涉及具有时间戳列的表上的可更新快照。 如果快照绑定到的表包含时间戳列，则应在调用`Requery``Edit`和`Update`后调用 。 如果没有，可能无法再次编辑同一记录。 调用`Edit`然后`Update`调用 时，记录将写入数据源，并更新时间戳列。 如果不调用`Requery`，快照中记录的时间戳值不再与数据源上的相应时间戳匹配。 当您尝试再次更新记录时，数据源可能会由于不匹配而禁止更新。

第二个问题涉及类[CTime](../../atl-mfc-shared/reference/ctime-class.md)在与`RFX_Date`函数一起使用时限制将时间和日期信息传输到表或从表传输信息。 在数据传输`CTime`过程中，处理对象会以额外的中间处理的形式施加一些开销。 对于某些应用程序，`CTime`对象的日期范围可能也太有限。 函数的`RFX_Date`新版本采用 ODBC *TIMESTAMP_STRUCT*参数而不是`CTime`对象。 有关详细信息，请参阅`RFX_Date` *MFC 参考*中的[宏和全局](../../mfc/reference/mfc-macros-and-globals.md)。

## <a name="using-the-cursor-library"></a><a name="_core_using_the_cursor_library"></a>使用光标库

当您通过调用[CDatabase：：：OpenEx](../../mfc/reference/cdatabase-class.md#openex)或[CDatabase：：打开](../../mfc/reference/cdatabase-class.md#open)连接到数据源时，可以指定是否对数据源使用游标库。 如果要在该数据源上创建快照`CDatabase::useCursorLib`，请在`dwOptions`参数中指定 选项，`OpenEx`或为*bUseCursorLib*参数指定`Open`TRUE（默认值为 TRUE）。 如果您的 ODBC 驱动程序支持动态集，并且要在数据源上打开动态集，请不要使用游标库（它屏蔽了动态集所需的某些驱动程序功能）。 在这种情况下，不要在`CDatabase::useCursorLib`中`OpenEx`指定或指定 FALSE 中的*bUseCursorLib*`Open`bUseCursorLib 参数。

## <a name="see-also"></a>另请参阅

[ODBC 基础](../../data/odbc/odbc-basics.md)
