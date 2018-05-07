---
title: 更改可能会使对默认代码 （MFC 数据访问） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- record views [C++], customizing default code
ms.assetid: 9992ed37-a6bf-45a5-a572-5c14e42b6628
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e647f6350819fa2cccb5f8319f95fbac16ca19fc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="changes-you-might-make-to-the-default-code--mfc-data-access"></a>可以对默认代码做的更改（MFC 数据访问）
[MFC 应用程序向导](../mfc/reference/database-support-mfc-application-wizard.md)为你在单个表中选择所有记录编写记录集类。 你通常还可以采用下列一种或多种方式修改该行为：  
  
-   为记录集设置筛选器或排序顺序。 在执行此操作`OnInitialUpdate`记录集对象之前构造完毕后其**打开**调用成员函数。 有关详细信息，请参阅[记录集： 筛选记录 (ODBC)](../data/odbc/recordset-filtering-records-odbc.md)和[记录集： 排序记录 (ODBC)](../data/odbc/recordset-sorting-records-odbc.md)。  
  
-   确定记录集的参数。 筛选后指定运行时的实际参数值。 有关详细信息，请参阅[记录集： 参数化记录集 (ODBC)](../data/odbc/recordset-parameterizing-a-recordset-odbc.md)  
  
-   自定义 SQL 将字符串传递给[打开](../mfc/reference/crecordset-class.md#open)成员函数。 可以使用此技术实现的任务的讨论，请参阅[SQL： 自定义您记录集的 SQL 语句 (ODBC)](../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)。  
  
## <a name="see-also"></a>请参阅  
 [使用记录视图](../data/using-a-record-view-mfc-data-access.md)