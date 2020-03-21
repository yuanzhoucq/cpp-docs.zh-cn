---
title: 记录字段交换：使用 RFX
ms.date: 11/04/2016
helpviewer_keywords:
- RFX (ODBC), implementing
ms.assetid: ada8f043-37e6-4d41-9db3-92c997a61957
ms.openlocfilehash: 70197d2a9130388e86bb94f0d670360bb35febeb
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075867"
---
# <a name="record-field-exchange-using-rfx"></a>记录字段交换：使用 RFX

本主题介绍了在与框架的作用相关时，要执行的操作。

> [!NOTE]
>  本主题适用于从[CRecordset](../../mfc/reference/crecordset-class.md)派生的类，其中尚未实现批量提取行。 如果使用批量提取行，则将实现批量记录字段交换（批量 RFX）。 批量 RFX 与 RFX 类似。 若要了解不同之处，请参阅[记录集：批量提取记录（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

以下主题包含相关信息：

- [记录字段交换：使用向导代码](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md)会引入 RFX 的主要组件，并说明 MFC 应用程序向导和**添加类**（如[添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)编写以支持 RFX）和如何修改向导代码中所述的代码。

- [记录字段交换：使用 RFX 函数](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)说明在 `DoFieldExchange` 重写中对 RFX 函数的编写调用。

下表显示了与框架的作用有关的角色。

### <a name="using-rfx-you-and-the-framework"></a>使用 RFX：您和框架

|你|框架|
|---------|-------------------|
|使用向导声明记录集类。 指定字段数据成员的名称和数据类型。|向导将派生一个 `CRecordset` 类并为您编写[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)替代，包括每个字段数据成员的 RFX 函数调用。|
|可有可无手动将任何所需的参数数据成员添加到类。 为每个参数数据成员手动添加一个 RFX 函数调用 `DoFieldExchange`，为参数组添加对[CFieldExchange：： SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)的调用，并指定[m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)中的参数总数。 请参阅[记录集：参数化记录集（ODBC）](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。||
|可有可无手动将其他列绑定到字段数据成员。 手动递增[m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)。 请参阅[记录集：动态绑定数据列（ODBC）](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。||
|构造记录集类的对象。 使用对象之前，请设置其参数数据成员的值（如果有）。|为提高效率，框架使用 ODBC prebinds 了参数。 传递参数值时，框架会将参数值传递给数据源。 除非排序和/或筛选器字符串已更改，否则仅发送用于查询的参数值。|
|使用[CRecordset：： open](../../mfc/reference/crecordset-class.md#open)打开记录集对象。|执行记录集的查询，将列绑定到记录集的字段数据成员，并调用 `DoFieldExchange` 在第一个选定记录和记录集的字段数据成员之间交换数据。|
|使用[CRecordset：： Move](../../mfc/reference/crecordset-class.md#move)或菜单或工具栏命令在记录集中滚动。|调用 `DoFieldExchange` 将数据从新的当前记录传输到字段数据成员。|
|添加、更新和删除记录。|调用 `DoFieldExchange` 将数据传输到数据源。|

## <a name="see-also"></a>另请参阅

[记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[记录字段交换：RFX 的工作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[记录集：获取 SUM 及其他聚合结果 (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[CRecordset 类](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange 类](../../mfc/reference/cfieldexchange-class.md)<br/>
[宏、全局函数和全局变量](../../mfc/reference/mfc-macros-and-globals.md)
