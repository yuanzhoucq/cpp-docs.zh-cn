---
title: "CMyProviderSession (MyProviderSess.H) | Microsoft Docs"
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
  - "cmyprovidersession"
  - ""myprovidersess.h""
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MyProviderSess.H 中的 CMyProviderSession 类"
  - "OLE DB 提供程序, 向导生成的文件"
ms.assetid: d37ad471-cf05-49c5-aa47-cd10824d777f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMyProviderSession (MyProviderSess.H)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

MyProviderSess.H 包含 OLE DB 会话对象的声明和实现。  数据源对象创建会话对象，表示使用者和提供程序之间的对话。  可以为一个数据源打开多个同时会话。  `CMyProviderSession` 的继承列表如下：  
  
```  
/////////////////////////////////////////////////////////////////////////  
// CMyProviderSession  
class ATL_NO_VTABLE CMyProviderSession :   
   public CComObjectRootEx<CComSingleThreadModel>,  
   public IGetDataSourceImpl<CMyProviderSession>,  
   public IOpenRowsetImpl<CMyProviderSession>,  
   public ISessionPropertiesImpl<CMyProviderSession>,  
   public IObjectWithSiteSessionImpl<CMyProviderSession>,  
   public IDBSchemaRowsetImpl<CMyProviderSession>,  
   public IDBCreateCommandImpl<CMyProviderSession, CMyProviderCommand>  
```  
  
 会话对象从 **IGetDataSource**、`IOpenRowset`、**ISessionProperties** 和 **IDBCreateCommand** 继承。  **IGetDataSource** 接口允许会话检索创建它的数据源。  如果需要从创建的数据源获取属性或数据源可以提供的其他信息，这很有用。  **ISessionProperties** 接口处理会话的所有属性。  `IOpenRowset` 和 **IDBCreateCommand** 接口用于做数据库工作。  如果提供程序支持命令，它将实现 **IDBCreateCommand** 接口。  它用于创建可以执行命令的命令对象。  提供程序总是实现 `IOpenRowset` 对象。  它用于从提供程序生成简单行集合。  它是来自提供程序的默认行集合（例如，`"select * from mytable"`）。  
  
 向导还生成三个会话类：`CMyProviderSessionColSchema`、`CMyProviderSessionPTSchema` 和 `CMyProviderSessionTRSchema`。  这些会话用于架构行集合。  架构行集合允许提供程序将元数据返回给使用者，而使用者不必执行查询或获取数据。  获取元数据可以比发现提供程序功能快得多。  
  
 OLE DB 规范要求实现 **IDBSchemaRowset** 接口的提供程序支持三种架构行集合类型：**DBSCHEMA\_COLUMNS**、**DBSCHEMA\_PROVIDER\_TYPES** 和 `DBSCHEMA_TABLES`。  向导为每个架构行集合生成实现。  向导生成的每个类都包含 `Execute` 方法。  在此 `Execute` 方法中，可以向提供程序返回有关支持哪些表、列和数据类型的数据。  此数据通常在编译时是已知的。  
  
## 请参阅  
 [提供程序向导生成的文件](../../data/oledb/provider-wizard-generated-files.md)