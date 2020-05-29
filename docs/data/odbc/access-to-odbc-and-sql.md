---
title: 访问 ODBC 和 SQL
ms.date: 11/04/2016
helpviewer_keywords:
- API calls [C++], calling DAO or ODBC directly
- Windows API [C++], calling from MFC
- ODBC API functions [C++]
- ODBC API functions [C++], calling from MFC
- SQL [C++], calling ODBC API functions
- ODBC [C++], API functions
ms.assetid: 5613d7dc-00b7-4646-99ae-1116c05c52b4
ms.openlocfilehash: 0b590ce9309cbbe95285001cc5befe70a1d1961f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213325"
---
# <a name="access-to-odbc-and-sql"></a>访问 ODBC 和 SQL

Microsoft 基础类库封装了许多 Windows API 调用，并且仍允许直接调用任何 Windows API 函数。 数据库类提供与 ODBC API 相同的灵活性。 尽管数据库类会使你免受 ODBC 的很大的复杂性，但你可以直接从程序的任何位置调用 ODBC API 函数。

同样，数据库类使你不必使用[sql](../../data/odbc/sql.md)，但你可以根据需要直接使用 sql。 您可以通过在打开记录集时传递自定义 SQL 语句（或设置默认语句的部分）来自定义记录集对象。 你还可以使用类[CDatabase](../../mfc/reference/cdatabase-class.md)的[ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql)成员函数直接执行 SQL 调用。

有关详细信息，请参阅[odbc：直接调用 ODBC API 函数](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)和[SQL：进行直接 SQL 调用（ODBC）](../../data/odbc/sql-making-direct-sql-calls-odbc.md)。

## <a name="see-also"></a>另请参阅

[ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)
