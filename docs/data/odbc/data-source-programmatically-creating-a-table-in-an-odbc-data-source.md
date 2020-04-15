---
title: 在 ODBC 数据源中以编程方式创建表
ms.date: 11/04/2016
helpviewer_keywords:
- programmatically creating ODBC tables [C++]
- tables [C++]
- ODBC data sources, creating tables in
- tables [C++], creating programmatically
ms.assetid: 9ca68fb5-c3df-424a-a75c-e3fb01cc1b18
ms.openlocfilehash: 6cf26cad7fe39f374daf371902525087b446658c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358843"
---
# <a name="data-source-programmatically-creating-a-table-in-an-odbc-data-source"></a>数据源：以编程方式在 ODBC 数据源中创建表

本主题介绍如何使用类`ExecuteSQL``CDatabase`的成员函数为数据源创建表，传递包含 CREATE **TABLE** SQL 语句的字符串。

有关 MFC 中 ODBC 数据源的一般信息，请参阅[数据源 （ODBC）。](../../data/odbc/data-source-odbc.md) 主题[数据源：以编程方式配置 ODBC 数据源](../../data/odbc/data-source-programmatically-configuring-an-odbc-data-source.md)描述创建数据源。

建立数据源后，可以轻松地使用`ExecuteSQL`成员函数和 CREATE **TABLE** SQL 语句创建表。 例如，如果您有一个`CDatabase`称为 的对象`myDB`，则可以使用以下 MFC 代码创建表：

```
myDB.ExecuteSQL("CREATE TABLE OFFICES (OfficeID TEXT(4)" ",
                         OfficeName TEXT(10))");
```

此代码示例在 Microsoft 访问数据源连接中创建名为"OFFICE"的`myDB`表，该表包含两个字段"OfficeID"和"办公室名称"。

> [!NOTE]
> **CREATE TABLE** SQL 语句中指定的字段类型可能因您使用的 ODBC 驱动程序而异。 Microsoft 查询程序（使用 Visual C++ 1.5 分发）是发现数据源可用的字段类型的一种方式。 在 Microsoft 查询**File**中，单击"**文件"，单击"Table_Definition"，** 从数据源中选择一个表，并查看 **"类型组合"** 框中显示的类型。 SQL 语法也存在以创建索引。

## <a name="see-also"></a>另请参阅

[数据源 (ODBC)](../../data/odbc/data-source-odbc.md)
