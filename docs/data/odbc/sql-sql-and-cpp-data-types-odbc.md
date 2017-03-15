---
title: "SQL：SQL 和 C++ 数据类型 (ODBC) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "数据类型 [C++], SQL 与 C++ 的比较"
  - "SQL [C++], 与 C++ 数据类型"
  - "SQL 数据类型 [C++]"
ms.assetid: 066e0070-d4da-435c-9c4b-f7cab3352c86
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SQL：SQL 和 C++ 数据类型 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  此信息适用于 MFC ODBC 类。  如果使用的是 MFC DAO 类，请参见 DAO 帮助中的“Microsoft Jet 数据库引擎 SQL 和 ANSI SQL 比较”主题。  
  
 下表将 ANSI SQL 数据类型映射到 C\+\+ 数据类型。  这丰富了 MSDN Library 光盘上 *ODBC SDK* *Programmer's Reference*（ODBC SDK 程序员参考）的附录 D 中给出的 C 语言信息。  向导为您管理大部分数据类型映射。  如果不使用向导，可以使用映射信息来帮助您手动编写字段交换代码。  
  
### 映射到 C\+\+ 数据类型的 ANSI SQL 数据类型  
  
|ANSI SQL 数据类型|C\+\+ 数据类型|  
|-------------------|----------------|  
|**CHAR**|`CString`|  
|**DECIMAL**|`CString` 1|  
|**SMALLINT**|`int`|  
|`REAL`|**float**|  
|**INTEGER**|**long**|  
|**FLOAT**|**double**|  
|**DOUBLE**|**double**|  
|**NUMERIC**|`CString` 1|  
|**VARCHAR**|`CString`|  
|**LONGVARCHAR**|`CLongBinary`, `CString` 2|  
|**BIT**|**BOOL**|  
|**TINYINT**|**BYTE**|  
|**BIGINT**|`CString` 1|  
|**BINARY**|`CByteArray`|  
|**VARBINARY**|`CByteArray`|  
|**LONGVARBINARY**|`CLongBinary`, `CByteArray` 3|  
|**DATE**|`CTime`, `CString`|  
|**TIME**|**CTime、CString**|  
|**TIMESTAMP**|**CTime、CString**|  
  
 1.  ANSI **DECIMAL** 和 **NUMERIC** 映射到 `CString`，这是因为 **SQL\_C\_CHAR** 是默认的 ODBC 传输类型。  
  
 2.  默认情况下，超过 255 个字符的字符数据在映射到 `CString` 时被截断。  可以通过显式设置 `RFX_Text` 的 `nMaxLength` 参数来扩展截取长度。  
  
 3.  默认情况下，超过 255 个字符的二进制数据映射到 `CByteArray` 时被截断。  可以通过显式设置 `RFX_Binary` 的 `nMaxLength` 参数来扩展截取长度。  
  
 如果没有使用 ODBC 游标库，则在尝试使用 Microsoft SQL Server ODBC 驱动程序和 MFC ODBC 数据库类更新两个或更多的长可变长度字段时可能会碰到问题。  ODBC 类型 **SQL\_LONGVARCHAR** 和 **SQL\_LONGVARBINARY** 映射到“text”和“image”SQL Server 类型。  如果在对 `CRecordset::Update` 的同一调用上更新两个或更多的长可变长度字段，则将引发 `CDBException`。  因此，不要使用 `CRecordset::Update` 同时更新多个长列。  可以使用 ODBC API **SQLPutData** 同时更新多个长列。  也可以使用 ODBC 游标库，但是建议对支持游标因而不需要游标库的驱动程序（如 SQL Server 驱动程序）不要使用游标库。  
  
 如果将 ODBC 游标库用于 MFC ODBC 数据库类和 Microsoft SQL Server ODBC 驱动程序，则在 `CRecordset::Requery` 调用之后调用 `CRecordset::Update` 时，**ASSERT** 可能会伴随 `CDBException` 一起发生。  作为替代方法，可调用 `CRecordset::Close` 和 `CRecordset::Open`，而不是 `CRecordset::Requery`。  另一种解决方案是不使用 ODBC 游标库，这是因为 SQL Server 和 SQL Server ODBC 驱动程序生来就对游标提供本机支持，因此不需要 ODBC 游标库。  
  
## 请参阅  
 [SQL](../../data/odbc/sql.md)   
 [SQL：进行直接 SQL 调用 \(ODBC\)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)