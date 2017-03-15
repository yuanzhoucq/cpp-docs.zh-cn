---
title: "ODBC：ODBC 游标库 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "游标库 [ODBC]"
  - "游标库 [ODBC], 快照"
  - "光标, ODBC 游标库"
  - "1 级 ODBC 驱动程序"
  - "ODBC 游标库 [ODBC]"
  - "ODBC 驱动程序, 光标支持"
  - "ODBC 驱动程序, 等级 1"
  - "ODBC, 时间戳"
  - "定位的更新"
  - "定位游标"
  - "快照, ODBC 中的支持"
  - "静态游标"
  - "时间戳, ODBC 时间戳列"
ms.assetid: 6608db92-82b1-4164-bb08-78153c227be3
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# ODBC：ODBC 游标库
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题介绍 ODBC 游标库并说明如何使用。  有关详细信息，请参阅：  
  
-   [游标库和 1 级 ODBC 驱动程序](#_core_the_cursor_library_and_level_1_odbc_drivers)  
  
-   [已定位的更新列和时间戳列](#_core_positioned_updates_and_timestamp_columns)  
  
-   [使用游表库](#_core_using_the_cursor_library)  
  
 ODBC 游标库是一个驻留在 ODBC 驱动程序管理器和驱动程序之间的动态链接库 \(DLL\)。  按照 ODBC 术语，驱动程序维护一个游标来跟踪它在记录集中的位置。  游标标记在记录集中已滚动到的位置，即当前记录。  
  
##  <a name="_core_the_cursor_library_and_level_1_odbc_drivers"></a> 游标库和 1 级 ODBC 驱动程序  
 ODBC 游标库赋予 1 级驱动程序下列新功能：  
  
-   前滚和后滚。  2 级驱动程序不需要游标库，因为它们已是可滚动的。  
  
-   支持快照。  游标库管理着包含快照记录的缓冲区。  此缓冲区反映程序对记录的删除和编辑，但不是其他用户的添加、删除或编辑。  因此，快照只与游标库的缓冲区一样新。  在您调用 **Requery** 之前，缓冲区也不反映您对记录所做的添加。  动态集不使用游标库。  
  
 即使驱动程序通常不支持快照，游标库仍会提供快照（静态游标）。  若您的驱动程序已经支持静态游标，则不再需要加载游标库来获取快照支持。  如果您确实在使用游标库，则只能使用快照和仅向前记录集。  如果您的驱动程序支持动态集（KEYSET\_DRIVEN 游标），而且您要使用它们，则一定不要使用游标库。  如果要同时使用快照和动态集，则必须将它们基于两个不同的 `CDatabase` 对象上（两条不同的连接）上，除非您的驱动程序同时支持快照和动态集。  
  
##  <a name="_core_positioned_updates_and_timestamp_columns"></a> 已定位的更新列和时间戳列  
  
> [!NOTE]
>  通过 MFC ODBC 类（如本主题所述）或通过 MFC 数据访问对象 \(DAO\) 类，都可以访问 ODBC 数据源。  
  
> [!NOTE]
>  如果您的 ODBC 驱动程序支持 **SQLSetPos**（只要有，MFC 就使用它），则本主题不适用于您。  
  
 多数 1 级驱动程序都不支持定位更新。  这些驱动程序依靠游标库来模拟 2 级驱动程序在这方面的功能。  游标库通过对不变的字段执行搜索更新来模拟定位更新支持。  
  
 在某些情况下，记录集可能包含一个时间戳列作为其中一个不变字段。  如果 MFC 记录集中的表含有时间戳列，使用这样的 MFC 记录集时，则会出现两个问题。  
  
 第一个问题关系到具有时间戳列的表上的可更新快照。  如果快照所绑定的表含有时间戳列，则应该在调用了 **Edit** 和 **Update** 之后调用 **Requery**。  否则，可能不能再次编辑同一记录。  调用 **Edit** 之后再调用 **Update** 时，将记录写入数据源，并更新时间戳列。  如果不调用 **Requery**，则快照中该记录的时间戳值不再与数据源上对应的时间戳值相符。  尝试再次更新该记录时，数据源可能因为值不相符而不允许更新。  
  
 第二个问题涉及在 [CTime](../../atl-mfc-shared/reference/ctime-class.md) 与 `RFX_Date` 函数一起使用，以向表中或从表中传输时间和日期信息时，对该类的限制。  由于数据传输过程中一些额外的中间处理，处理 `CTime` 对象要增加一些系统开销。  `CTime` 对象的日期范围也可能极大地限制某些应用程序。  `RFX_Date` 函数的新版本使用 ODBC **TIMESTAMP\_STRUCT** 参数，而不再使用 `CTime` 对象。  有关更多信息，请参见“MFC 参考”中的[宏和全局](../Topic/Macros,%20Global%20Functions,%20and%20Global%20Variables.md)中的 `RFX_Date`。  
  
##  <a name="_core_using_the_cursor_library"></a> 使用游表库  
 通过调用 [CDatabase::OpenEx](../Topic/CDatabase::OpenEx.md) 或 [CDatabase::Open](../Topic/CDatabase::Open.md) 连接到数据源时，可以指定是否将游标库用于数据源。  如果要在该数据源上创建快照，则将 `dwOptions` 参数中的 **CDatabase::useCursorLib** 选项指定为 `OpenEx`，或者将 **Open** 的 **bUseCursorLib** 参数指定为 **TRUE**（默认值即为 **TRUE**）。  假如您的 ODBC 驱动程序支持动态集，而且您要在数据源上打开动态集，则不要使用游标库（它会屏蔽动态集所需的某些驱动程序功能）。  这种情况下，不要指定 `OpenEx` 中的 **CDatabase::useCursorLib**，也不要将 **Open** 中的 **bUseCursorLib** 参数指定为 **FALSE**。  
  
## 请参阅  
 [ODBC 基础](../../data/odbc/odbc-basics.md)