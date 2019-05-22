---
title: 记录集 (ODBC)
ms.date: 05/09/2019
helpviewer_keywords:
- recordsets, snapshots
- recordsets, creating
- dynamic recordsets
- forward-only recordsets
- recordsets, dynasets
- ODBC recordsets, CRecordset objects
- ODBC recordsets
- recordsets, about recordsets
- snapshots, ODBC recordsets
- dynasets
ms.assetid: 333337c5-575e-4d26-b5f6-47166ad7874d
ms.openlocfilehash: b043b08e13611b87bbffbe9dfb3255d5520e3359
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707835"
---
# <a name="recordset-odbc"></a>记录集 (ODBC)

本主题适用于 MFC ODBC 类。

[CRecordset](../../mfc/reference/crecordset-class.md) 对象表示从数据源中选择的一组记录。 记录可以来自：

- 表。

- 查询。

- 访问一个或多个表的存储过程。

一个基于表的记录集示例是“所有客户”，它可以访问“客户”表。 一个查询的示例是“Joe Smith 的所有发票”。 一个基于存储过程（有时称为预定义查询）的记录集示例是“所有逾期帐户”，它将调用后端数据库中的存储过程。 记录集可以联接来自同一数据源的两个或多个表，但不能联接来自不同数据源的表。

> [!NOTE]
>  某些 ODBC 驱动程序支持数据库的视图。 这种意义上的视图是最初使用 SQL `CREATE VIEW` 语句创建的查询。

##  <a name="_core_recordset_capabilities"></a> 记录集功能

所有记录集对象共享以下功能：

- 如果数据源不是只读的，则可以指定你的记录集为[可更新的](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)、[可附加的](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)还是只读的。 如果记录集是可更新的，则可以选择保守或乐观[锁定](../../data/odbc/recordset-locking-records-odbc.md)方法，前提是驱动程序提供适当的锁定支持。 如果数据源是只读的，记录集将为只读的。

- 可以调用成员函数来[滚动](../../data/odbc/recordset-scrolling-odbc.md)浏览所选的记录。

- 可以[筛选](../../data/odbc/recordset-filtering-records-odbc.md)记录以限制从可用记录中选择哪些记录。

- 可以根据一个或多个列按升序或降序对记录进行[排序](../../data/odbc/recordset-sorting-records-odbc.md)。

- 可以[参数化](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)记录集以在运行时限定记录集选择。

##  <a name="_core_snapshots_and_dynasets"></a> 快照和动态集

记录集有两种主体类型：[快照](../../data/odbc/snapshot.md)和[动态集](../../data/odbc/dynaset.md)。 两者都受到 `CRecordset` 类的支持。 尽管每种类型共享所有记录集的共同特征，但每种类型也以其自身的专用方式扩展了常用功能。 快照提供数据的静态视图，对于报告和其他需要查看特定时间的数据视图的情况非常有用。 当你想使其他用户所进行的更新在记录集中可见而无需再次查询或刷新记录集时，动态集则非常有用。 快照和动态集可以是可更新的或只读的。 若要反映其他用户添加或删除的记录，请调用 [CRecordset::Requery](../../mfc/reference/crecordset-class.md#requery)。

`CRecordset` 还支持两种其他类型的记录集：动态记录集和只进记录集。 动态记录集类似于动态集；但是，动态记录集反映了在不调用 `CRecordset::Requery` 的情况下添加或删除的任何记录。 出于此原因，通常在 DBMS 上的处理动态记录集非常耗时，并且许多 ODBC 驱动程序不支持它们。 相比之下，只进记录集为不需要更新或向后滚动的记录集提供了最有效的数据访问方法。 例如，你可以使用只进记录集将数据从一个数据源迁移到另一个数据源，在此过程中你只需向前移动数据即可。 若要使用只进记录集，必须执行以下两项操作：

- 将选项 `CRecordset::forwardOnly` 作为 [Open](../../mfc/reference/crecordset-class.md#open) 成员函数的“nOpenType”参数传递。

- 在 `Open` 的“dwOptions”参数中指定 `CRecordset::readOnly`。

    > [!NOTE]
    >  有关动态集支持的 ODBC 驱动程序要求的信息，请参阅 [ODBC](../../data/odbc/odbc-basics.md)。 有关此版本的 Visual C++ 中包含的 ODBC 驱动程序列表以及有关获取其他驱动程序的信息，请参阅 [ODBC 驱动程序列表](../../data/odbc/odbc-driver-list.md)。

##  <a name="_core_your_recordsets"></a> 记录集

对于要访问的每个不同的表、视图或存储过程，通常需要定义派生自 `CRecordset` 的类。 （数据库联接是一个例外情况，其中一个记录集表示来自两个或多个表的列。）在派生记录集类时，启用记录字段交换 (RFX) 机制或批量记录字段交换（批量 RFX）机制，这类似于对话框数据交换 (DDX) 机制。 RFX 和批量 RFX 简化了从数据源到记录集的数据传输；RFX 还将数据从记录集传输到数据源。 有关详细信息，请参阅[记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md) 和[记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

记录集对象使你可以访问所有选定的记录。 使用 `CRecordset` 成员函数（例如 `MoveNext` 和 `MovePrev`）滚动浏览多个选定的记录。 同时，记录集对象仅表示所选记录中的一条，即当前记录。 可以通过声明与表的列或与数据库查询记录的列对应的记录集类成员变量来检查当前记录的字段。 有关记录集数据成员的信息，请参阅[记录集：体系结构 (ODBC)](../../data/odbc/recordset-architecture-odbc.md)。

以下主题说明了使用记录集对象的详细信息。 主题是按功能类别和自然浏览顺序列出的，以便按顺序阅读。

### <a name="topics-about-the-mechanics-of-opening-reading-and-closing-recordsets"></a>关于打开、阅读和关闭记录集的机制的主题

- [记录集：体系结构 (ODBC)](../../data/odbc/recordset-architecture-odbc.md)

- [记录集：声明表的类 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)

- [记录集：创建和关闭记录集 (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)

- [记录集：滚动 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)

- [记录集：书签和绝对位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)

- [记录集：筛选记录 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)

- [记录集：排序记录 (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)

- [记录集：参数化记录集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)

### <a name="topics-about-the-mechanics-of-modifying-recordsets"></a>关于修改记录集的机制的主题

- [记录集：添加、更新和删除记录 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)

- [记录集：锁定记录 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)

- [记录集：重新查询记录集 (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)

### <a name="topics-about-somewhat-more-advanced-techniques"></a>关于某种程度上更高级技术的主题

- [记录集：执行联接 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)

- [记录集：声明预定义查询的类 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)

- [记录集：动态绑定数据列 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)

- [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

- [记录集：处理大数据项 (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)

- [记录集：获取 SUM 及其他聚合结果 (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)

### <a name="topics-about-how-recordsets-work"></a>有关记录集工作原理的主题

- [记录集：记录集如何选择记录 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)

- [记录集：记录集如何更新记录 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)

## <a name="see-also"></a>请参阅

[开放式数据库连接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[MFC ODBC 使用](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[事务 (ODBC)](../../data/odbc/transaction-odbc.md)