---
title: "动态集 |Microsoft 文档"
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
- ODBC recordsets, dynasets
- ODBC cursor library [ODBC], dynasets
- keyset-driven cursors in dynasets
- cursors [ODBC], keyset-driven cursors in dynasets
- cursor library [ODBC], dynaset availability
- recordsets [C++], dynasets
- dynasets
ms.assetid: 2867e6be-208e-4fe7-8bbe-b8697cb1045c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f0f2f7ddd4a1b4021dfff8d533bb81acd84129a4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="dynaset"></a>动态集
本主题介绍动态集，并讨论了其[可用性](#_core_availability_of_dynasets)。  
  
> [!NOTE]
>  本主题适用于 MFC ODBC 类，包括[CRecordset](../../mfc/reference/crecordset-class.md)。 有关在 DAO 类中的动态记录集的信息，请参阅[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。 使用 DAO，你可以打开动态集类型记录集。  
  
 动态集是具有动态属性的记录集。 在其生存期内，在动态集模式下 （通常称为动态集） 的记录集对象保持同步与数据源以下列方式。 在多用户环境中，其他用户可能编辑或删除在您的动态集中的记录或将记录添加到你的动态集表示表。 你的应用程序将添加到或从记录集中删除的记录将反映在您的动态集中。 其他用户将添加到表的记录将不会反映在您的动态集中之前通过调用重建动态集其**Requery**成员函数。 当其他用户删除记录时，MFC 代码跳过删除的记录集中。 滚动到受影响的记录时，就会立即，对现有记录的其他用户的编辑更改会反映在你的动态集中。  
  
 同样，编辑您对中动态集的记录会反映在正在使用的动态集由其他用户。 它们的类型重新查询其动态记录集之前，您添加的记录不会反映在其他用户的动态记录集。 删除的记录将被标记为"已删除"其他用户的记录集内。 如果你有多个连接到同一数据库 (多个`CDatabase`对象)，这些连接与关联的记录集具有相同状态作为其他用户的记录集。  
  
 当数据必须是动态的作为 （例如） 航空订票系统中，动态记录集是最有价值。  
  
> [!NOTE]
>  若要使用动态记录集，必须具有 ODBC 驱动程序的数据源支持动态记录集和 ODBC 游标库必须未加载。 有关详细信息，请参阅[动态集可用性](#_core_availability_of_dynasets)。  
  
 若要指定记录集是动态集，请将传递**CRecordset::dynaset**的第一个参数作为**打开**的记录集对象的成员函数。  
  
> [!NOTE]
>  可更新动态记录集，ODBC 驱动程序必须支持任一定位的更新语句或**:: SQLSetPos** ODBC API 函数。 如果支持这两，MFC 使用**:: SQLSetPos**为提高效率。  
  
##  <a name="_core_availability_of_dynasets"></a>动态集的可用性  
 MFC 数据库类支持动态记录集，如果满足以下要求：  
  
-   ODBC 游标库 DLL 不能用于此数据源。  
  
     如果使用的是光标库，则它会屏蔽基础的 ODBC 驱动程序所需的动态集支持的某些功能。 如果你想要使用动态记录集 （和 ODBC 驱动程序具有动态集，所需的功能，如本部分的其余部分中所述），你可能会导致无法加载的是光标库，当你创建的 MFC`CDatabase`对象。 有关详细信息，请参阅[ODBC](../../data/odbc/odbc-basics.md)和[OpenEx](../../mfc/reference/cdatabase-class.md#openex)或[打开](../../mfc/reference/cdatabase-class.md#open)类的成员函数`CDatabase`。  
  
     在 ODBC 术语中，动态记录集和快照统称为游标。 一种用于跟踪其位置在记录集中使用的机制。  
  
-   您的数据源的 ODBC 驱动程序必须支持由键集驱动的游标。  
  
     键集驱动游标通过获取并存储的密钥集，从表中管理数据。 密钥用于从表中获取当前数据，当用户滚动到特定的记录。 若要确定您的驱动程序是否提供此支持，请调用**:: SQLGetInfo**具有 ODBC API 函数**SQL_SCROLL_OPTIONS**参数。  
  
     如果你尝试打开不由键集支持动态集，则获取`CDBException`，返回代码值**AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED**。  
  
-   您的数据源的 ODBC 驱动程序必须支持扩展提取。  
  
     扩展提取是能够向后滚动，以及通过将 SQL 查询的结果记录转发。 若要确定您的驱动程序是否支持此功能，请调用**:: SQLGetFunctions**具有 ODBC API 函数**SQL_API_SQLEXTENDEDFETCH**参数。  
  
 如果你想可更新动态记录集 （或快照，其实），ODBC 驱动程序还必须支持任一**:: SQLSetPos** ODBC API 函数或定位的更新。 **:: SQLSetPos**函数使 MFC 能够更新数据源而无需发送 SQL 语句。 此支持，MFC 就使用它进行更新使用 SQL 优先。 若要确定您的驱动程序是否支持**:: SQLSetPos**，调用**:: SQLGetInfo**与**SQL_POS_OPERATIONS**参数。  
  
 定位的更新使用 SQL 语法 (窗体的**WHERE CURRENT OF** \<cursorname >) 以标识数据源上的表中的特定行。 若要确定您的驱动程序是否支持定位的更新，请调用**:: SQLGetInfo**与**SQL_POSITIONED_STATEMENTS**参数。  
  
 通常情况下，MFC 动态记录集 （但不是仅向前的记录集） 需要使用 2 级 API 一致性 ODBC 驱动程序。 如果您的数据源的驱动程序符合 1 级 API 集，你仍然可以使用可更新和只读快照以及只进的记录集，但不是能使用动态集。 但是，第 1 级驱动程序可以支持动态记录集如果它支持扩展提取和键集驱动游标。 有关 ODBC 一致性级别的详细信息，请参阅[ODBC](../../data/odbc/odbc-basics.md)。  
  
> [!NOTE]
>  如果你想要使用快照和动态集，必须将它们建立在两个不同`CDatabase`对象 （两个不同的连接）。  
  
 与快照，使用 ODBC 游标库中间存储维护，不同动态记录集获取该记录直接从数据源就会立即向滚动到它。 这将保持最初通过动态集与数据源同步所选的记录。  
  
 有关此版本的 Visual c + + 中包含的 ODBC 驱动程序的列表以及有关获取其他驱动程序的信息，请参阅[ODBC 驱动程序列表](../../data/odbc/odbc-driver-list.md)。  
  
## <a name="see-also"></a>请参阅  
 [开放式数据库连接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)