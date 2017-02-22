---
title: "PROVIDER_COLUMN_ENTRY_GN | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PROVIDER_COLUMN_ENTRY_GN"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PROVIDER_COLUMN_ENTRY_GN 宏"
ms.assetid: be77ba85-634c-4e28-832f-d2fa40413254
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# PROVIDER_COLUMN_ENTRY_GN
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示提供程序所支持的特定列。  
  
## 语法  
  
```  
  
PROVIDER_COLUMN_ENTRY_GN (  
name  
, ordinal, flags, colSize, dbtype, precision, scale, guid )  
```  
  
#### 参数  
 *name*  
 \[in\] 列名。  
  
 `ordinal`  
 \[in\] 列数。  除非将列是书签列，列数无法为 0。  
  
 `flags`  
 \[in\] 指定数据的返回方式。  参见 [DBBINDING 结构](https://msdn.microsoft.com/en-us/library/ms716845.aspx)的 `dwFlags` 说明。  
  
 *colSize*  
 \[in\] 列的大小。  
  
 `dbtype`  
 \[in\] 指示值的数据类型。  参见 [DBBINDING 结构](https://msdn.microsoft.com/en-us/library/ms716845.aspx)的 **wType** 说明。  
  
 *precision*  
 \[in\] 精度指示何时使用 *dbType* 获取数据，如果是 `DBTYPE_NUMERIC` 或 **DBTYPE\_DECIMAL**。  参见 [DBBINDING 结构](https://msdn.microsoft.com/en-us/library/ms716845.aspx)的 **bPrecision** 说明。  
  
 `scale`  
 \[in\] 要指示缩放使用获取数据，如果 dbType 是 `DBTYPE_NUMERIC` 或 **DBTYPE\_DECIMAL**。  参见 [DBBINDING 结构](https://msdn.microsoft.com/en-us/library/ms716845.aspx)的 **bScale** 说明。  
  
 `guid`  
 架构行集的 GUID。  用于架构行集及其的 GUID 列表查看 *OLE DB 程序员参考》\) 中的*[IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx)。  
  
## 备注  
 可以指定列的大小、数据类型、精度、小数位数和架构行集的 GUID。  
  
## 要求  
 **页眉：** atldb.h  
  
## 请参阅  
 [OLE DB 提供程序模板宏](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)   
 [创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)