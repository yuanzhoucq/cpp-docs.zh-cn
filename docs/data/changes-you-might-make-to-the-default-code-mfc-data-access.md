---
title: 可以对默认代码做的更改（MFC 数据访问）
ms.date: 11/04/2016
helpviewer_keywords:
- record views [C++], customizing default code
ms.assetid: 9992ed37-a6bf-45a5-a572-5c14e42b6628
ms.openlocfilehash: fc448ae1e13025a83b33386c2845bdf7bb4d5eec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398003"
---
# <a name="changes-you-might-make-to-the-default-code--mfc-data-access"></a>可以对默认代码做的更改（MFC 数据访问）

[MFC 应用程序向导](../mfc/reference/database-support-mfc-application-wizard.md)记录集类为您编写了一个表中选择所有记录。 你通常还可以采用下列一种或多种方式修改该行为：

- 为记录集设置筛选器或排序顺序。 在执行此操作`OnInitialUpdate`记录集对象之前构造完毕后其`Open`调用成员函数。 有关详细信息，请参阅[记录集：筛选记录 (ODBC)](../data/odbc/recordset-filtering-records-odbc.md) 和[记录集：排序记录 (ODBC)](../data/odbc/recordset-sorting-records-odbc.md)。

- 确定记录集的参数。 筛选后指定运行时的实际参数值。 有关详细信息，请参阅[记录集：参数化记录集 (ODBC)](../data/odbc/recordset-parameterizing-a-recordset-odbc.md)

- 传递到自定义的 SQL 字符串[打开](../mfc/reference/crecordset-class.md#open)成员函数。 有关使用此技术完的操作的讨论，请参阅 [SQL：自定义记录集的 SQL 语句 (ODBC)](../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)。

## <a name="see-also"></a>请参阅

[使用记录视图](../data/using-a-record-view-mfc-data-access.md)