---
title: 记录集：执行联接 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- joins [C++], in recordsets
- data binding [C++], recordset columns
- recordsets [C++], binding data
- data binding [C++], columns in recordsets
- filters [C++], join conditions for recordsets
- ODBC recordsets [C++], joins
- recordsets [C++], joining tables
ms.assetid: ca720900-a156-4780-bf01-4293633bea64
ms.openlocfilehash: 135992e7eebd56c985c24228370695f10ac6da3a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523933"
---
# <a name="recordset-performing-a-join-odbc"></a>记录集：执行联接 (ODBC)

本主题适用于 MFC ODBC 类。

## <a name="what-a-join-is"></a>什么是联接

联接操作，常见的数据访问任务，使您可以使用多个表使用一个记录集对象中的数据。 联接两个或多个表生成的记录集可以包含每个表中的列，但显示为单个表为你的应用程序。 联接有时会使用所有表，但有时 SQL 中的所有列**选择**联接中的子句只都使用某些的每个表中的列。 数据库类支持只读联接，但不可更新的联接。

若要选择包含已联接的表中的列的记录，需要以下项：

- 包含要联接的所有表的名称的表列表。

- 包含的所有参与的列名称的列列表。 具有相同名称但来自不同表的列是由表名限定。

- 筛选器 (SQL**其中**子句)，它指定在其联接表的列。 此筛选器将在窗体"Table1.KeyCol = Table2.KeyCol"和实际上完成了联接。

可以在相同的方式联接两个以上的表，即多个列对，通过 SQL 关键字联接每一对通过**AND**。

## <a name="see-also"></a>请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[记录集：为预定义查询声明一个类 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)<br/>
[记录集：声明表的类 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[记录集：再次查询记录集 (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)