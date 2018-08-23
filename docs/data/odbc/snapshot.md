---
title: 快照 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: cb3f2f63d60cd5120479a66eea1fe6bdee91b8ac
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2018
ms.locfileid: "39338202"
---
# <a name="snapshot"></a>快照
快照是反映数据的静态视图时创建快照时存在的记录集。 当您打开快照并移动到的所有记录时，它包含的记录集和它们的值不变，除非通过调用重建快照`Requery`。  
  
> [!NOTE]
>  本主题适用于 MFC ODBC 类。 如果您使用 MFC DAO 类而不 MFC ODBC 类，请参阅[cdaorecordset:: Open](../../mfc/reference/cdaorecordset-class.md#open)快照类型的记录集的说明。  
  
 可以使用数据库类来创建可更新或只读快照。 与动态集，不同的可更新的快照不会反映更改，以记录所做的其他用户的值，但它反映更新和删除应用程序所做的。 记录添加到快照不会对快照可见直到您调用`Requery`。  
  
> [!TIP]
>  快照是 ODBC 静态游标。 在滚动到该记录之前，静态游标并不实际获取数据行。 若要确保立即检索所有记录，可以向下滚动到记录集的末尾，然后向下滚动到你想要查看的第一个记录。 但请注意，滚动至末尾需要额外的开销并降低性能。  
  
 当你需要在您的操作，为何时生成的报表或执行计算期间保持固定的数据时，快照是最有价值。 即便如此，数据源可以显著和快照的不同，因此可能需要不时重新生成它。  
  
 快照支持基于 ODBC 游标库，其中提供了静态游标和定位为任何级别 1 驱动程序更新 （所需的可更新性）。 在这种支持的内存中，必须加载游标库 DLL。 当构造`CDatabase`对象，并调用其`OpenEx`成员函数，则必须指定`CDatabase::useCursorLib`的选项*dwOptions*参数。 如果调用`Open`成员函数，该游标库加载默认情况下。 如果使用动态集而不快照，不要使游标库加载。  
  
 快照是仅当时被加载 ODBC 游标库可用`CDatabase`构造对象或正在使用的 ODBC 驱动程序支持静态游标。  
  
> [!NOTE]
>  对于某些 ODBC 驱动程序中，快照 （静态游标） 可能不是可更新。 检查您的驱动程序文档支持游标类型和它们支持的并发类型。 若要保证可更新的快照，请确保您在创建时，游标库加载到内存`CDatabase`对象。 有关详细信息，请参阅[ODBC: ODBC 游标库](../../data/odbc/odbc-the-odbc-cursor-library.md)。  
  
> [!NOTE]
>  如果你想要使用快照和动态集，必须将它们建立在两个不同`CDatabase`对象 （两个不同的连接）。  
  
 与所有记录集属性快照共享的详细信息，请参阅[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)。 有关 ODBC 和快照，包括 ODBC 游标库的详细信息请参阅[ODBC](../../data/odbc/odbc-basics.md)。  
  
## <a name="see-also"></a>请参阅  
 [开放式数据库连接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)