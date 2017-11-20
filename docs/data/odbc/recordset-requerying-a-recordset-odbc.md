---
title: "记录集： 再次查询记录集 (ODBC) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- recordsets, requerying
- requerying recordsets
- Requery method
- ODBC recordsets, requerying
- refreshing recordsets
ms.assetid: 4ebc3b5b-5b91-4f51-a967-245223c6b8e1
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e5cf85c4fc124388e723654a1f3a97e13237fe6b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="recordset-requerying-a-recordset-odbc"></a>记录集：再次查询记录集 (ODBC)
本主题适用于 MFC ODBC 类。  
  
 本主题说明如何使用记录集对象的类型重新查询 （即，刷新） 本身从数据库和你可能想要使用[Requery](../../mfc/reference/crecordset-class.md#requery)成员函数。  
  
 再次查询记录集的主要原因是：  
  
-   将最新记录由你或其他用户通过添加和删除其他用户 （删除已经反映在记录集） 的记录方面的记录集。  
  
-   刷新记录集根据不断变化的参数值。  
  
##  <a name="_core_bringing_the_recordset_up_to_date"></a>记录集向上推向日期  
 通常情况下，你将想要再次查询记录集对象以使其保持最新。 在多用户数据库环境中，其他用户可以更改数据的记录集的生命周期内。 有关当你记录集反映其他用户所做的更改和其他用户的记录集时反映所做的更改的详细信息，请参阅[记录集： 如何更新记录 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)和[动态集](../../data/odbc/dynaset.md).  
  
##  <a name="_core_requerying_based_on_new_parameters"></a>再次查询基于新的参数  
 另一个常用-和同等重要 — 利用[Requery](../../mfc/reference/crecordset-class.md#requery)是选择一组新的记录根据不断变化的参数值。  
  
> [!TIP]
>  查询速度是快可能很多，如果调用**Requery**用变化于直接调用的参数值**打开**试。  
  
##  <a name="_core_requerying_dynasets_vs.._snapshots"></a>再次查询动态记录集 vs。快照  
 因为动态记录集为了提供一组记录具有动态的最新数据，你想要再次查询动态，通常，如果你想要反映其他用户的添加件。 快照，另一方面，非常有用，因为可以安全地依赖于其静态内容，而准备报表、 计算总计，依次类推。 尽管如此，你有时可能想要查询以及快照。 在多用户环境中，由于其他用户更改数据库快照数据可能会失去与数据源的同步。  
  
#### <a name="to-requery-a-recordset-object"></a>再次查询记录集对象  
  
1.  调用[Requery](../../mfc/reference/crecordset-class.md#requery)成员函数的对象。  
  
 或者，你可以关闭并重新打开原始记录集。 在任一情况下，新的记录集表示数据源的当前状态。  
  
 有关示例，请参阅[记录视图： 填充列表框从第二个记录集](../../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md)。  
  
> [!TIP]
>  若要优化**Requery**性能，避免更改记录集的[筛选器](../../data/odbc/recordset-filtering-records-odbc.md)或[排序](../../data/odbc/recordset-sorting-records-odbc.md)。 更改仅之前调用的参数值**Requery**。  
  
 如果**Requery**调用将失败，你可以重试调用; 否则，你的应用程序应正常终止。 调用**Requery**或**打开**多种原因导致的任何可能会失败。 可能发生网络错误;或者，在调用期间发布的现有数据后但在之前获取新的数据，另一个用户可能获得独占访问权;或者无法删除记录集所依赖的表。  
  
## <a name="see-also"></a>另请参阅  
 [记录集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [记录集： 动态绑定数据列 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)   
 [记录集：创建和关闭记录集 (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)