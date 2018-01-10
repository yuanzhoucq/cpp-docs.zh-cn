---
title: "选择和操作记录 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- records, selecting
- record selection, MFC ODBC classes
- ODBC recordsets, selecting records
ms.assetid: 7f0b3a4a-9941-4475-a612-9ec8d15b7691
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: dec5e0094405cf9d038e53959da97ba079736505
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="selecting-and-manipulating-records"></a>选择和操作记录
通常当你选择记录从数据源使用的 SQL**选择**语句，会得到一个结果集，这是一组从表或查询的记录。 与数据库类中，你可以使用记录集对象来选择和访问结果集。 这是特定于应用程序类派生自的类的一个对象[CRecordset](../../mfc/reference/crecordset-class.md)。 当定义记录集类时，指定要与之相关的数据源、 若要使用，表和表的列。 MFC 应用程序向导或**添加类**(中所述[添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) 创建一个具有与特定数据源的连接类。 向导编写[GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql)类的成员函数`CRecordset`返回的表名称。 有关使用向导创建记录集类的详细信息，请参阅[数据库支持，MFC 应用程序向导](../../mfc/reference/database-support-mfc-application-wizard.md)和[添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)。  
  
 使用[CRecordset](../../mfc/reference/crecordset-class.md)对象在运行时，你可以：  
  
-   检查当前记录的数据字段。  
  
-   筛选或排序记录集。  
  
-   自定义默认的 sql 语句**选择**语句。  
  
-   滚动查看所选的记录。  
  
-   添加、 更新或删除记录 （如果数据源和记录集都是可更新）。  
  
-   测试是否是记录集允许再次查询，并刷新记录集的内容。  
  
 当你完成使用记录集对象时，你将关闭并将其销毁。 有关记录集的详细信息，请参阅[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)。  
  
## <a name="see-also"></a>请参阅  
 [ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)