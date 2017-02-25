---
title: "SCHEMA_ENTRY | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SCHEMA_ENTRY"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SCHEMA_ENTRY 宏"
ms.assetid: e8bee479-80f3-417e-8f41-cdaddd49690c
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# SCHEMA_ENTRY
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

关联 GUID 与类。  
  
## 语法  
  
```  
  
      SCHEMA_ENTRY(  
   guid,  
   rowsetClass   
);   
```  
  
#### 参数  
 `guid`  
 架构行集的 GUID。  用于架构行集及其的 GUID 列表查看 *OLE DB 程序员参考》\) 中的*[IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx)。  
  
 *rowsetClass*  
 将创建表示架构行集合的类。  
  
## 备注  
 可以[IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md) 然后查询 GUID 列表的映射，也可以创建一行集合，则赋予它一 GUID。  架构行集 `IDBSchemaRowsetImpl` 创建类似于标准 `CRowsetImpl`派生类，除此之外，它必须提供方法的 **执行** 具有以下签名：  
  
 `HRESULT Execute (LONG* pcRowsAffected, ULONG cRestrictions,`  
  
 `const VARIANT* rgRestrictions)`  
  
 此 **执行** 函数填充：，其中填充行集合中的数据。  ATL 项目向导创建，如 *OLE DB 程序员参考》\) 中的*[IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) 所述，三最初的架构行集合。三个必需的架构 OLE DB 中的每个项目：  
  
-   `DBSCHEMA_TABLES`  
  
-   **DBSCHEMA\_COLUMNS**  
  
-   **DBSCHEMA\_PROVIDER\_TYPES**  
  
 向导还将架构映射的三个对应的项。  参见 [创建 OLE DB 提供程序模板](../../data/oledb/creating-an-ole-db-provider.md) 有关使用更多向导的信息创建提供程序。  
  
## 要求  
 **页眉：** atldb.h  
  
## 请参阅  
 [OLE DB 提供程序模板宏](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [BEGIN\_SCHEMA\_MAP](../../data/oledb/begin-schema-map.md)   
 [END\_SCHEMA\_MAP](../../data/oledb/end-schema-map.md)