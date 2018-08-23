---
title: 动态集 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5bd6abb1985ca50e7f63e600452b826972d403f1
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340425"
---
# <a name="dynaset"></a>动态集
本主题介绍动态集，并讨论了他们[可用性](#_core_availability_of_dynasets)。  
  
> [!NOTE]
>  本主题适用于 MFC ODBC 类，其中包括[CRecordset](../../mfc/reference/crecordset-class.md)。 在 DAO 类中的动态集有关的信息，请参阅[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。 使用 DAO，可以打开动态集类型的记录集。  
  
 动态集是具有动态属性的记录集。 在其生存期内，记录集对象 （通常称为动态集） 的动态集模式与源保持同步数据如下所示。 在多用户环境中，其他用户可能编辑或删除您的动态集的记录或将记录添加到你的动态集表示表。 你的应用程序将添加到或从记录集中删除的记录将反映在您的动态集。 其他用户添加到表的记录将不会反映在您的动态集之前调用重建动态集及其`Requery`成员函数。 当其他用户删除记录时，MFC 代码跳过为记录集中删除。 只要滚动到受影响的记录，与现有记录的其他用户的编辑更改将反映在您的动态集。  
  
 同样中动态集, 的记录所做的编辑将反映在正在使用的动态集由其他用户。 直到它们再次查询其动态，您添加的记录不会反映在其他用户的需求。 您删除的记录标记为"已删除"其他用户的记录集内。 如果有多个连接到同一数据库 (多个`CDatabase`对象)，这些连接关联的记录集中具有相同的状态作为记录集的其他用户。  
  
 当数据必须是动态的作为 （例如） 航空订票系统中，动态集是最有价值。  
  
> [!NOTE]
>  若要使用动态集，必须具有 ODBC 驱动程序的数据源支持动态集和必须加载 ODBC 游标库。 有关详细信息，请参阅[动态集可用性](#_core_availability_of_dynasets)。  
  
 若要指定记录集是动态集，请将传递`CRecordset::dynaset`的第一个参数作为`Open`的记录集对象的成员函数。  
  
> [!NOTE]
>  可更新的动态集，ODBC 驱动程序必须支持任一定位的 update 语句或`::SQLSetPos`ODBC API 函数。 如果两者都受支持，MFC 使用`::SQLSetPos`以提高效率。  
  
##  <a name="_core_availability_of_dynasets"></a> 动态集的可用性  
 MFC 数据库类支持动态集，如果满足以下要求：  
  
-   ODBC 游标库 DLL 不能用于此数据源。  
  
     如果使用游标库，则它会屏蔽基础 ODBC 驱动程序所需的动态集支持的一些功能。 如果你想要使用动态集 （和 ODBC 驱动程序具有动态集，所需的功能，如在本部分的其余部分所述），可以使 MFC 不加载游标库，在创建时`CDatabase`对象。 有关详细信息，请参阅[ODBC](../../data/odbc/odbc-basics.md)并[OpenEx](../../mfc/reference/cdatabase-class.md#openex)或[打开](../../mfc/reference/cdatabase-class.md#open)类的成员函数`CDatabase`。  
  
     在 ODBC 术语中，动态集和快照都称为游标。 游标是一种机制，用于跟踪中记录集的位置使用。  
  
-   您的数据源的 ODBC 驱动程序必须支持由键集驱动的游标。  
  
     由键集驱动的游标通过获取并存储密钥的一组表中管理数据。 密钥用于在用户滚动到特定记录上时从表中获取当前数据。 若要确定您的驱动程序是否提供此支持，请调用`::SQLGetInfo`与 ODBC API 函数*SQL_SCROLL_OPTIONS*参数。  
  
     如果您尝试打开不由键集支持动态集，则获取`CDBException`，返回代码值 AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED。  
  
-   您的数据源的 ODBC 驱动程序必须支持扩展获取。  
  
     扩展获取是能够向后滚动，以及通过 SQL 查询的结果记录转发。 若要确定您的驱动程序是否支持此功能，请调用`::SQLGetFunctions`与 ODBC API 函数*SQL_API_SQLEXTENDEDFETCH*参数。  
  
 如果您希望可更新的动态集 （或快照，就此而言），ODBC 驱动程序还必须支持任一`::SQLSetPos`ODBC API 函数或定位的更新。 `::SQLSetPos`函数使 MFC 更新而无需将 SQL 语句发送的数据源。 此支持，MFC 就使用它而不进行更新使用 SQL。 若要确定您的驱动程序是否支持`::SQLSetPos`，调用`::SQLGetInfo`与*SQL_POS_OPERATIONS*参数。  
  
 定位的更新使用的 SQL 语法 (窗体**WHERE CURRENT OF** \<cursorname >) 来标识数据源上的表中的特定行。 若要确定您的驱动程序是否支持定位的更新，请调用`::SQLGetInfo`与*SQL_POSITIONED_STATEMENTS*参数。  
  
 通常情况下，MFC 动态集 （但不是仅向前的记录集） 需要使用 2 级 API 一致性的 ODBC 驱动程序。 如果您的数据源的驱动程序符合级别 1 API 集，您仍可以使用可更新和只读快照和只进的记录集，但不是能使用动态集。 但是，如果它支持扩展获取动态集和由键集驱动游标可以支持第 1 级驱动程序。 有关 ODBC 一致性级别的详细信息，请参阅[ODBC](../../data/odbc/odbc-basics.md)。  
  
> [!NOTE]
>  如果你想要使用快照和动态集，必须将它们建立在两个不同`CDatabase`对象 （两个不同的连接）。  
  
 与不同的快照，使用 ODBC 游标库中间存储来维护，动态集获取一条记录直接从数据源就立即向滚动到它。 这会使情况下与数据源同步动态集最初选择的记录。  
  
 有关此版本的 Visual c + + 中包含的 ODBC 驱动程序的列表和有关获取其他驱动程序的信息，请参阅[ODBC 驱动程序列表](../../data/odbc/odbc-driver-list.md)。  
  
## <a name="see-also"></a>请参阅  
 [开放式数据库连接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)