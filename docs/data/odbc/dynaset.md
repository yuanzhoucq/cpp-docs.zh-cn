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
ms.openlocfilehash: 2eb2447d1f984b7734d5e9c45087023e5a6f003f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371839"
---
# <a name="dynaset"></a>动态集

本主题介绍动态集并讨论其[可用性](#_core_availability_of_dynasets)。

> [!NOTE]
> 本主题适用于 MFC ODBC 类，包括[CRecordset。](../../mfc/reference/crecordset-class.md) 有关 DAO 类中的动态集的信息，请参阅[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。 使用 DAO，您可以打开动态集类型的记录集。

动态集是具有动态属性的记录集。 在其生存期内，动态集模式下的记录集对象（通常称为动态集）以以下方式与数据源保持同步。 在多用户环境中，其他用户可能会编辑或删除动态集中的记录，或将记录添加到动态集所代表的表中。 应用程序添加到的记录集中添加或删除的记录将反映在动态集中。 其他用户添加到表的记录不会反映在动态集中，直到您通过调用其`Requery`成员函数重建动态集。 当其他用户删除记录时，MFC 代码将跳过记录集中的删除。 滚动到受影响的记录后，其他用户对现有记录的编辑更改将立即反映在动态集中。

同样，对动态集中记录进行的编辑将反映在其他用户正在使用的动态集中。 您添加的记录不会反映在其他用户的动态集中，直到他们重新查询其动态集。 您删除的记录在其他用户的记录集中标记为"已删除"。 如果有多个连接到同一数据库（多个`CDatabase`对象），则与这些连接关联的记录集具有与其他用户的记录集相同的状态。

当数据必须是动态的时，Dynaset 最有价值，例如航空公司预订系统中的数据。

> [!NOTE]
> 要使用动态集，必须为数据源提供支持动态集的 ODBC 驱动程序，并且不得加载 ODBC 游标库。 有关详细信息，请参阅[动态集的可用性](#_core_availability_of_dynasets)。

要指定记录集是动态集，请作为第一个`CRecordset::dynaset`参数传递给记录集对象`Open`的成员函数。

> [!NOTE]
> 对于可更新的发电机组，您的 ODBC 驱动程序必须支持定位更新语句或`::SQLSetPos`ODBC API 功能。 如果两者都支持，MFC`::SQLSetPos`用于提高效率。

## <a name="availability-of-dynasets"></a><a name="_core_availability_of_dynasets"></a>Dynasets 的可用性

如果满足以下要求，MFC 数据库类支持动态集：

- ODBC 游标库 DLL 不得用于此数据源。

   如果使用游标库，它将屏蔽基础 ODBC 驱动程序的某些功能，这些功能对于动态设置支持是必需的。 如果要使用动态集（并且 ODBC 驱动程序具有动态集所需的功能（如本节其余部分所述），可能会导致 MFC 在创建`CDatabase`对象时不加载游标库。 有关详细信息，请参阅[ODBC](../../data/odbc/odbc-basics.md)和类`CDatabase`的[OpenEx](../../mfc/reference/cdatabase-class.md#openex)或[Open](../../mfc/reference/cdatabase-class.md#open)成员函数。

   在 ODBC 术语中，动态集和快照称为游标。 游标是用于跟踪其在记录集中的位置的机制。

- 数据源的 ODBC 驱动程序必须支持键集驱动的游标。

   Keyset 驱动的游标通过获取和存储一组密钥来管理表中的数据。 当用户滚动到特定记录时，这些键用于从表中获取当前数据。 要确定驱动程序是否提供此支持，请使用`::SQLGetInfo`*SQL_SCROLL_OPTIONS*参数调用 ODBC API 函数。

   如果尝试在没有密钥集支持的情况下打开动态集，则AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED获取具有返回代码`CDBException`值的 。

- 数据源的 ODBC 驱动程序必须支持扩展提取。

   扩展提取是向后滚动和向前滚动 SQL 查询的结果记录的能力。 要确定驱动程序是否支持此功能，请使用*SQL_API_SQLEXTENDEDFETCH*参数`::SQLGetFunctions`调用 ODBC API 函数。

如果需要可更新的动态集（或快照），ODBC 驱动程序还必须支持`::SQLSetPos`ODBC API 功能或定位更新。 该`::SQLSetPos`函数允许 MFC 在不发送 SQL 语句的情况下更新数据源。 如果此支持可用，MFC 会将其用于使用 SQL 进行更新。 要确定驱动程序是否支持`::SQLSetPos`，请`::SQLGetInfo`使用*SQL_POS_OPERATIONS*参数调用。

定位更新使用 SQL 语法\<（>）**标识**数据源表中的特定行。 要确定驱动程序是否支持定位更新，请使用`::SQLGetInfo`*SQL_POSITIONED_STATEMENTS*参数进行调用。

通常，MFC 动态集（但不只转发记录集）需要具有 2 级 API 一致性的 ODBC 驱动程序。 如果数据源的驱动程序符合 1 级 API 集，您仍可以使用可更新和只读快照和仅转发记录集，但不能使用动态集。 但是，如果级别 1 驱动程序支持扩展提取和键集驱动的游标，则可以支持动态集。 有关 ODBC 符合性级别的详细信息，请参阅[ODBC](../../data/odbc/odbc-basics.md)。

> [!NOTE]
> 如果要同时使用快照和动态集，则必须将它们基于两个不同的`CDatabase`对象（两个不同的连接）。

与使用 ODBC 游标库维护的中间存储的快照不同，动态集在滚动到数据源时直接从数据源获取记录。 这样，最初由动态集选择的记录与数据源保持同步。

有关此版本的 Visual C++ 中包含的 ODBC 驱动程序列表以及有关获取其他驱动程序的信息，请参阅 [ODBC 驱动程序列表](../../data/odbc/odbc-driver-list.md)。

## <a name="see-also"></a>另请参阅

[开放数据库连接 （ODBC）](../../data/odbc/open-database-connectivity-odbc.md)
