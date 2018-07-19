---
title: 记录集： 执行联接 (ODBC) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- joins [C++], in recordsets
- data binding [C++], recordset columns
- recordsets [C++], binding data
- data binding [C++], columns in recordsets
- filters [C++], join conditions for recordsets
- ODBC recordsets [C++], joins
- recordsets [C++], joining tables
ms.assetid: ca720900-a156-4780-bf01-4293633bea64
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0be740a57f5c455b971dd23575401c666bf0723c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33093306"
---
# <a name="recordset-performing-a-join-odbc"></a>记录集：执行联接 (ODBC)
本主题适用于 MFC ODBC 类。  
  
## <a name="what-a-join-is"></a>什么联接就是将  
 联接操作，一个通用的数据访问任务，使你可以使用单个记录集对象的多个表的数据。 联接两个或多个表生成一个可以包含每个表中的列，但显示为你的应用程序到单个表的记录集。 有时联接使用所有表，但有时 SQL 中的所有列**选择**子句一个联接中的只都使用某些的每个表中的列。 数据库类支持只读联接，但不是可更新的联接。  
  
 若要选择包含联接的表中的列的记录，你需要以下各项：  
  
-   包含要联接的所有表的名称的表列表。  
  
-   包含所有参与列的名称的列列表。 具有相同名称但来自不同表的列是由表名限定。  
  
-   筛选器 (SQL**其中**子句)，它指定在其表已联接的列。 此筛选器的形式"Table1.KeyCol = Table2.KeyCol"和实际完成联接。  
  
 可以在相同的方式联接两个以上的表，即多个列对，通过 SQL 关键字联接每一对通过**AND**。  
  
## <a name="see-also"></a>请参阅  
 [记录集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [记录集： 为预定义的查询 (ODBC) 声明一个类](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)   
 [记录集： 声明表 (ODBC) 类](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)   
 [记录集：再次查询记录集 (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)