---
title: SQL：SQL 和 C++ 数据类型 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- data types [C++], SQL vs. C++
- SQL data types [C++]
- SQL [C++], vs. C++ data types
ms.assetid: 066e0070-d4da-435c-9c4b-f7cab3352c86
ms.openlocfilehash: 1c1ce908b5c8d345906d49adc79e322225ed49f5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212610"
---
# <a name="sql-sql-and-c-data-types-odbc"></a>SQL：SQL 和 C++ 数据类型 (ODBC)

> [!NOTE]
>  此信息适用于 MFC ODBC 类。 如果使用的是 MFC DAO 类，请参阅 DAO 帮助中的 "Microsoft Jet 数据库引擎 SQL 和 ANSI SQL 比较" 主题。

下表将 ANSI SQL 数据类型映射到C++数据类型。 这补充了 MSDN Library CD 上的*ODBC SDK* *程序员参考*的附录 D 中提供的 C 语言信息。 向导可管理大多数数据类型映射。 如果不使用向导，可以使用映射信息来帮助您手动编写字段交换代码。

### <a name="ansi-sql-data-types-mapped-to-c-data-types"></a>映射到数据类型的C++ ANSI SQL 数据类型

|ANSI SQL 数据类型|C++ 数据类型|
|------------------------|---------------------|
|**CHAR**|`CString`|
|**DECIMAL**|`CString` 1|
|**SMALLINT**|**int**|
|**REAL**|**float**|
|**INTEGER**|**long**|
|**FLOAT**|**double**|
|**DOUBLE**|**double**|
|**NUMERIC**|`CString` 1|
|**VARCHAR**|`CString`|
|**LONGVARCHAR**|`CLongBinary`，`CString` 2|
|**BIT**|**BOOL**|
|**TINYINT**|**BYTE**|
|**BIGINT**|`CString` 1|
|**二进制**|`CByteArray`|
|**VARBINARY**|`CByteArray`|
|**LONGVARBINARY**|`CLongBinary`，`CByteArray` 3|
|**DATE**|`CTime`、`CString`|
|**TIME**|`CTime`、`CString`|
|**TIMESTAMP**|`CTime`、`CString`|

1. ANSI **DECIMAL**和**NUMERIC** map to `CString` 因为**SQL_C_CHAR**为默认 ODBC 传输类型。

2. 默认情况下，在映射到 `CString`时，将截断超过255个字符的字符数据。 可以通过显式设置 `RFX_Text`的*nMaxLength*参数来扩展截断长度。

3. 默认情况下，在映射到 `CByteArray`时，将默认截断超过255个字符的二进制数据。 可以通过显式设置 `RFX_Binary`的*nMaxLength*参数来扩展截断长度。

如果未使用 ODBC 游标库，则在尝试使用 Microsoft SQL Server ODBC 驱动程序和 MFC ODBC 数据库类更新两个或多个长可变长度字段时可能会遇到问题。 ODBC 类型（ **SQL_LONGVARCHAR**和**SQL_LONGVARBINARY**）映射到文本和图像 SQL Server 类型。 如果在对 `CRecordset::Update`的同一调用上更新两个或更多长可变长度字段，则会引发 `CDBException`。 因此，请不要同时更新多个 `CRecordset::Update`的长列。 可以同时更新多个长列和 ODBC API `SQLPutData`。 你还可以使用 ODBC 游标库，但不建议将其用于支持游标且不需要游标库的驱动程序（如 SQL Server 驱动程序）。

如果你使用的是包含 MFC ODBC 数据库类和 Microsoft SQL Server ODBC 驱动程序的 ODBC 游标库，则如果对 `CRecordset::Update` 的调用遵循对 `CRecordset::Requery`的调用，则可能会出现一个**断言**和一个 `CDBException`。 相反，请调用 `CRecordset::Close` 和 `CRecordset::Open` 而不是 `CRecordset::Requery`。 另一种解决方案是不使用 ODBC 游标库，因为 SQL Server 和 SQL Server ODBC 驱动程序提供本机支持游标，并且不需要 ODBC 游标库。

## <a name="see-also"></a>另请参阅

[SQL](../../data/odbc/sql.md)<br/>
[SQL：进行直接 SQL 调用 (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)
