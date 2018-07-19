---
title: 'ODBC: ODBC 游标库 |Microsoft 文档'
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
ms.openlocfilehash: e57251263738d534b7e7e22ff287607fbc5159a5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33092589"
---
# <a name="odbc-the-odbc-cursor-library"></a>ODBC：ODBC 游标库
本主题介绍 ODBC 游标库，并说明如何使用它。 有关详细信息，请参见:  
  
-   [游标库和第 1 级 ODBC 驱动程序](#_core_the_cursor_library_and_level_1_odbc_drivers)  
  
-   [定位的更新以及时间戳列](#_core_positioned_updates_and_timestamp_columns)  
  
-   [使用的是光标库](#_core_using_the_cursor_library)  
  
 ODBC 游标库是动态链接库 (DLL) 位于之间 ODBC 驱动程序管理器和驱动程序。 在 ODBC 术语中，驱动程序维护一个游标来跟踪它中记录集的位置。 光标将标记中与其已具有滚动记录集的位置-当前记录。  
  
##  <a name="_core_the_cursor_library_and_level_1_odbc_drivers"></a> 游标库和第 1 级 ODBC 驱动程序  
 ODBC 游标库为 1 级驱动程序提供了以下新功能：  
  
-   向前和向后滚动。 级别 2 驱动程序不需要的是光标库，因为它们已是可滚动。  
  
-   支持的快照。 游标库管理包含快照的记录的缓冲区。 此缓冲区反映程序的删除和编辑记录，但不是添加、 删除或其他用户的编辑。 因此，快照仅为当前为光标库的缓冲区。 缓冲区也不会反映你自己添加直到你调用**Requery**。 动态集不使用的是光标库。  
  
 游标库提供快照 （静态游标） 即使您的驱动程序通常不支持。 如果您的驱动程序已支持静态游标，你不需要加载的是光标库来获取快照支持。 如果你使用的是光标库，你可以仅使用快照和只进的记录集。 如果您的驱动程序支持动态记录集 （KEYSET_DRIVEN 游标） 和你想要使用它们，你必须使用的是光标库。 如果你想要使用快照和动态集，必须将它们建立在两个不同`CDatabase`对象 （两个不同的连接），除非您的驱动程序同时支持。  
  
##  <a name="_core_positioned_updates_and_timestamp_columns"></a> 定位的更新以及时间戳列  
  
> [!NOTE]
>  ODBC 数据源是通过 MFC ODBC 类，如本主题中所述，或通过 MFC 数据访问对象 (DAO) 类访问。  
  
> [!NOTE]
>  如果 ODBC 驱动程序支持**SQLSetPos**，MFC 使用如果可用，本主题不适用于你。  
  
 大多数级别 1 驱动程序不支持定位的更新。 此类驱动程序依赖于的是光标库来模拟级别 2 驱动程序的功能在这一点。 游标库执行的不变的字段在搜索的更新，以模拟定位的更新支持。  
  
 在某些情况下，记录集可能包含一个时间戳列作为其中一个不变字段。 对包含时间戳列的表使用 MFC 记录集产生两个问题。  
  
 第一个问题涉及对具有时间戳列的表的可更新快照。 如果你快照绑定到表包含时间戳列，则应调用**Requery**调用后**编辑**和**更新**。 如果没有，你可能不能再次编辑同一个记录。 当调用**编辑**然后**更新**、 记录写入到数据源和更新时间戳列。 如果不调用**Requery**，在快照中的记录的时间戳值不再匹配数据源上的相应时间戳。 当你尝试再次更新该记录时，数据源可能允许更新，由于不匹配。  
  
 第二个问题涉及的类限制[CTime](../../atl-mfc-shared/reference/ctime-class.md)一起使用时`RFX_Date`函数传输到或从表的时间和日期信息。 处理`CTime`对象增加额外的数据传输过程的中间处理窗体中的一些系统开销。 日期范围`CTime`对象可能也极大地限制某些应用程序。 新版本`RFX_Date`函数采用一个 ODBC **TIMESTAMP_STRUCT**参数而不是`CTime`对象。 有关详细信息，请参阅`RFX_Date`中[宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)中*MFC 参考*。  

  
##  <a name="_core_using_the_cursor_library"></a> 使用的是光标库  
 当你连接到数据源-通过调用[CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex)或[CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) -你可以指定是否为数据源使用的是光标库。 如果要在该数据源上创建快照，指定**CDatabase::useCursorLib**选项`dwOptions`参数`OpenEx`或指定**TRUE**为**bUseCursorLib**参数**打开**(默认值是**TRUE**)。 如果你的 ODBC 驱动程序支持动态记录集，并且你想要打开数据源上的动态记录集，则不要使用游标库 （它会屏蔽需要动态集的某些驱动程序功能）。 在这种情况下，未指定**CDatabase::useCursorLib**中`OpenEx`或指定**FALSE**为**bUseCursorLib**中的参数**打开**.  
  
## <a name="see-also"></a>请参阅  
 [ODBC 基础](../../data/odbc/odbc-basics.md)