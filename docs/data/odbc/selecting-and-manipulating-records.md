---
title: 选择和操作记录 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- records, selecting
- record selection, MFC ODBC classes
- ODBC recordsets, selecting records
ms.assetid: 7f0b3a4a-9941-4475-a612-9ec8d15b7691
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8cfbeaa1fac2fd9df707dfa9c16ec168d48fc215
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50078344"
---
# <a name="selecting-and-manipulating-records"></a>选择和操作记录

通常当您选择的记录从数据源使用的 SQL**选择**语句中，您将得到一个结果集，这是一组来自一个表或查询中的记录。 使用数据库类中，使用记录集对象来选择和访问的结果集。 这是从类派生一个特定于应用程序的类的对象[CRecordset](../../mfc/reference/crecordset-class.md)。 定义记录集类，需要指定要将其与相关联的数据源、 要使用的表和表中的列。 MFC 应用程序向导或**添加类**(如中所述[添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) 创建一个具有与特定数据源的连接类。 这些向导编写[GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql)类的成员函数`CRecordset`返回的表名称。 有关使用向导创建记录集类的详细信息，请参阅[数据库支持，MFC 应用程序向导](../../mfc/reference/database-support-mfc-application-wizard.md)并[添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)。

使用[CRecordset](../../mfc/reference/crecordset-class.md)对象在运行时，你可以：

- 检查当前记录的数据字段。

- 筛选或排序记录集。

- 自定义默认的 sql 语句**选择**语句。

- 滚动浏览所选的记录。

- 添加、 更新或删除记录 （如果数据源和记录集都是可更新）。

- 测试是否是记录集允许再次查询和刷新记录集的内容。

完成使用记录集对象后，关闭，然后将其销毁。 关于记录集的详细信息，请参阅[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)。

## <a name="see-also"></a>请参阅

[ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)