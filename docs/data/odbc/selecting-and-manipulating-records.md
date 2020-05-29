---
title: 选择和操作记录
ms.date: 05/09/2019
helpviewer_keywords:
- records, selecting
- record selection, MFC ODBC classes
- ODBC recordsets, selecting records
ms.assetid: 7f0b3a4a-9941-4475-a612-9ec8d15b7691
ms.openlocfilehash: 596ee602b5358fbd854888f43f21748fd4d85b7a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212701"
---
# <a name="selecting-and-manipulating-records"></a>选择和操作记录

> [!NOTE]
> MFC ODBC 使用者向导在 Visual Studio 2019 及更高版本中不可用。 你仍可以手动创建使用者。

通常，当你使用 SQL SELECT 语句从数据源中选择记录时，你将获得一个结果集，此结果集是表或查询中的一组记录。 凭借数据库类，你可以使用记录集对象来选择和访问结果集。 这是从 [CRecordset](../../mfc/reference/crecordset-class.md) 类派生的特定于应用程序的类的对象。 定义记录集类时，需要指定要与其关联的数据源、要使用的表以及表的列。 MFC 应用程序向导或“添加类”（如[添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)中所述）将创建一个与特定数据源连接的类。 向导将编写 `CRecordset` 类的 [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql) 成员函数以返回表名。

通过在运行时使用 [CRecordset](../../mfc/reference/crecordset-class.md) 对象，你可以：

- 检查当前记录的数据字段。

- 对记录集进行筛选或排序。

- 自定义默认的 SQL SELECT 语句。

- 滚动浏览所选的记录。

- 添加、更新或删除记录（如果数据源和记录集都是可更新的）。

- 测试记录集是否允许再次查询和刷新记录集的内容。

完成使用记录集对象后，需要将其关闭并销毁。 有关记录集的详细信息，请参阅[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)。

## <a name="see-also"></a>请参阅

[ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)
