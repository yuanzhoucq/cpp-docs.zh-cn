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
ms.openlocfilehash: e1cb5df4a93fc642ccf4d500a5eb93690b0b3d75
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2020
ms.locfileid: "86403813"
---
# <a name="odbc-calling-odbc-api-functions-directly"></a>ODBC：直接调用 ODBC API 函数

与 ODBC 相比，数据库类提供了与[数据源](../../data/odbc/data-source-odbc.md)更简单的接口。 因此，这些类不封装所有 ODBC API。 对于超出类功能范围的任何功能，必须直接调用 ODBC API 函数。 例如，必须直接调用 ODBC 目录函数（、、 `::SQLColumns` `::SQLProcedures` `::SQLTables` 等）。

> [!NOTE]
> ODBC 数据源可通过 MFC ODBC 类访问，如本主题中所述，或通过 MFC 数据访问对象（DAO）类访问。

若要直接调用 ODBC API 函数，您必须执行的步骤与您在不使用框架的情况下进行调用时需要执行的步骤相同。 它们的步骤如下：

- 为调用返回的任何结果分配存储。

- 传递 ODBC `HDBC` 或 `HSTMT` 句柄，具体取决于函数的参数签名。 使用[AFXGetHENV](../../mfc/reference/database-macros-and-globals.md#afxgethenv)宏检索 ODBC 句柄。

   成员变量 `CDatabase::m_hdbc` 和 `CRecordset::m_hstmt` 是可用的，因此您无需自行分配和初始化这些变量。

- 可能需要调用其他 ODBC 函数来准备或跟进主调用。

- 完成时释放存储。

有关这些步骤的详细信息，请参阅[ODBC 程序员参考](/sql/odbc/reference/odbc-programmer-s-reference)。

除了这些步骤以外，还需要执行额外的步骤来检查函数返回值，确保程序不会等待异步调用完成等。 您可以通过使用 AFX_SQL_ASYNC 和 AFX_SQL_SYNC 宏来简化这些最后的步骤。 有关详细信息，请参阅[MFC 宏和全局](../../mfc/reference/mfc-macros-and-globals.md)。

## <a name="see-also"></a>另请参阅

[ODBC 基础知识](../../data/odbc/odbc-basics.md)
