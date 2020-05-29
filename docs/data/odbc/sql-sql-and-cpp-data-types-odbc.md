---
title: SQL：SQL 和 C++ 数据类型 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- data types [C++], SQL vs. C++
- SQL data types [C++]
- SQL [C++], vs. C++ data types
ms.assetid: 066e0070-d4da-435c-9c4b-f7cab3352c86
ms.openlocfilehash: cffe44b832ac1eb28d368072b8f0e92ea9f57feb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374478"
---
# <a name="sql-sql-and-c-data-types-odbc"></a>SQL：SQL 和 C++ 数据类型 (ODBC)

> [!NOTE]
> 此信息适用于 MFC ODBC 类。 如果您正在使用 MFC DAO 类，请参阅 DAO 帮助中的主题"微软喷气数据库引擎 SQL 和 ANSI SQL 的比较"。

下表将 ANSI SQL 数据类型映射到C++数据类型。 这增强了*ODBC SDK 程序员*在 MSDN 库 CD 上的参考附录 D 中给出*的*C 语言信息。 向导为您管理大多数数据类型映射。 如果不使用向导，则可以使用映射信息来帮助手动编写字段交换代码。

### <a name="ansi-sql-data-types-mapped-to-c-data-types"></a>映射到C++数据类型的 ANSI SQL 数据类型

|ANSI SQL 数据类型|C++ 数据类型|
|------------------------|---------------------|
|**字符**|`CString`|
|**十进制**|`CString`1|
|**小林特**|**Int**|
|**真正**|**浮动**|
|**整数**|**长**|
|**浮动**|**double**|
|**双**|**double**|
|**数字**|`CString`1|
|**瓦尔查尔**|`CString`|
|**LONGVARCHAR**|`CLongBinary`， `CString` 2|
|**位**|**Bool**|
|**蒂林特**|**字节**|
|**比金特**|`CString`1|
|**二 进 制**|`CByteArray`|
|**瓦尔里进制**|`CByteArray`|
|**LONGVARBINARY**|`CLongBinary`， `CByteArray` 3|
|**日期**|`CTime`, `CString`|
|**时间**|`CTime`, `CString`|
|**时间 戳**|`CTime`, `CString`|

1. ANSI **DECIMAL**和**数字**映射，`CString`因为**SQL_C_CHAR**是默认的 ODBC 传输类型。

2. 默认情况下，在映射到 时，超过 255 个字符的字符数据将被`CString`截断。 可以通过显式设置*nMaxLength 参数*来延长截断长度`RFX_Text`。

3. 默认情况下，在映射到 时，超过 255 个字符的二进制数据`CByteArray`将被截断。 可以通过显式设置*nMaxLength 参数*来延长截断长度`RFX_Binary`。

如果不使用 ODBC 游标库，则在尝试使用 Microsoft SQL Server ODBC 驱动程序和 MFC ODBC 数据库类更新两个或多个长变量长度字段时可能会遇到问题。 ODBC 类型 **，SQL_LONGVARCHAR**和**SQL_LONGVARBINARY，** 映射到文本和图像 SQL 服务器类型。 如果`CDBException`在同一调用 上更新两个或多个长度的可变长度字段，`CRecordset::Update`则引发 。 因此，不要与`CRecordset::Update`同时更新多个长列。 您可以同时更新多个长列与 ODBC API `SQLPutData`。 也可以使用 ODBC 游标库，但不建议支持游标的驱动程序（如 SQL Server 驱动程序）使用，并且不需要游标库。

如果将 ODBC 光标库与 MFC ODBC 数据库类和 Microsoft SQL Server ODBC 驱动程序一起使用，则`CDBException`可能会与 调用`CRecordset::Update`后调用`CRecordset::Requery`时一起出现**ASSERT。** 相反，调用`CRecordset::Close``CRecordset::Open`而不是`CRecordset::Requery`。 另一个解决方案是不使用 ODBC 游标库，因为 SQL Server 和 SQL Server ODBC 驱动程序为游标本机提供本机支持，并且不需要 ODBC 游标库。

## <a name="see-also"></a>另请参阅

[SQL](../../data/odbc/sql.md)<br/>
[SQL：进行直接 SQL 调用 (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)
