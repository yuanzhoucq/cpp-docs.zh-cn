---
title: "数据源：以编程方式在 ODBC 数据源中创建表 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ODBC 数据源, 创建表"
  - "以编程方式创建 ODBC 表 [C++]"
  - "表 [C++]"
  - "表 [C++], 以编程方式创建"
ms.assetid: 9ca68fb5-c3df-424a-a75c-e3fb01cc1b18
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 数据源：以编程方式在 ODBC 数据源中创建表
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题说明如何为数据源创建表，创建的方法是使用类 `CDatabase` 的 `ExecuteSQL` 成员函数，给该函数传递一个包含 **CREATE TABLE** SQL 语句的字符串。  
  
 有关 MFC 中 ODBC 数据源的一般信息，请参见[数据源 \(ODBC\)](../../data/odbc/data-source-odbc.md)。  主题 [数据源：用编程方式配置 ODBC 数据源](../../data/odbc/data-source-programmatically-configuring-an-odbc-data-source.md)介绍了如何创建数据源。  
  
 建立了数据源后，就可以很容易使用 `ExecuteSQL` 成员函数和 **CREATE TABLE** SQL 语句来创建表。  例如，假设有一个名为 `myDB` 的 `CDatabase` 对象，则可以用下列 MFC 代码创建一个表：  
  
```  
myDB.ExecuteSQL("CREATE TABLE OFFICES (OfficeID TEXT(4)" ",   
                         OfficeName TEXT(10))");  
```  
  
 此代码示例将在由 `myDB` 维护的 Microsoft Access 数据源连接中创建了一个名为“OFFICES”的表，该表包含“OfficeID”和“OfficeName”这两个字段。  
  
> [!NOTE]
>  根据您所使用的 ODBC 驱动程序，在 **CREATE TABLE** SQL 语句中指定的字段类型可能有所不同。  Microsoft Query 程序（随 Visual C\+\+ 1.5 版本分布）是一种发现可用于数据源的字段类型的办法。  在 Microsoft Query 中，单击**“文件”**，单击**“表定义”**，从数据源中选择一个表，然后查看**“类型”**组合框中显示的类型。  也有创建索引的 SQL 语法。  
  
## 请参阅  
 [数据源 \(ODBC\)](../../data/odbc/data-source-odbc.md)