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
ms.openlocfilehash: 7edc1c04da617f96165b25a47ce169b266ae0003
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59024590"
---
# <a name="recordset-requerying-a-recordset-odbc"></a>记录集：再次查询记录集 (ODBC)

本主题适用于 MFC ODBC 类。

本主题说明如何使用记录集对象的类型重新查询 （即，刷新） 本身从数据库和你可能想要执行此操作与[再次查询](../../mfc/reference/crecordset-class.md#requery)成员函数。

再次查询记录集的主要原因是：

- 将最新记录由你或其他用户添加和删除其他用户 （你删除那些已反映在记录集） 的记录方面的记录集。

- 刷新记录集根据不断变化的参数值。

##  <a name="_core_bringing_the_recordset_up_to_date"></a> 记录集最多引入日期

通常情况下，你将想要再次查询记录集对象以使其保持最新。 在多用户数据库环境中，其他用户可以进行更改的数据的记录集的生命周期内。 有关记录集时反映由其他用户所做的更改和其他用户的记录集时反映所做的更改的详细信息，请参阅[记录集：如何记录集更新记录 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)并[动态集](../../data/odbc/dynaset.md)。

##  <a name="_core_requerying_based_on_new_parameters"></a> 再次查询基于新的参数

另一个常用 — 也是同等重要 — 利用[再次查询](../../mfc/reference/crecordset-class.md#requery)是选择一组新的基于不断变化的参数值的记录。

> [!TIP]
>  查询速度可能明显更快，如果您调用`Requery`更改于直接调用的参数值`Open`试。

##  <a name="_core_requerying_dynasets_vs.._snapshots"></a> 再次查询动态集 vs。快照

因为动态集旨在使用最新的动态数据提供一组记录，你想要重新查询动态集，通常，如果你想要反映其他用户的新增功能。 快照，但是，非常有用，因为可以安全地依赖于其静态内容，而准备报表、 计算总计，依次类推。 尽管如此，您有时可能想要再次查询以及快照。 在多用户环境中，快照数据可能会丢失与数据源同步，因为其他用户更改的数据库。

#### <a name="to-requery-a-recordset-object"></a>若要再次查询记录集对象

1. 调用[再次查询](../../mfc/reference/crecordset-class.md#requery)对象的成员函数。

或者，可以关闭并重新打开原始记录集。 在任一情况下，新的记录集表示数据源的当前状态。

有关示例，请参阅[记录视图：从另一个记录集填充列表框](../../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md)所述。

> [!TIP]
>  若要优化`Requery`性能，避免更改记录集的[筛选器](../../data/odbc/recordset-filtering-records-odbc.md)或[排序](../../data/odbc/recordset-sorting-records-odbc.md)。 更改仅参数值，然后才能调用`Requery`。

如果`Requery`调用失败，您可以重试调用; 否则，你的应用程序应正常终止。 调用`Requery`或`Open`任意多种原因可能会失败。 可能会发生网络错误;或者，在调用期间发布的现有数据之后，但之前获得新的数据，另一个用户可能会获取独占访问权限;或者可能删除记录集所依赖的表。

## <a name="see-also"></a>请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[记录集：动态绑定数据列 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[记录集：创建和关闭记录集 (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)