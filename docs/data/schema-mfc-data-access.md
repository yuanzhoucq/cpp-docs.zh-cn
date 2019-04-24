---
title: 架构（MFC 数据访问）
ms.date: 11/04/2016
helpviewer_keywords:
- structures [C++], database
- databases [C++], schema
- database schema [C++], about database schemas
- database schema [C++]
- schemas [C++], database
- structures [C++]
ms.assetid: 7d17e35f-1ccf-4853-b915-5b8c7a45b9ee
ms.openlocfilehash: cc333ee987ed0c6cba6cb11730d8f940e49d525d
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59039028"
---
# <a name="schema--mfc-data-access"></a>架构（MFC 数据访问）

数据库架构描述了表格的当前结构和数据库中的数据库视图。 一般情况下，向导生成的代码假定数据集所访问的表格的架构不会改变，但数据库类可以处理部分架构更改，如添加、重新排序或删除未绑定的列。 如果表格更改，则必须手动更新表格的记录集，然后重新编译应用程序。

你还可以补充由向导生成的代码来处理在编译时并非完全清楚架构的数据库。 有关详细信息，请参阅[记录集：动态绑定数据列 (ODBC)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。

## <a name="see-also"></a>请参阅

[数据访问编程 (MFC/ATL)](../data/data-access-programming-mfc-atl.md)<br/>
[SQL](../data/odbc/sql.md)<br/>
[记录集 (ODBC)](../data/odbc/recordset-odbc.md)