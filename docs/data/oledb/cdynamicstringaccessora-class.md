---
title: "CDynamicStringAccessorA 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDynamicStringAccessorA"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDynamicStringAccessorA 类"
ms.assetid: ed0d9821-a655-41f1-a902-43c3042ac49c
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CDynamicStringAccessorA 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

可以访问数据源时，可以在不了解数据库架构 \(基础结构\)。  
  
## 语法  
  
```  
typedef CDynamicStringAccessorT<CHAR, DBTYPE_STR> CDynamicStringAccessorA;  
```  
  
## 备注  
 这些请求提供程序获取从数据存储访问的所有数据都以字符串数据，`CDynamicStringAccessor`，但请求 ANSI 字符串数据。  
  
 `CDynamicStringAccessorA` 继承 **GetString** 从 `CDynamicStringAccessor`和 `SetString`。  当您使用时在 `CDynamicStringAccessorA` 调用这些方法，***BaseType*** 对象是 **CHAR**。  
  
## 要求  
 **标题**:atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor 类](../../data/oledb/caccessor-class.md)   
 [CDynamicParameterAccessor 类](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [CManualAccessor 类](../../data/oledb/cmanualaccessor-class.md)   
 [CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicStringAccessor 类](../../data/oledb/cdynamicstringaccessor-class.md)