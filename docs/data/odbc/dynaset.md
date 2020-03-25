---
title: 动态集
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets, dynasets
- ODBC cursor library [ODBC], dynasets
- keyset-driven cursors in dynasets
- cursors [ODBC], keyset-driven cursors in dynasets
- cursor library [ODBC], dynaset availability
- recordsets [C++], dynasets
- dynasets
ms.assetid: 2867e6be-208e-4fe7-8bbe-b8697cb1045c
ms.openlocfilehash: ed7098600126005978c8b017e7db378fca4c1a68
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213234"
---
# <a name="dynaset"></a>动态集

本主题介绍动态集并讨论其[可用性](#_core_availability_of_dynasets)。

> [!NOTE]
>  本主题适用于 MFC ODBC 类，包括[CRecordset](../../mfc/reference/crecordset-class.md)。 有关 DAO 类中的动态集的信息，请参阅[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。 借助 DAO，可以打开动态集类型的记录集。

动态集是包含动态属性的记录集。 在其生存期内，动态集模式下的记录集对象（通常称为动态集）将按以下方式与数据源保持同步。 在多用户环境中，其他用户可以编辑或删除动态集中的记录，或将记录添加到你的动态集表示的表中。 应用程序在记录集中添加或删除的记录将反映在动态集中。 其他用户添加到表中的记录将不会反映在您的动态集中，直到您通过调用其 `Requery` 成员函数重新生成动态集。 当其他用户删除记录时，MFC 代码将跳过记录集中的删除操作。 当滚动到受影响的记录后，其他用户对现有记录所做的编辑更改将立即反映在动态集中。

同样，在动态集中对记录所做的编辑将反映在其他用户使用的动态集中。 添加的记录在重新查询其动态集之前不会反映在其他用户的动态集中。 删除的记录在其他用户的记录集中被标记为 "已删除"。 如果有多个连接到同一个数据库（多个 `CDatabase` 对象），则与这些连接相关联的记录集与其他用户的记录集具有相同的状态。

当数据必须是动态的（例如）在航空公司预订系统中时，动态集是最有价值的。

> [!NOTE]
> 若要使用动态集，您必须具有支持动态集的数据源的 ODBC 驱动程序，并且不能加载 ODBC 游标库。 有关详细信息，请参阅[动态集的可用性](#_core_availability_of_dynasets)。

若要指定记录集为动态集，请将 `CRecordset::dynaset` 作为第一个参数传递给 recordset 对象的 `Open` 成员函数。

> [!NOTE]
> 对于可更新的动态集，ODBC 驱动程序必须支持定位的 update 语句或 `::SQLSetPos` ODBC API 函数。 如果两者都受支持，MFC 将使用 `::SQLSetPos` 提高效率。

##  <a name="availability-of-dynasets"></a><a name="_core_availability_of_dynasets"></a>动态集的可用性

如果满足以下要求，则 MFC 数据库类支持动态集：

- 此数据源不得使用 ODBC 游标库 DLL。

   如果使用游标库，它将屏蔽动态集支持所需的基础 ODBC 驱动程序的某些功能。 如果要使用动态集（并且 ODBC 驱动程序具有动态集所需的功能，如本部分的其余部分所述），则在创建 `CDatabase` 对象时，可能会导致 MFC 不加载游标库。 有关详细信息，请参阅[ODBC](../../data/odbc/odbc-basics.md)和类 `CDatabase`的[microsoft.office.interop.visio.documents.open](../../mfc/reference/cdatabase-class.md#openex)或[Open](../../mfc/reference/cdatabase-class.md#open)成员函数。

   在 ODBC 术语中，动态集和快照称为游标。 游标是一种用于在记录集中跟踪其位置的机制。

- 数据源的 ODBC 驱动程序必须支持由键集驱动的游标。

   由键集驱动的游标通过获取和存储一组密钥来管理表中的数据。 当用户滚动到特定记录时，使用这些键获取表中的当前数据。 若要确定驱动程序是否提供此支持，请调用 `::SQLGetInfo` 具有*SQL_SCROLL_OPTIONS*参数的 ODBC API 函数。

   如果尝试在没有键集支持的情况下打开动态集，则会收到一个 `CDBException`，其中返回代码值为 AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED。

- 数据源的 ODBC 驱动程序必须支持扩展提取。

   扩展提取是指向后滚动，并向前滚动 SQL 查询的结果记录。 若要确定驱动程序是否支持此功能，请调用 `::SQLGetFunctions` 具有*SQL_API_SQLEXTENDEDFETCH*参数的 ODBC API 函数。

如果需要可更新的动态集（或快照），ODBC 驱动程序还必须支持 `::SQLSetPos` ODBC API 函数或定位更新。 `::SQLSetPos` 函数允许 MFC 更新数据源，而无需发送 SQL 语句。 如果此支持可用，MFC 将使用它，以便使用 SQL 进行更新。 若要确定驱动程序是否支持 `::SQLSetPos`，请调用具有*SQL_POS_OPERATIONS*参数 `::SQLGetInfo`。

定位更新使用 SQL 语法（其**当前的**\<cursorname > 的形式）来标识数据源中的表中的特定行。 若要确定驱动程序是否支持定位更新，请调用与*SQL_POSITIONED_STATEMENTS*参数 `::SQLGetInfo`。

通常，MFC 动态集（而非只进记录集）需要具有2级 API 一致性的 ODBC 驱动程序。 如果数据源的驱动程序符合第1级 API 集，则仍可使用可更新和只读快照以及只进记录集，但不能使用动态集。 但是，如果第1级驱动程序支持扩展提取和由键集驱动的游标，则它可以支持动态集。 有关 ODBC 一致性级别的详细信息，请参阅[odbc](../../data/odbc/odbc-basics.md)。

> [!NOTE]
> 如果要同时使用快照和动态集，则必须将它们基于两个不同的 `CDatabase` 对象（两个不同的连接）。

与使用 ODBC 游标库维护的中间存储的快照不同，在滚动到数据源后，动态集会立即从数据源中提取记录。 这会保留最初由动态集选择的记录与数据源同步。

有关此版本的 Visual C++ 中包含的 ODBC 驱动程序列表以及有关获取其他驱动程序的信息，请参阅 [ODBC 驱动程序列表](../../data/odbc/odbc-driver-list.md)。

## <a name="see-also"></a>另请参阅

[开放式数据库连接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
