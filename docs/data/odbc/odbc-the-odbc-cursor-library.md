---
title: 'ODBC: ODBC 游标库 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 064683c3905e7ad8ba1e405bd3963832c65cff57
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340399"
---
# <a name="odbc-the-odbc-cursor-library"></a>ODBC：ODBC 游标库
本主题介绍 ODBC 游标库，并说明如何使用它。 有关详细信息，请参见:  
  
-   [游标库和第 1 级 ODBC 驱动程序](#_core_the_cursor_library_and_level_1_odbc_drivers)  
  
-   [定位的更新和时间戳列](#_core_positioned_updates_and_timestamp_columns)  
  
-   [使用游标库](#_core_using_the_cursor_library)  
  
 ODBC 游标库是 ODBC 驱动程序管理器和驱动程序之间的动态链接库 (DLL)。 在 ODBC 术语中，驱动程序维护一个游标来跟踪中记录集的位置。 光标将标记已滚动到的记录集中的位置 — 当前记录。  
  
##  <a name="_core_the_cursor_library_and_level_1_odbc_drivers"></a> 游标库和第 1 级 ODBC 驱动程序  
 ODBC 游标库为 1 级驱动程序提供了以下新功能：  
  
-   向前和向后滚动。 第 2 级驱动程序不需要该游标库，因为它们是可滚动。  
  
-   对快照的支持。 游标库管理包含快照的记录的缓冲区。 此缓冲区反映程序的删除和编辑记录，但不是添加、 删除或编辑其他用户。 因此，快照是仅为当前游标库的缓冲区。 缓冲区也不会反映添加您在您调用之前`Requery`。 动态集不使用游标库。  
  
 即使您的驱动程序通常不支持，游标库可以为您提供快照 （静态游标）。 如果您的驱动程序已支持静态游标，您不需要加载游标库以获取快照的支持。 如果您使用游标库，可以使用仅快照和只进的记录集。 如果您的驱动程序支持动态集 （KEYSET_DRIVEN 游标），并且你想要使用它们，您必须使用游标库。 如果你想要使用快照和动态集，必须将它们建立在两个不同`CDatabase`对象 （两个不同的连接），除非您的驱动程序支持。  
  
##  <a name="_core_positioned_updates_and_timestamp_columns"></a> 定位的更新和时间戳列  
  
> [!NOTE]
>  ODBC 数据源是可通过 MFC ODBC 类，如本主题中所述或 MFC 数据访问对象 (DAO) 类的访问。  
  
> [!NOTE]
>  如果您的 ODBC 驱动程序支持`SQLSetPos`，MFC 使用如果可用，本主题不适用于您。  
  
 大多数 1 级驱动程序不支持定位的更新。 此类驱动程序依赖于该游标库来模拟在这方面的第 2 级驱动程序的功能。 游标库执行操作上不变的字段的搜索的更新，以模拟定位的更新支持。  
  
 在某些情况下，记录集可能包含一个时间戳列作为不变字段之一。 在包含时间戳列的表中使用 MFC 的记录集产生两个问题。  
  
 第一个问题涉及具有时间戳列的表的可更新快照。 如果在快照绑定到的表包含时间戳列，则应调用`Requery`调用之后`Edit`和`Update`。 如果没有，您可能不能再次编辑同一条记录。 当您调用`Edit`，然后`Update`、 记录写入到数据源和更新时间戳列。 如果不调用`Requery`，快照中记录的时间戳值不再匹配数据源上的相应时间戳。 当你尝试再次更新该记录时，则数据源可能由于不匹配允许更新。  
  
 第二个问题涉及的类的限制[CTime](../../atl-mfc-shared/reference/ctime-class.md)一起使用时`RFX_Date`函数传输到或从表的日期和时间信息。 处理`CTime`对象增加额外的中间处理在数据传输过程中窗体中的一些系统开销。 日期范围`CTime`对象可能也极大地限制对于某些应用程序。 新版`RFX_Date`函数采用 ODBC *TIMESTAMP_STRUCT*参数而不是`CTime`对象。 有关详细信息，请参阅`RFX_Date`中[宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)中*MFC 参考*。  

  
##  <a name="_core_using_the_cursor_library"></a> 使用游标库  
 在连接到数据源时，通过调用[不同](../../mfc/reference/cdatabase-class.md#openex)或[CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) — 您可以指定是否为数据源使用游标库。 如果要在该数据源上创建快照，指定`CDatabase::useCursorLib`选项`dwOptions`参数`OpenEx`，或指定为 TRUE，数据*bUseCursorLib*参数`Open`（默认值是为 TRUE)。 如果您的 ODBC 驱动程序支持动态集，并且你想要打开数据源上的动态集，则不要使用游标库 （它会屏蔽一些驱动程序的功能所需的动态集）。 在这种情况下，未指定`CDatabase::useCursorLib`中`OpenEx`或指定为 FALSE *bUseCursorLib*中的参数`Open`。  
  
## <a name="see-also"></a>请参阅  
 [ODBC 基础](../../data/odbc/odbc-basics.md)