---
title: ODBC：直接调用 ODBC API 函数
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC API functions [C++], calling
- ODBC [C++], catalog functions
- ODBC API functions [C++]
- APIs [C++], calling
- ODBC classes [C++], vs. ODBC API
- direct ODBC API calls
- catalog functions (ODBC)
- catalog functions (ODBC), calling
- ODBC [C++], API functions
ms.assetid: 4295f1d9-4528-4d2e-bd6a-c7569953c7fa
ms.openlocfilehash: 208749438f40eef746a638dd12373397c426d454
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368668"
---
# <a name="odbc-calling-odbc-api-functions-directly"></a>ODBC：直接调用 ODBC API 函数

与 ODBC 相比，数据库类为[数据源](../../data/odbc/data-source-odbc.md)提供了更简单的接口。 因此，类不封装所有 ODBC API。 对于任何超出类功能的功能，必须直接调用 ODBC API 函数。 例如，必须直接调用 ODBC 目录函数（、、、`::SQLColumns``::SQLProcedures``::SQLTables`等函数）。

> [!NOTE]
> ODBC 数据源可通过 MFC ODBC 类（如本主题所述）或通过 MFC 数据访问对象 （DAO） 类访问。

要直接调用 ODBC API 函数，必须执行与在没有框架的情况下进行调用时相同的步骤。 它们的步骤是：

- 为呼叫返回的任何结果分配存储。

- 传递 ODBC `HDBC` `HSTMT`或句柄，具体取决于函数的参数签名。 使用[AFXGetHENV](../../mfc/reference/database-macros-and-globals.md#afxgethenv)宏检索 ODBC 句柄。

   成员变量`CDatabase::m_hdbc`，`CRecordset::m_hstmt`并且可用，因此您无需自己分配和初始化这些变量。

- 可能调用其他 ODBC 功能来准备或跟进主呼叫。

- 完成后取消分配存储。

有关这些步骤的详细信息，请参阅 MSDN 文档中[的开放数据库连接 （ODBC）](/sql/odbc/microsoft-open-database-connectivity-odbc) SDK。

除了这些步骤之外，还需要执行额外的步骤来检查函数返回值，确保程序不等待异步调用完成，等等。 可以使用AFX_SQL_ASYNC和AFX_SQL_SYNC宏来简化最后的步骤。 有关详细信息，请参阅*MFC 参考*中的[宏和全局](../../mfc/reference/mfc-macros-and-globals.md)。

## <a name="see-also"></a>另请参阅

[ODBC 基础](../../data/odbc/odbc-basics.md)
