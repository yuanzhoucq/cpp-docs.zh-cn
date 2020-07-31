---
title: SQL：SQL 和 C++ 数据类型 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- data types [C++], SQL vs. C++
- SQL data types [C++]
- SQL [C++], vs. C++ data types
ms.assetid: 066e0070-d4da-435c-9c4b-f7cab3352c86
ms.openlocfilehash: 424ae09f6462d4d34b5a847fc210f9329e76d788
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218333"
---
# <a name="sql-sql-and-c-data-types-odbc"></a>SQL：SQL 和 C++ 数据类型 (ODBC)

> [!NOTE]
> 此信息适用于 MFC ODBC 类。 如果使用的是 MFC DAO 类，请参阅 DAO 帮助中的 "Microsoft Jet 数据库引擎 SQL 和 ANSI SQL 比较" 主题。

下表将 ANSI SQL 数据类型映射到 c + + 数据类型。 这补充了[ODBC 程序员参考](/sql/odbc/reference/odbc-programmer-s-reference)文档的附录 D 中提供的 C 语言信息。 向导可管理大多数数据类型映射。 如果不使用向导，可以使用映射信息来帮助您手动编写字段交换代码。

### <a name="ansi-sql-data-types-mapped-to-c-data-types"></a>映射到 c + + 数据类型的 ANSI SQL 数据类型

|ANSI SQL 数据类型|C++ 数据类型|
|------------------------|---------------------|
|**CHAR**|`CString`|
|DECIMAL|`CString`2|
|**SMALLINT**|**`int`**|
|**实际上**|**`float`**|
|**整数**|**`long`**|
|**FLOAT**|**`double`**|
|**仔细**|**`double`**|
|**加法**|`CString`2|
|**VARCHAR**|`CString`|
|**LONGVARCHAR**|`CLongBinary`， `CString` 2|
|**小段**|**型**|
|**TINYINT**|**位**|
|**BIGINT**|`CString`2|
|**二进制**|`CByteArray`|
|**VARBINARY**|`CByteArray`|
|**LONGVARBINARY**|`CLongBinary`， `CByteArray` 3|
|DATE|`CTime`, `CString`|
|**阶段**|`CTime`, `CString`|
|**标志**|`CTime`, `CString`|

1. 将 ANSI **DECIMAL**和**NUMERIC**映射到， `CString` 因为**SQL_C_CHAR**是默认的 ODBC 传输类型。

2. 默认情况下，在映射到时，将截断超过255个字符的字符数据 `CString` 。 可以通过显式设置的*nMaxLength*参数来扩展截断长度 `RFX_Text` 。

3. 默认情况下，在映射到时，将截断超过255个字符的二进制数据 `CByteArray` 。 可以通过显式设置的*nMaxLength*参数来扩展截断长度 `RFX_Binary` 。

如果未使用 ODBC 游标库，则在尝试使用 Microsoft SQL Server ODBC 驱动程序和 MFC ODBC 数据库类更新两个或多个长可变长度字段时可能会遇到问题。 ODBC 类型（ **SQL_LONGVARCHAR**和**SQL_LONGVARBINARY**）映射到文本和图像 SQL Server 类型。 如果在对 `CDBException` 的同一调用上更新两个或多个长可变长度字段，则会引发 `CRecordset::Update` 。 因此，请不要同时更新多个长列 `CRecordset::Update` 。 可以同时更新多个长列和 ODBC API `SQLPutData` 。 你还可以使用 ODBC 游标库，但不建议将其用于支持游标且不需要游标库的驱动程序（如 SQL Server 驱动程序）。

如果将 ODBC 游标库与 MFC ODBC 数据库类和 Microsoft SQL Server ODBC 驱动程序一起使用，则在调用后调用时，可能会出现一个**断言**和一个 `CDBException` `CRecordset::Update` `CRecordset::Requery` 。 相反，请调用而 `CRecordset::Close` `CRecordset::Open` 不是 `CRecordset::Requery` 。 另一种解决方案是不使用 ODBC 游标库，因为 SQL Server 和 SQL Server ODBC 驱动程序提供本机支持游标，并且不需要 ODBC 游标库。

## <a name="see-also"></a>另请参阅

[SQL](../../data/odbc/sql.md)<br/>
[SQL：进行直接 SQL 调用（ODBC）](../../data/odbc/sql-making-direct-sql-calls-odbc.md)
