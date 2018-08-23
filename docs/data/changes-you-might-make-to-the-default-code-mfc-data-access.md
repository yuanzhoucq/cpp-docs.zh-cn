---
title: 可以对默认代码 （MFC 数据访问） 做的更改 |Microsoft Docs
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
ms.openlocfilehash: 29b5373bd9fb638e7ee4d20cba0c64b9354be70f
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2018
ms.locfileid: "39339193"
---
# <a name="changes-you-might-make-to-the-default-code--mfc-data-access"></a>可以对默认代码做的更改（MFC 数据访问）
[MFC 应用程序向导](../mfc/reference/database-support-mfc-application-wizard.md)记录集类为您编写了一个表中选择所有记录。 你通常还可以采用下列一种或多种方式修改该行为：  
  
-   为记录集设置筛选器或排序顺序。 在执行此操作`OnInitialUpdate`记录集对象之前构造完毕后其`Open`调用成员函数。 有关详细信息，请参阅[记录集： 筛选记录 (ODBC)](../data/odbc/recordset-filtering-records-odbc.md)并[记录集： 排序记录 (ODBC)](../data/odbc/recordset-sorting-records-odbc.md)。  
  
-   确定记录集的参数。 筛选后指定运行时的实际参数值。 有关详细信息，请参阅[记录集： 参数化记录集 (ODBC)](../data/odbc/recordset-parameterizing-a-recordset-odbc.md)  
  
-   传递到自定义的 SQL 字符串[打开](../mfc/reference/crecordset-class.md#open)成员函数。 您可以实现利用这种技术的讨论，请参阅[SQL： 自定义您记录集的 SQL 语句 (ODBC)](../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)。  
  
## <a name="see-also"></a>请参阅  
 [使用记录视图](../data/using-a-record-view-mfc-data-access.md)