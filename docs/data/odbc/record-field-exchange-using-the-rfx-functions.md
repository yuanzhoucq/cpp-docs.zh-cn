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
ms.openlocfilehash: 4d621fbe2207114dd51845b819d309802a009690
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216526"
---
# <a name="record-field-exchange-using-the-rfx-functions"></a>记录字段交换：使用 RFX 函数

本主题说明如何使用构成替代体的 RFX 函数调用 `DoFieldExchange` 。

> [!NOTE]
> 本主题适用于从[CRecordset](../../mfc/reference/crecordset-class.md)派生的类，其中尚未实现批量提取行。 如果使用批量提取行，则将实现批量记录字段交换（批量 RFX）。 批量 RFX 与 RFX 类似。 若要了解不同之处，请参阅[记录集：批量提取记录（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

RFX 全局函数在数据源中的列与记录集的字段数据成员之间交换数据。 在记录集的[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)成员函数中编写 RFX 函数调用。 本主题简要介绍函数并显示 RFX 函数可用的数据类型。 [技术说明 43](../../mfc/tn043-rfx-routines.md)介绍了如何为其他数据类型编写您自己的 RFX 函数。

## <a name="rfx-function-syntax"></a><a name="_core_rfx_function_syntax"></a>RFX 函数语法

每个 RFX 函数使用三个参数（并且有些参数采用可选的第四个或第五个参数）：

- 指向[CFieldExchange](../../mfc/reference/cfieldexchange-class.md)对象的指针。 只需传递 `pFX` 传递到的指针 `DoFieldExchange` 。

- 显示在数据源中的列的名称。

- 记录集类中相应的字段数据成员或参数数据成员的名称。

- 可有可无在某些函数中，是要传输的字符串或数组的最大长度。 默认值为255个字节，但您可能需要更改它。 最大大小取决于对象的最大大小（ `CString` **INT_MAX** （2147483647）字节），但在该大小之前可能会遇到驱动程序限制。

- 可有可无在 `RFX_Text` 函数中，有时使用第五个参数指定列的数据类型。

有关详细信息，请参阅类库*参考*中[宏和全局](../../mfc/reference/mfc-macros-and-globals.md)下的 RFX 函数。 有关可能会对参数进行特殊使用的示例，请参阅[记录集：获取 sum 和其他聚合结果（ODBC）](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)。

## <a name="rfx-data-types"></a><a name="_core_rfx_data_types"></a>RFX 数据类型

类库提供 RFX 函数，用于在数据源和记录集之间传输许多不同的数据类型。 下面的列表按数据类型汇总 RFX 函数。 在必须编写自己的 RFX 函数调用的情况下，请按数据类型从这些函数中进行选择。

|函数|数据类型|
|--------------|---------------|
|`RFX_Bool`|**型**|
|`RFX_Byte`|**位**|
|`RFX_Binary`|`CByteArray`|
|`RFX_Double`|**`double`**|
|`RFX_Single`|**`float`**|
|`RFX_Int`|**`int`**|
|`RFX_Long`|**`long`**|
|`RFX_LongBinary`|`CLongBinary`|
|`RFX_Text`|`CString`|
|`RFX_Date`|`CTime`|

有关详细信息，请参阅类库*参考*中[宏和全局](../../mfc/reference/mfc-macros-and-globals.md)下的 RFX 函数文档。 有关 c + + 数据类型映射到 SQL 数据类型的方式的信息，请参阅 " [sql： sql 和 c + + 数据类型（ODBC）](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)" 中映射到 c + + 数据类型的表 ANSI SQL 数据类型。

## <a name="see-also"></a>另请参阅

[记录字段交换（RFX）](../../data/odbc/record-field-exchange-rfx.md)<br/>
[记录字段交换： RFX 的工作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[记录集：参数化记录集（ODBC）](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[记录集：动态绑定数据列（ODBC）](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[CRecordset 类](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange 类](../../mfc/reference/cfieldexchange-class.md)
