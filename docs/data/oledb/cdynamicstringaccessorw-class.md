---
title: "CDynamicStringAccessorW 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDynamicStringAccessorW"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDynamicStringAccessorW 类"
ms.assetid: 9b7fd5cc-3a9b-4b57-b907-f1e35de2c98f
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicStringAccessorW 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

动态访问器使您可以在不了解数据库架构（基础结构）的情况下访问数据源。  
  
## 语法  
  
```  
typedef CDynamicStringAccessorT<WCHAR, DBTYPE_WSTR> CDynamicStringAccessorW;  
```  
  
## 备注  
 这些请求提供程序获取从数据存储访问的所有数据都以字符串数据，`CDynamicStringAccessor`，但请求 Unicode 字符串数据。  
  
 `CDynamicStringAccessorW` 继承 **GetString** 从 `CDynamicStringAccessor`和 `SetString`。  当您使用时在 `CDynamicStringAccessorW` 调用这些方法，***BaseType*** 对象是 **WCHAR**。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor 类](../../data/oledb/caccessor-class.md)   
 [CDynamicParameterAccessor 类](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [CManualAccessor 类](../../data/oledb/cmanualaccessor-class.md)   
 [CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicStringAccessor 类](../../data/oledb/cdynamicstringaccessor-class.md)