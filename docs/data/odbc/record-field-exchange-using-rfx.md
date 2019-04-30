---
title: 记录字段交换：使用 RFX
ms.date: 11/04/2016
helpviewer_keywords:
- RFX (ODBC), implementing
ms.assetid: ada8f043-37e6-4d41-9db3-92c997a61957
ms.openlocfilehash: 2a029f653753363e08b3c4f8b9fceab6295924af
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395646"
---
# <a name="record-field-exchange-using-rfx"></a>记录字段交换：使用 RFX

本主题介绍您如何使用 RFX 相对于框架的用途。

> [!NOTE]
>  本主题适用于类派生自[CRecordset](../../mfc/reference/crecordset-class.md)中的批量行提取尚未实现。 如果使用批量行提取，实现批量记录字段交换 (Bulk RFX)。 批量 RFX 是类似于 RFX。 若要了解的差异，请参阅[记录集：(ODBC) 批量提取记录](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

以下主题包含相关的信息：

- [记录字段交换：使用向导代码](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md)引入了 RFX 的主要组件，并说明代码的 MFC 应用程序向导并**添加类**(如中所述[添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) 写入若要支持 RFX 和如何你可能想要修改向导代码。

- [记录字段交换：使用 RFX 函数](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)介绍了中的 RFX 函数编写调用你`DoFieldExchange`重写。

下表显示了你的角色相对于框架为您的用途。

### <a name="using-rfx-you-and-the-framework"></a>使用 RFX:你和框架

|你|框架|
|---------|-------------------|
|声明记录集类具有一个向导。 指定的字段数据成员的名称和数据类型。|该向导派生`CRecordset`类并将事件写入[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)为你重写，其中包括 RFX 函数的每个字段数据成员的调用。|
|（可选）手动将任何所需的参数数据成员添加到类。 手动添加到的 RFX 函数调用`DoFieldExchange`对于每个参数的数据成员，请添加对的调用[CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)组的参数，并指定中的参数的总数[m_nParams](../../mfc/reference/crecordset-class.md#m_nparams). 请参阅[记录集：参数化记录集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。||
|（可选）手动将其他列绑定到的字段数据成员。 手动递增[m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)。 请参阅[记录集：动态绑定数据列 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。||
|构造记录集类的对象。 在之前使用的对象，设置其参数的值数据成员，如果有的话。|为提高效率，框架预绑定参数，使用 ODBC。 当传递参数值时，框架会将它们传递到数据源。 只有参数值都发送用于再次查询，除非已更改的排序和/或筛选器字符串。|
|打开记录集对象使用[crecordset:: Open](../../mfc/reference/crecordset-class.md#open)。|执行记录集的查询时，将列绑定到字段数据成员的记录集，并调用`DoFieldExchange`交换的第一个所选的记录和记录集的字段数据成员之间的数据。|
|在记录集使用滚动[CRecordset::Move](../../mfc/reference/crecordset-class.md#move)或菜单或工具栏命令。|调用`DoFieldExchange`将从新的当前记录数据传输到的字段数据成员。|
|添加、 更新和删除记录。|调用`DoFieldExchange`将数据传输到数据源。|

## <a name="see-also"></a>请参阅

[记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[记录字段交换：RFX 工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[记录集：获取 SUM 及其他聚合结果 (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[CRecordset 类](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange 类](../../mfc/reference/cfieldexchange-class.md)<br/>
[宏、 全局函数和全局变量](../../mfc/reference/mfc-macros-and-globals.md)

