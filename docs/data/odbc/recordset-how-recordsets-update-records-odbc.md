---
title: "记录集： 如何记录集更新记录 (ODBC) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- records, updating
- ODBC recordsets, updating
- recordsets, editing records
- updating recordsets
- recordsets, updating
ms.assetid: 5ceecc06-7a86-43b1-93db-a54fb1e717c7
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5ca360ce914fea69163a400df2f9bc00750920e7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="recordset-how-recordsets-update-records-odbc"></a>记录集：记录集如何更新记录 (ODBC)
本主题适用于 MFC ODBC 类。  
  
 除了其能够从数据源选择记录，记录集还可以 （可选） 更新或删除所选的记录或添加新的记录。 三个因素确定记录集的 updateability： 是否可更新连接的数据源，指定当创建记录集对象，并创建 SQL 的选项。  
  
> [!NOTE]
>  在其上的 SQL 你`CRecordset`基于对象可能会影响的记录集的 updateability。 例如，如果你的 SQL 包含联接或**GROUP BY**子句，则 MFC 会将 updateability 设置为**FALSE**。  
  
> [!NOTE]
>  本主题适用于派生自`CRecordset`中哪些批量行提取尚未实现。 如果你将批量行提取，请参阅[记录集： 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 本主题说明：  
  
-   [在记录集更新角色](#_core_your_role_in_recordset_updating)框架为你的用途和。  
  
-   [记录集持久化为编辑缓冲区](#_core_the_edit_buffer)和[动态记录集和快照之间的差异](#_core_dynasets_and_snapshots)。  
  
 [记录集： 如何 AddNew、 Edit 和删除工作 (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)描述了从记录集的角度来看这些函数的操作。  
  
 [记录集： 更多有关更新 (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md)记录集更新情景完成通过介绍事务如何影响更新、 滚动或关闭记录集如何影响正在更新，以及如何与其他更新你更新交互用户。  
  
##  <a name="_core_your_role_in_recordset_updating"></a>在记录集更新你的角色  
 下表显示你的角色中使用记录集来添加、 编辑或删除记录，以及框架为你的用途。  
  
### <a name="recordset-updating-you-and-the-framework"></a>更新记录集： 您和框架  
  
|你|框架|  
|---------|-------------------|  
|确定数据源是否可更新 （或可追加）。|提供[CDatabase](../../mfc/reference/cdatabase-class.md)用于测试数据源的 updateability 或 appendability 成员函数。|  
|打开一个可更新的记录集 （的任何类型）。||  
|确定记录集是否可以更新通过调用`CRecordset`如更新函数`CanUpdate`或`CanAppend`。||  
|调用记录集成员函数来添加、 编辑和删除记录。|管理你的记录集对象和数据源之间交换数据的机制。|  
|（可选） 使用事务来控制更新过程。|提供`CDatabase`成员函数来支持事务。|  
  
 有关事务的详细信息，请参阅[事务 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
##  <a name="_core_the_edit_buffer"></a>编辑缓冲区  
 共同，记录集的字段数据成员作为包含一条记录的编辑缓冲区-当前记录。 更新操作使用此缓冲区来操作的当前记录。  
  
-   当你将添加一条记录时，编辑缓冲区用于生成一条新记录。 在你完成添加记录后，先前的当前记录再次成为当前记录。  
  
-   当你更新时将会使用 （编辑） 的记录，编辑缓冲区，将记录集的字段数据成员设置为新值。 完成更新后，已更新的记录仍是最新。  
  
 当调用[AddNew](../../mfc/reference/crecordset-class.md#addnew)或[编辑](../../mfc/reference/crecordset-class.md#edit)，因此它可以根据需要更高版本还原存储当前记录。 当调用[删除](../../mfc/reference/crecordset-class.md#delete)当前记录不会存储，但标记为已删除，你必须向下滚动到另一个记录。  
  
> [!NOTE]
>  编辑缓冲区不起作用中删除记录。 当你删除当前记录时，记录被标记为删除，并滚动到另一条记录之前，记录集将是"而不是在上一条记录"。  
  
##  <a name="_core_dynasets_and_snapshots"></a>动态集和快照  
 [动态集](../../data/odbc/dynaset.md)当滚动到的记录将刷新记录的内容。 [快照](../../data/odbc/snapshot.md)是静态表示形式的记录，因此除非调用不会刷新记录的内容[Requery](../../mfc/reference/crecordset-class.md#requery)。 若要使用的动态记录集的所有功能，您必须使用符合 ODBC API 支持的正确级别的 ODBC 驱动程序。 有关详细信息，请参阅[ODBC](../../data/odbc/odbc-basics.md)和[动态集](../../data/odbc/dynaset.md)。  
  
## <a name="see-also"></a>另请参阅  
 [记录集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [记录集：AddNew、Edit 和 Delete 的工作方式 (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)