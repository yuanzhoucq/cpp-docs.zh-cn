---
title: 记录字段交换：使用 RFX
ms.date: 11/04/2016
helpviewer_keywords:
- RFX (ODBC), implementing
ms.assetid: ada8f043-37e6-4d41-9db3-92c997a61957
ms.openlocfilehash: dc0cdcee758f4842b0738068a8a11c4e2e404155
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367149"
---
# <a name="record-field-exchange-using-rfx"></a>记录字段交换：使用 RFX

本主题介绍您如何处理使用 RFX 与框架的作用。

> [!NOTE]
> 本主题适用于从[CRecordset](../../mfc/reference/crecordset-class.md)派生的类，其中尚未实现批量行提取。 如果使用批量提取行，则将实现批量记录字段交换（批量 RFX）。 批量 RFX 与 RFX 类似。 要了解差异，请参阅[记录集：批量提取记录 （ODBC）。](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

以下主题包含相关信息：

- [记录字段交换：使用向导代码](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md)引入了 RFX 的主要组件，并解释了 MFC 应用程序向导和**添加类**（如[添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)中所述）为支持 RFX 而编写的代码，以及如何修改向导代码。

- [记录字段交换：使用 RFX 函数](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)可以解释在重写中写入对 RFX 函数的`DoFieldExchange`调用。

下表显示了您相对于框架为您做什么的角色。

### <a name="using-rfx-you-and-the-framework"></a>使用 RFX：您和框架

|你|框架|
|---------|-------------------|
|使用向导声明记录集类。 指定字段数据成员的名称和数据类型。|向导派生一个`CRecordset`类，并为您编写[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)重写，包括针对每个字段数据成员的 RFX 函数调用。|
|（可选）手动将任何所需的参数数据成员添加到类中。 手动`DoFieldExchange`为每个参数数据成员添加 RFX 函数调用，向[CFieldExchange：：SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)添加参数组调用，并在[m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)中指定参数的总数。 请参阅[记录集：参数化记录集 （ODBC）。](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)||
|（可选）手动将其他列绑定到字段数据成员。 手动增加[m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)。 请参阅[记录集：动态绑定数据列 （ODBC）。](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)||
|构造记录集类的对象。 在使用 对象之前，设置其参数数据成员的值（如果有）。|为了提高效率，框架使用 ODBC 预绑定参数。 传递参数值时，框架会将它们传递给数据源。 除非排序和/或筛选器字符串已更改，否则仅发送参数值进行重新查询。|
|使用[CRecordset：：打开](../../mfc/reference/crecordset-class.md#open)记录集对象。|执行记录集的查询，将列绑定到记录集的字段数据成员，并调用`DoFieldExchange`在第一个选定的记录和记录集的字段数据成员之间交换数据。|
|使用[CRecordset：move](../../mfc/reference/crecordset-class.md#move)或菜单或工具栏命令在记录集中滚动。|调用`DoFieldExchange`将数据从新的当前记录传输到字段数据成员。|
|添加、更新和删除记录。|将数据`DoFieldExchange`传输到数据源的调用。|

## <a name="see-also"></a>另请参阅

[记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[记录字段交换：RFX 的工作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[记录集：获取 SUM 及其他聚合结果 (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[CRecordset 类](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange 课程](../../mfc/reference/cfieldexchange-class.md)<br/>
[宏、全局函数和全局变量](../../mfc/reference/mfc-macros-and-globals.md)
