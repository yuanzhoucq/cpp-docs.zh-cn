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
ms.openlocfilehash: b7cf40ca3b0c8e415368772063aee61008a52764
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212779"
---
# <a name="recordset-requerying-a-recordset-odbc"></a>记录集：再次查询记录集 (ODBC)

本主题适用于 MFC ODBC 类。

本主题说明如何使用 recordset 对象从数据库中再次查询（即，刷新）自身，以及何时需要使用[requery](../../mfc/reference/crecordset-class.md#requery)成员函数执行此操作。

重新查询记录集的主要原因是：

- 使您或其他用户添加的记录与其他用户（删除的那些记录）中的记录与其他用户所删除的记录保持最新。

- 基于更改参数值刷新记录集。

##  <a name="bringing-the-recordset-up-to-date"></a><a name="_core_bringing_the_recordset_up_to_date"></a>使记录集保持最新

通常，您将需要再次查询记录集对象，使其保持最新状态。 在多用户数据库环境中，其他用户可以在记录集的生存期内对数据进行更改。 有关记录集何时反映其他用户所做的更改以及其他用户的记录集是否反映你所做的更改的详细信息，请参阅[记录集：记录集如何更新记录（ODBC）](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)和[动态集](../../data/odbc/dynaset.md)。

##  <a name="requerying-based-on-new-parameters"></a><a name="_core_requerying_based_on_new_parameters"></a>基于新参数的重新查询

另一种常见的情况是，也同样重要的是，使用[Requery](../../mfc/reference/crecordset-class.md#requery)是根据变化的参数值选择一组新的记录。

> [!TIP]
>  如果调用 `Requery` 与更改参数值（而不是再次调用 `Open`），查询速度可能会快得多。

##  <a name="requerying-dynasets-vs-snapshots"></a><a name="_core_requerying_dynasets_vs.._snapshots"></a>重新查询动态集与快照

由于动态集的目的是提供一组包含动态最新数据的记录，因此，如果想要反映其他用户的新增内容，则需要经常再次查询动态集。 另一方面，快照非常有用，因为您可以在准备报表、计算总计等时安全地依赖其静态内容。 尽管如此，有时也可能需要再次查询快照。 在多用户环境中，快照数据可能会与数据源失去同步，因为其他用户更改了数据库。

#### <a name="to-requery-a-recordset-object"></a>重新查询记录集对象

1. 调用对象的[Requery](../../mfc/reference/crecordset-class.md#requery)成员函数。

或者，您可以关闭并重新打开原始记录集。 在任一情况下，新记录集都表示数据源的当前状态。

有关示例，请参阅[记录视图：从另一个记录集填充列表框](../../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md)。

> [!TIP]
>  若要优化 `Requery` 性能，请避免更改记录集的[筛选器](../../data/odbc/recordset-filtering-records-odbc.md)或[排序](../../data/odbc/recordset-sorting-records-odbc.md)。 在调用 `Requery`之前，只更改参数值。

如果 `Requery` 调用失败，你可以重试调用;否则，应用程序应正确终止。 对 `Requery` 或 `Open` 的调用可能因多种原因而失败。 可能出现网络错误;或者，在调用期间，在已发布现有数据之后但在获取新数据之前，其他用户可能会获取独占访问权限;或者可以删除记录集所依赖的表。

## <a name="see-also"></a>另请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[记录集：动态绑定数据列 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[记录集：创建和关闭记录集 (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)
