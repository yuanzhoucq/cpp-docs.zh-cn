---
title: 连接到数据源 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- database connections [C++], ODBC
- ODBC connections [C++], using
- connections [C++], data source
- databases [C++], connecting to
- data sources [C++], connecting to
- ODBC data sources [C++], connections
- database connections [C++], MFC ODBC classes
ms.assetid: ef6c8c98-5979-43a8-9fb5-5bb06fc59f36
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2b6a33f1e2421c56f89184d26185903b4ec7859e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33088386"
---
# <a name="connecting-to-a-data-source"></a>连接到数据源
ODBC 数据源是一组特定的数据，访问该数据和数据源，可以使用数据源名称描述的位置所需的信息。 从程序的角度来看，数据源包括数据、 DBMS、 网络 （如果有） 和 ODBC。  
  
 若要访问由数据源提供的数据，您的程序必须首先建立与数据源的连接。 通过该连接管理所有数据访问。  
  
 数据源连接由类封装[CDatabase](../../mfc/reference/cdatabase-class.md)。 当`CDatabase`对象连接到数据源，您可以：  
  
-   构造[记录集](../../mfc/reference/crecordset-class.md)，其中从表或查询中选择记录。  
  
-   管理[事务](../../data/odbc/transaction-odbc.md)，因此所有批处理更新同时提交到数据源 （或回滚整个事务以数据源保持不变）-如果数据源支持所需的级别的事务。  
  
-   直接执行[SQL](../../data/odbc/sql.md)语句。  
  
 当你完成使用的数据源连接时，你关闭`CDatabase`对象，并且销毁它或将其重复用于新的连接。 有关数据源连接的详细信息，请参阅[数据源 (ODBC)](../../data/odbc/data-source-odbc.md)。  
  
## <a name="see-also"></a>请参阅  
 [ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)