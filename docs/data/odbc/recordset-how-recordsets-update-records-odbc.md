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
ms.openlocfilehash: 03fb696c1fadd834962d37c8e75b5f8910af819e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366969"
---
# <a name="recordset-how-recordsets-update-records-odbc"></a>记录集：记录集如何更新记录 (ODBC)

本主题适用于 MFC ODBC 类。

除了从数据源中选择记录的能力外，记录集还可以（可选）更新或删除所选记录或添加新记录。 三个因素决定了记录集的可更新性：连接的数据源是否可更新、创建记录集对象时指定的选项以及创建的 SQL。

> [!NOTE]
> `CRecordset`对象基于的 SQL 可能会影响记录集的可更新性。 例如，如果您的 SQL 包含联接或 GROUP **BY**子句，MFC 会将可更新性设置为 FALSE。

> [!NOTE]
> 本主题适用于从 `CRecordset` 派生的对象，其中尚未实现批量提取行。 如果使用批量行提取，请参阅[记录集：批量提取记录 （ODBC）。](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

本主题介绍：

- [您在记录集更新中的角色](#_core_your_role_in_recordset_updating)以及框架为您做什么。

- [记录集作为编辑缓冲区](#_core_the_edit_buffer)以及[动态集和快照之间的差异](#_core_dynasets_and_snapshots)。

[记录集：如何](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)从记录集的角度描述这些函数的操作。"

[记录集：有关更新的详细信息 （ODBC）](../../data/odbc/recordset-more-about-updates-odbc.md)通过解释事务如何影响更新、关闭记录集或滚动如何影响正在进行的更新以及更新如何与其他用户的更新交互来完成记录集更新故事。

## <a name="your-role-in-recordset-updating"></a><a name="_core_your_role_in_recordset_updating"></a>您在记录集更新中的角色

下表显示了您在使用记录集添加、编辑或删除记录中的角色，以及框架为您执行的作用。

### <a name="recordset-updating-you-and-the-framework"></a>记录集更新：您和框架

|你|框架|
|---------|-------------------|
|确定数据源是可更新的（或可追加的）。|提供[CDatabase](../../mfc/reference/cdatabase-class.md)成员函数，用于测试数据源的可更新性或可追加性。|
|打开可上升的记录集（任何类型的）。||
|通过调用`CRecordset`更新函数（如`CanUpdate`或`CanAppend`）确定记录集是否可更新。||
|调用记录集成员函数以添加、编辑和删除记录。|管理记录集对象和数据源之间交换数据的机制。|
|或者，使用事务来控制更新过程。|提供`CDatabase`成员功能以支持事务。|

有关交易记录的详细信息，请参阅事务[（ODBC）](../../data/odbc/transaction-odbc.md)。

## <a name="the-edit-buffer"></a><a name="_core_the_edit_buffer"></a>编辑缓冲区

综合而言，记录集的字段数据成员用作包含一条记录 （当前记录）的编辑缓冲区。 更新操作使用此缓冲区对当前记录进行操作。

- 添加记录时，编辑缓冲区用于生成新记录。 完成添加记录后，以前当前的记录将再次变为当前。

- 更新（编辑）记录时，编辑缓冲区用于将记录集的字段数据成员设置为新值。 更新完成后，更新的记录仍然是最新的。

当您调用[AddNew](../../mfc/reference/crecordset-class.md#addnew)或[Edit](../../mfc/reference/crecordset-class.md#edit)时，将存储当前记录，以便以后可以根据需要还原该记录。 当您调用[Delete](../../mfc/reference/crecordset-class.md#delete)时，不会存储当前记录，但标记为已删除，您必须滚动到其他记录。

> [!NOTE]
> 编辑缓冲区在记录删除中不扮演任何角色。 删除当前记录时，记录将标记为已删除，并且记录集在滚动到其他记录之前"不在记录上"。

## <a name="dynasets-and-snapshots"></a><a name="_core_dynasets_and_snapshots"></a>动态集和快照

当您滚动到记录时，[动态集](../../data/odbc/dynaset.md)会刷新记录的内容。 [快照](../../data/odbc/snapshot.md)是记录的静态表示形式，因此除非调用[Requery](../../mfc/reference/crecordset-class.md#requery)，否则不会刷新记录的内容。 要使用动态集的所有功能，您必须使用符合正确级别的 ODBC API 支持的 ODBC 驱动程序。 有关详细信息，请参阅[ODBC](../../data/odbc/odbc-basics.md)和[Dynaset](../../data/odbc/dynaset.md)。

## <a name="see-also"></a>另请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[记录集：AddNew、Edit 和 Delete 的工作方式 (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)
