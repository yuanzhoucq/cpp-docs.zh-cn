---
title: 记录字段交换：使用 RFX 函数
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC [C++], data types
- data types [C++], ODBC record field exchange
- RFX (ODBC) [C++], function syntax and parameters
- DoFieldExchange method, and RFX functions
- ODBC [C++], RFX
- RFX (ODBC) [C++], data types
- function calls, RFX functions
ms.assetid: c594300b-5a29-4119-a68b-e7ca32def696
ms.openlocfilehash: dc717336a5279e7eda1b7c39b19a7c76f9055cd3
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59035979"
---
# <a name="record-field-exchange-using-the-rfx-functions"></a>记录字段交换：使用 RFX 函数

本主题说明如何使用 RFX 函数调用的正文构成您`DoFieldExchange`重写。

> [!NOTE]
>  本主题适用于类派生自[CRecordset](../../mfc/reference/crecordset-class.md)中的批量行提取尚未实现。 如果使用批量行提取，实现批量记录字段交换 (Bulk RFX)。 批量 RFX 是类似于 RFX。 若要了解的差异，请参阅[记录集：(ODBC) 批量提取记录](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

RFX 全局函数之间交换数据集中的记录的数据源和字段数据成员上的列。 你编写记录集的调用 RFX 函数[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)成员函数。 本主题简要介绍的函数，并显示对其使用 RFX 函数都是可用的数据类型。 [技术说明 43](../../mfc/tn043-rfx-routines.md)介绍如何为其他数据类型编写您自己的 RFX 函数。

##  <a name="_core_rfx_function_syntax"></a> RFX 函数语法

每个 RFX 函数采用三个参数 （和一些需要可选的第四个或第五个参数）：

- 一个指向[CFieldExchange](../../mfc/reference/cfieldexchange-class.md)对象。 只需传递`pFX`指针传递到`DoFieldExchange`。

- 因为它的列的名称将显示数据源。

- 记录集类中的参数数据成员的对应字段数据成员的名称。

- （可选）在某些函数、 字符串或正在传输的数组的最大长度。 此值默认为 255 个字节，但你可能想要对其进行更改。 最大大小为基础的最大大小`CString`对象 — **INT_MAX** (2,147,483,647) 个字节，但您可能会遇到该大小之前的驱动程序限制。

- （可选）在`RFX_Text`函数，你有时会使用第五个参数指定列的数据类型。

有关详细信息，请参阅下的 RFX 函数[宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)中*类库参考*。 当你可能会进行特殊的示例使用的参数，请参阅[记录集：获取 Sum 及其他聚合结果 (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)。

##  <a name="_core_rfx_data_types"></a> RFX 数据类型

类库提供 RFX 函数之间的数据源和记录集传输许多不同的数据类型。 以下列表总结了 RFX 函数按数据类型。 在其中必须编写您自己 RFX 函数调用的情况下，从这些数据类型的函数中进行选择。

|函数|数据类型|
|--------------|---------------|
|`RFX_Bool`|**BOOL**|
|`RFX_Byte`|**BYTE**|
|`RFX_Binary`|`CByteArray`|
|`RFX_Double`|**double**|
|`RFX_Single`|**float**|
|`RFX_Int`|**int**|
|`RFX_Long`|**long**|
|`RFX_LongBinary`|`CLongBinary`|
|`RFX_Text`|`CString`|
|`RFX_Date`|`CTime`|


有关详细信息，请参阅下的 RFX 函数文档[宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)中*类库参考*。 有关如何信息C++数据类型映射到 SQL 数据类型，请参阅表 ANSI SQL 数据类型映射到C++中的数据类型[SQL:SQL 和C++数据类型 (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)。

## <a name="see-also"></a>请参阅

[记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[记录字段交换：RFX 的工作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[记录集：确定记录集的参数 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[记录集：动态绑定数据列 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[CRecordset 类](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange 类](../../mfc/reference/cfieldexchange-class.md)