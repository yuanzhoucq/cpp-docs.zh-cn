---
title: "以编程方式在 ODBC 数据源中创建表 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- programmatically creating ODBC tables [C++]
- tables [C++]
- ODBC data sources, creating tables in
- tables [C++], creating programmatically
ms.assetid: 9ca68fb5-c3df-424a-a75c-e3fb01cc1b18
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 43be9c8a2339bb47d598304145a8c34f391b11c8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="data-source-programmatically-creating-a-table-in-an-odbc-data-source"></a>数据源：以编程方式在 ODBC 数据源中创建表
本主题说明如何创建表以获取你的数据源，使用`ExecuteSQL`类的成员函数`CDatabase`，将该函数传递一个字符串，包含**CREATE TABLE** SQL 语句。  
  
 有关在 MFC 中的 ODBC 数据源的常规信息，请参阅[数据源 (ODBC)](../../data/odbc/data-source-odbc.md)。 主题[数据源： 以编程方式配置 ODBC 数据源](../../data/odbc/data-source-programmatically-configuring-an-odbc-data-source.md)介绍了如何创建数据源。  
  
 如果您拥有建立数据源，你可以轻松创建表使用`ExecuteSQL`成员函数和**CREATE TABLE** SQL 语句。 例如，如果你有`CDatabase`调用对象`myDB`，你可以使用以下的 MFC 代码来创建一个表：  
  
```  
myDB.ExecuteSQL("CREATE TABLE OFFICES (OfficeID TEXT(4)" ",   
                         OfficeName TEXT(10))");  
```  
  
 此代码示例创建名为"办公室"由维护的 Microsoft Access 数据源连接中的表`myDB`; 表中包含两个字段"OfficeID"和"OfficeName。"  
  
> [!NOTE]
>  中指定的字段类型**CREATE TABLE** SQL 语句可能会因你使用的 ODBC 驱动程序。 Microsoft Query 程序 （随 Visual c + + 1.5） 是一种方法发现可用的数据源的字段类型。 在 Microsoft 查询中，单击**文件**，单击**表定义**，从数据源，选择一个表并查看中显示的类型**类型**组合框。 SQL 语法也存在是为了创建索引。  
  
## <a name="see-also"></a>请参阅  
 [数据源 (ODBC)](../../data/odbc/data-source-odbc.md)