---
title: 记录集：如何记录集更新记录 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- records, updating
- ODBC recordsets, updating
- recordsets, editing records
- updating recordsets
- recordsets, updating
ms.assetid: 5ceecc06-7a86-43b1-93db-a54fb1e717c7
ms.openlocfilehash: bf71f562714e2dacfe75540e1e532219b3eb307f
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59034477"
---
# <a name="recordset-how-recordsets-update-records-odbc"></a>记录集：如何记录集更新记录 (ODBC)

本主题适用于 MFC ODBC 类。

除了能够从数据源选择记录，记录集还可以 （可选） 更新或删除所选的记录或添加新记录。 三个因素确定记录集的可更新性： 是否已连接的数据源是可更新、 创建记录集对象，并创建 SQL 时指定的选项。

> [!NOTE]
>  在其上的 SQL 你`CRecordset`基于对象可能会影响记录集的可更新性。 例如，如果 SQL 包含联接或**GROUP BY**子句，则 MFC 会将可更新性设置为 FALSE。

> [!NOTE]
>  本主题适用于对象派生自`CRecordset`中的批量行提取尚未实现。 如果使用批量行提取，请参阅[记录集：(ODBC) 批量提取记录](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

本主题说明：

- [在记录集更新中的角色](#_core_your_role_in_recordset_updating)和框架为您的用途。

- [记录集持久化为未编辑的缓冲区](#_core_the_edit_buffer)并[动态集与快照之间的差异](#_core_dynasets_and_snapshots)。

[记录集：如何 AddNew、 Edit 和删除工作 (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)介绍的这些函数的记录集的角度的操作。

[记录集：更多有关更新 (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md)完成记录集更新情景说明事务如何影响更新，如何关闭记录集或滚动更新正在运行，以及更新如何与其他用户的更新进行交互。

##  <a name="_core_your_role_in_recordset_updating"></a> 在记录集更新中的角色

下表中使用记录集来添加、 编辑或删除记录，以及该框架为您显示您的角色。

### <a name="recordset-updating-you-and-the-framework"></a>更新记录集：你和框架

|你|框架|
|---------|-------------------|
|确定数据源是可更新 （或可追加）。|提供，数量[CDatabase](../../mfc/reference/cdatabase-class.md)成员函数进行测试数据源的可更新性或 appendability。|
|打开一个可更新的记录集 （的任何类型）。||
|确定记录集是否可以更新通过调用`CRecordset`更新函数，例如`CanUpdate`或`CanAppend`。||
|调用记录集成员函数来添加、 编辑和删除记录。|管理记录集对象和数据源之间交换数据的机制。|
|（可选） 使用事务来控制更新过程。|提供`CDatabase`成员函数来支持事务。|

有关事务的详细信息，请参阅[事务 (ODBC)](../../data/odbc/transaction-odbc.md)。

##  <a name="_core_the_edit_buffer"></a> 编辑缓冲区

共同，记录集的字段数据成员作为包含一条记录的编辑缓冲区 — 当前记录。 更新操作使用此缓冲区来操作的当前记录。

- 当您添加一条记录时，编辑缓冲区用于生成新的记录。 完成添加记录后，先前的当前记录将再次成为当前。

- 在更新时使用 （编辑） 的记录，编辑缓冲区将记录集的字段数据成员设置为新值。 完成更新后，已更新的记录仍是最新。

当您调用[AddNew](../../mfc/reference/crecordset-class.md#addnew)或[编辑](../../mfc/reference/crecordset-class.md#edit)，以便可以稍后根据需要还原存储的当前记录。 当您调用[删除](../../mfc/reference/crecordset-class.md#delete)、 当前记录不会存储，但标记为已删除，必须滚动到另一条记录。

> [!NOTE]
>  编辑缓冲区中记录删除操作不起任何作用。 删除当前记录时，该记录被标记为已删除，并滚动到另一条记录之前，记录集是"不在上一条记录"。

##  <a name="_core_dynasets_and_snapshots"></a> 动态集与快照

[动态集](../../data/odbc/dynaset.md)刷新记录的内容，如滚动到的记录。 [快照](../../data/odbc/snapshot.md)是静态表示形式的记录，因此除非调用，否则不会刷新记录的内容[再次查询](../../mfc/reference/crecordset-class.md#requery)。 若要使用的动态集的所有功能，必须使用 ODBC 驱动程序符合 ODBC API 支持的正确级别的工作。 有关详细信息，请参阅[ODBC](../../data/odbc/odbc-basics.md)并[动态集](../../data/odbc/dynaset.md)。

## <a name="see-also"></a>请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[记录集：如何 AddNew，编辑和删除工作 (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)