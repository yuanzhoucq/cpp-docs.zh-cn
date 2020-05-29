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
ms.openlocfilehash: f1afded360cfeff564f1f3d8bb9b294aa33cb733
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367130"
---
# <a name="record-field-exchange-using-the-rfx-functions"></a>记录字段交换：使用 RFX 函数

本主题介绍如何使用构成`DoFieldExchange`重写正文的 RFX 函数调用。

> [!NOTE]
> 本主题适用于从[CRecordset](../../mfc/reference/crecordset-class.md)派生的类，其中尚未实现批量行提取。 如果使用批量提取行，则将实现批量记录字段交换（批量 RFX）。 批量 RFX 与 RFX 类似。 要了解差异，请参阅[记录集：批量提取记录 （ODBC）。](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

RFX 全局函数在数据源列和记录集中的字段数据成员之间交换数据。 在记录集的[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)成员函数中写入 RFX 函数调用。 本主题简要介绍这些函数，并显示 RFX 函数可用的数据类型。 [技术说明 43](../../mfc/tn043-rfx-routines.md)介绍了如何为其他数据类型编写自己的 RFX 函数。

## <a name="rfx-function-syntax"></a><a name="_core_rfx_function_syntax"></a>RFX 函数语法

每个 RFX 函数需要三个参数（有些参数采用可选的第四个或第五个参数）：

- 指向[CFieldExchange](../../mfc/reference/cfieldexchange-class.md)对象的指针。 您只需传递传递给`pFX``DoFieldExchange`的指针即可。

- 列的名称，因为它显示在数据源上。

- 记录集类中相应字段数据成员或参数数据成员的名称。

- （可选）在某些函数中，要传输的字符串或数组的最大长度。 这默认值为 255 字节，但您可能希望更改它。 最大大小基于`CString`对象的最大大小 **（INT_MAX** （2，147，483，647） 字节，但在该大小之前可能会遇到驱动程序限制。

- （可选）在函数`RFX_Text`中，有时使用第五个参数来指定列的数据类型。

有关详细信息，请参阅*类库参考*中的[宏和全局](../../mfc/reference/mfc-macros-and-globals.md)下的 RFX 函数。 有关何时可以特殊使用参数的示例，请参阅[记录集：获取 SUM 和其他聚合结果 （ODBC）。](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)

## <a name="rfx-data-types"></a><a name="_core_rfx_data_types"></a>RFX 数据类型

类库提供 RFX 函数，用于在数据源和记录集之间传输许多不同的数据类型。 下面的列表按数据类型汇总了 RFX 函数。 在必须编写自己的 RFX 函数调用的情况下，请按数据类型从这些函数中选择。

|函数|数据类型|
|--------------|---------------|
|`RFX_Bool`|**Bool**|
|`RFX_Byte`|**字节**|
|`RFX_Binary`|`CByteArray`|
|`RFX_Double`|**double**|
|`RFX_Single`|**浮动**|
|`RFX_Int`|**Int**|
|`RFX_Long`|**长**|
|`RFX_LongBinary`|`CLongBinary`|
|`RFX_Text`|`CString`|
|`RFX_Date`|`CTime`|

有关详细信息，请参阅*类库参考*中的[宏和全局](../../mfc/reference/mfc-macros-and-globals.md)下的 RFX 函数文档。 有关C++数据类型如何映射到 SQL 数据类型的信息，请参阅映射到 SQL 中C++数据类型的表 ANSI SQL 数据类型[：SQL 和C++数据类型 （ODBC）。](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)

## <a name="see-also"></a>另请参阅

[记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[记录字段交换：RFX 的工作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[记录集：参数化记录集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[记录集：动态绑定数据列 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[CRecordset 类](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange 课程](../../mfc/reference/cfieldexchange-class.md)
