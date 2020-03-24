---
title: 记录集：记录集如何更新记录 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- records, updating
- ODBC recordsets, updating
- recordsets, editing records
- updating recordsets
- recordsets, updating
ms.assetid: 5ceecc06-7a86-43b1-93db-a54fb1e717c7
ms.openlocfilehash: 578b3b39d90b3beb80dbd201d4982fee30dc6bce
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212870"
---
# <a name="recordset-how-recordsets-update-records-odbc"></a>记录集：记录集如何更新记录 (ODBC)

本主题适用于 MFC ODBC 类。

除了能够从数据源中选择记录外，记录集还可以（可选）更新或删除所选记录或添加新记录。 以下三个因素决定了记录集的可更新性：连接数据源是否可更新、创建记录集对象时指定的选项以及创建的 SQL。

> [!NOTE]
>  `CRecordset` 对象所基于的 SQL 可能会影响记录集的可更新性。 例如，如果 SQL 包含 join 或**GROUP by**子句，则 MFC 会将更新设置为 FALSE。

> [!NOTE]
>  本主题适用于从 `CRecordset` 派生的对象，其中尚未实现批量提取行。 如果使用批量取行，请参阅[记录集：批量提取记录（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

本主题介绍：

- [你在记录集更新中的角色](#_core_your_role_in_recordset_updating)以及框架为你提供的功能。

- [作为编辑缓冲区的记录集](#_core_the_edit_buffer)，以及[动态集和快照之间的差异](#_core_dynasets_and_snapshots)。

[记录集： AddNew、Edit 和 Delete 的工作方式（ODBC）](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)说明了这些函数在记录集的位置的操作。

[记录集：有关更新的详细信息（ODBC）](../../data/odbc/recordset-more-about-updates-odbc.md)通过说明事务如何影响更新、关闭记录集或滚动影响正在进行的更新以及更新如何与其他用户的更新进行交互，来完成记录集更新。

##  <a name="your-role-in-recordset-updating"></a><a name="_core_your_role_in_recordset_updating"></a>你在记录集更新中的角色

下表显示了使用记录集来添加、编辑或删除记录的角色，以及框架为你执行的操作。

### <a name="recordset-updating-you-and-the-framework"></a>记录集更新：您和框架

|你|框架|
|---------|-------------------|
|确定数据源是否可更新（或可追加）。|提供[CDatabase](../../mfc/reference/cdatabase-class.md)成员函数，用于测试数据源的更新或 appendability。|
|打开可更新的记录集（类型为）。||
|通过调用 `CanUpdate` 或 `CanAppend`等 `CRecordset` 更新函数来确定是否可更新记录集。||
|调用记录集成员函数来添加、编辑和删除记录。|管理记录集对象和数据源之间交换数据的机制。|
|（可选）使用事务来控制更新过程。|提供 `CDatabase` 成员函数以支持事务。|

有关事务的详细信息，请参阅[Transaction （ODBC）](../../data/odbc/transaction-odbc.md)。

##  <a name="the-edit-buffer"></a><a name="_core_the_edit_buffer"></a>编辑缓冲区

记录集的字段数据成员统称为包含一条记录的编辑缓冲区（当前记录）。 更新操作使用此缓冲区对当前记录进行操作。

- 添加记录时，编辑缓冲区用于生成新记录。 完成记录添加后，以前的当前记录将再次变为当前记录。

- 更新（编辑）记录时，编辑缓冲区用于将记录集的字段数据成员设置为新值。 完成更新后，更新的记录仍是最新的。

调用[AddNew](../../mfc/reference/crecordset-class.md#addnew)或[Edit](../../mfc/reference/crecordset-class.md#edit)时，将存储当前记录，以便以后可以根据需要进行还原。 调用[Delete](../../mfc/reference/crecordset-class.md#delete)时，不会存储当前记录，但会将其标记为已删除，并且必须滚动到其他记录。

> [!NOTE]
>  编辑缓冲区在记录删除中不起作用。 当您删除当前记录时，记录将标记为已删除，并且在您滚动到其他记录之前，记录集将 "不在记录上"。

##  <a name="dynasets-and-snapshots"></a><a name="_core_dynasets_and_snapshots"></a>动态集和快照

滚动到记录时，[动态集](../../data/odbc/dynaset.md)会刷新记录的内容。 [快照](../../data/odbc/snapshot.md)是记录的静态表示形式，因此除非调用[Requery](../../mfc/reference/crecordset-class.md#requery)，否则不会刷新记录的内容。 若要使用动态集的所有功能，必须使用符合 ODBC API 支持的正确级别的 ODBC 驱动程序。 有关详细信息，请参阅[ODBC](../../data/odbc/odbc-basics.md)和[动态集](../../data/odbc/dynaset.md)。

## <a name="see-also"></a>另请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[记录集：AddNew、Edit 和 Delete 的工作方式 (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)
