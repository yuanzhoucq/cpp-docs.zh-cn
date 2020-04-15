---
title: 记录集：再次查询记录集 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- recordsets, requerying
- requerying recordsets
- Requery method
- ODBC recordsets, requerying
- refreshing recordsets
ms.assetid: 4ebc3b5b-5b91-4f51-a967-245223c6b8e1
ms.openlocfilehash: cdae28f81eebe8427bc829072e0d9a83c6ec1722
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366949"
---
# <a name="recordset-requerying-a-recordset-odbc"></a>记录集：再次查询记录集 (ODBC)

本主题适用于 MFC ODBC 类。

本主题介绍如何使用记录集对象从数据库中重新查询（即刷新）自身，以及何时使用[Requery](../../mfc/reference/crecordset-class.md#requery)成员函数执行此操作。

重新查询记录集的主要原因是：

- 将记录设置与您或其他用户添加的记录以及其他用户删除的记录（您删除的记录已反映在记录集中）保持最新状态。

- 根据更改的参数值刷新记录集。

## <a name="bringing-the-recordset-up-to-date"></a><a name="_core_bringing_the_recordset_up_to_date"></a>使记录设置保持最新

通常，您需要重新查询记录集对象，使其保持最新状态。 在多用户数据库环境中，其他用户可以在记录集的生命周期内对数据进行更改。 有关记录集何时反映其他用户所做的更改以及其他用户的记录集反映您的更改的详细信息，请参阅[记录集：记录集如何更新记录 （ODBC）](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)和[动态集](../../data/odbc/dynaset.md)。

## <a name="requerying-based-on-new-parameters"></a><a name="_core_requerying_based_on_new_parameters"></a>基于新参数重新查询

[重新查询](../../mfc/reference/crecordset-class.md#requery)的另一个频繁且同样重要的用途是根据更改的参数值选择一组新的记录。

> [!TIP]
> 如果使用更改参数值进行调用，则查询`Requery`速度可能比再次调用`Open`时快得多。

## <a name="requerying-dynasets-vs-snapshots"></a><a name="_core_requerying_dynasets_vs.._snapshots"></a>重新查询动态集与快照

由于动态集旨在显示一组具有动态最新数据的记录，因此如果要反映其他用户的添加内容，则经常要重新查询动态集。 另一方面，快照很有用，因为您可以在准备报表、计算总计等时安全地依赖其静态内容。 不过，有时您可能还需要重新查询快照。 在多用户环境中，当其他用户更改数据库时，快照数据可能会失去与数据源的同步。

#### <a name="to-requery-a-recordset-object"></a>重新查询记录集对象

1. 调用对象的[重新查询](../../mfc/reference/crecordset-class.md#requery)成员函数。

或者，您可以关闭并重新打开原始记录集。 在这两种情况下，新记录集表示数据源的当前状态。

例如，请参阅[记录视图：从第二个记录集填充列表框](../../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md)。

> [!TIP]
> 要优化`Requery`性能，请避免更改记录集的[筛选器](../../data/odbc/recordset-filtering-records-odbc.md)或[排序](../../data/odbc/recordset-sorting-records-odbc.md)。 在调用`Requery`之前仅更改参数值。

如果`Requery`呼叫失败，您可以重试呼叫;如果呼叫失败，则可以重试呼叫。否则，您的应用程序应正常终止。 由于多种原因`Requery`，`Open`调用或可能失败。 可能发生网络错误;或，在通话过程中，在现有数据发布后，但在获取新数据之前，其他用户可能会获得独占访问权限;或可以删除记录集所依赖的表。

## <a name="see-also"></a>另请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[记录集：动态绑定数据列 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[记录集：创建和关闭记录集 (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)
