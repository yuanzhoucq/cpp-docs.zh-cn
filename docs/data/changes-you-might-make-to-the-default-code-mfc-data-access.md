---
title: 可以对默认代码做的更改（MFC 数据访问）
ms.date: 11/04/2016
helpviewer_keywords:
- record views [C++], customizing default code
ms.assetid: 9992ed37-a6bf-45a5-a572-5c14e42b6628
ms.openlocfilehash: 7ea616caf176cd1e9e2f26bee1339640067b4e3e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213455"
---
# <a name="changes-you-might-make-to-the-default-code--mfc-data-access"></a>可以对默认代码做的更改（MFC 数据访问）

[MFC 应用程序向导](../mfc/reference/database-support-mfc-application-wizard.md)将为您编写记录集类，您可以选择一个表中的所有记录。 你通常还可以采用下列一种或多种方式修改该行为：

- 为记录集设置筛选器或排序顺序。 在构造 recordset 对象之后但在调用其 `Open` 成员函数之前，在 `OnInitialUpdate` 中执行此操作。 有关详细信息，请参阅[记录集：筛选记录（odbc）](../data/odbc/recordset-filtering-records-odbc.md)和[记录集：对记录进行排序（odbc）](../data/odbc/recordset-sorting-records-odbc.md)。

- 确定记录集的参数。 筛选后指定运行时的实际参数值。 有关详细信息，请参阅[记录集：参数化记录集（ODBC）](../data/odbc/recordset-parameterizing-a-recordset-odbc.md)

- 向[Open](../mfc/reference/crecordset-class.md#open)成员函数传递自定义的 SQL 字符串。 有关使用此方法可以完成的操作的讨论，请参阅[sql：自定义记录集的 SQL 语句（ODBC）](../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)。

## <a name="see-also"></a>另请参阅

[使用记录视图](../data/using-a-record-view-mfc-data-access.md)
