---
title: "快照 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c31e08fdda3cef526f46946e45ef956f9ad1adaa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="snapshot"></a>快照
快照是反映数据的静态视图时创建快照时存在的记录集。 当你打开快照，并将移动到的所有记录时，它包含的记录集，直到调用重建快照不会更改其值**Requery**。  
  
> [!NOTE]
>  本主题适用于 MFC ODBC 类。 如果您使用 MFC DAO 类而不 MFC ODBC 类，请参阅[cdaorecordset:: Open](../../mfc/reference/cdaorecordset-class.md#open)有关快照类型记录集的说明。  
  
 可以使用数据库类来创建可更新或只读快照。 与动态集，不同的可更新的快照不会反映记录值其他用户所做的更改，但它反映更新和删除你的程序所做的。 添加到快照的记录不会对快照可见直到你调用**Requery**。  
  
> [!TIP]
>  快照是 ODBC 静态游标。 静态游标不真正获取数据行滚动到该记录之前。 若要确保立即检索的所有记录，可以滚动到记录集的末尾，然后向下滚动到想要查看的第一个记录。 但是，请注意，滚动到结束需要额外的开销并降低性能。  
  
 当你需要在你的操作，作为何时提供生成的报表，或执行计算过程中保持固定的数据时，快照具有最有价值。 即便如此，数据源可以显著和快照可能不同，因此你可能想要不时地重新生成。  
  
 要支持快照开始算起 ODBC 游标库，其中提供静态游标定位为任何级别 1 驱动程序更新 （updateability 所需）。 必须在这种支持内存中加载的是光标库 DLL。 构造时`CDatabase`对象并调用其`OpenEx`成员函数，您必须指定**CDatabase::useCursorLib**选项`dwOptions`参数。 如果调用**打开**成员函数，光标库加载默认情况下。 如果将动态记录集而不快照，您不想要导致要加载的是光标库。  
  
 快照是 ODBC 游标库加载时才可用`CDatabase`对象构造的或正在使用的 ODBC 驱动程序支持静态游标。  
  
> [!NOTE]
>  对于某些 ODBC 驱动程序中，快照 （静态游标） 可能不是可更新。 检查你驱动程序文档，了解支持的游标类型和它们支持的并发类型。 若要确保可更新的快照，请确保你在创建时，游标库加载到内存`CDatabase`对象。 有关详细信息，请参阅[ODBC: ODBC 游标库](../../data/odbc/odbc-the-odbc-cursor-library.md)。  
  
> [!NOTE]
>  如果你想要使用快照和动态集，必须将它们建立在两个不同`CDatabase`对象 （两个不同的连接）。  
  
 关于属性快照共享的所有记录集的详细信息，请参阅[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)。 ODBC 和快照，包括 ODBC 游标库，有关详细信息，请参阅[ODBC](../../data/odbc/odbc-basics.md)。  
  
## <a name="see-also"></a>请参阅  
 [开放式数据库连接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)