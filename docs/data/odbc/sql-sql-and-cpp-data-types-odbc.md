---
title: "SQL: SQL 和 c + + 数据类型 (ODBC) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- data types [C++], SQL vs. C++
- SQL data types [C++]
- SQL [C++], vs. C++ data types
ms.assetid: 066e0070-d4da-435c-9c4b-f7cab3352c86
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 14afd27887368f07610fb1315d7b573c09382c49
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="sql-sql-and-c-data-types-odbc"></a>SQL：SQL 和 C++ 数据类型 (ODBC)
> [!NOTE]
>  此信息适用于 MFC ODBC 类。 如果你正在使用 MFC DAO 类，请参阅主题"比较的 Microsoft Jet 数据库引擎 SQL 和 ANSI SQL"DAO 帮助中。  
  
 下表将 ANSI SQL 数据类型映射到 c + + 数据类型。 这可以增强为给定的附录 D 中的 C 语言信息*ODBC SDK* *程序员参考*MSDN 库 CD 上。 向导管理为你的大多数数据类型映射。 如果不使用向导，你可以使用映射信息可帮助你手动编写字段交换代码。  
  
### <a name="ansi-sql-data-types-mapped-to-c-data-types"></a>ANSI SQL 数据类型映射到 c + + 数据类型  
  
|ANSI SQL 数据类型|C++ 数据类型|  
|------------------------|---------------------|  
|**CHAR**|`CString`|  
|DECIMAL|`CString` 1|  
|**SMALLINT**|`int`|  
|`REAL`|**float**|  
|**整数**|**long**|  
|**FLOAT**|**double**|  
|**DOUBLE**|**double**|  
|**数值**|`CString` 1|  
|**VARCHAR**|`CString`|  
|**LONGVARCHAR**|`CLongBinary`, `CString` 2|  
|**位**|**BOOL**|  
|**TINYINT**|**BYTE**|  
|**BIGINT**|`CString` 1|  
|**二进制**|`CByteArray`|  
|**VARBINARY**|`CByteArray`|  
|**LONGVARBINARY**|`CLongBinary`, `CByteArray` 3|  
|DATE|`CTime`, `CString`|  
|**时间**|**CTime、 CString**|  
|**时间戳**|**CTime、 CString**|  
  
 1. ANSI**十进制**和**数值**映射到`CString`因为**SQL_C_CHAR**是默认 ODBC 传输类型。  
  
 2. 默认情况下，映射到时截断超过 255 个字符的字符数据`CString`。 你可以通过显式设置扩展截断长度`nMaxLength`参数`RFX_Text`。  
  
 3. 超过 255 个字符的二进制数据被截断默认情况下，当映射到`CByteArray`。 你可以通过显式设置扩展截断长度`nMaxLength`参数`RFX_Binary`。  
  
 如果你未使用 ODBC 游标库，你可能会遇到问题时尝试更新两个或更多长时间的变量长度字段使用 Microsoft SQL Server ODBC 驱动程序和 MFC ODBC 数据库类。 ODBC 类型， **SQL_LONGVARCHAR**和**SQL_LONGVARBINARY**、 映射到文本和图像 SQL Server 类型。 A`CDBException`如果更新到相同的调用的两个或多个长可变长度字段引发`CRecordset::Update`。 因此，不更新同时包含多个长列`CRecordset::Update`。 你可以使用 ODBC API 同时更新多个长列**SQLPutData**。 你还可以使用 ODBC 游标库，但这不建议用于和驱动程序，如 SQL Server 驱动程序，支持游标不需要的是光标库。  
  
 如果使用 MFC ODBC 数据库类和 Microsoft SQL Server ODBC 驱动程序，使用 ODBC 游标库**断言**可能发生连同`CDBException`如果调用`CRecordset::Update`调用`CRecordset::Requery`。 而应调用`CRecordset::Close`和`CRecordset::Open`而非`CRecordset::Requery`。 另一个解决方案是不是使用 ODBC 游标库，因为 SQL Server 和 SQL Server ODBC 驱动程序提供本机支持为游标本机和 ODBC 光标库，则不需要。  
  
## <a name="see-also"></a>请参阅  
 [SQL](../../data/odbc/sql.md)   
 [SQL：进行直接 SQL 调用 (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)