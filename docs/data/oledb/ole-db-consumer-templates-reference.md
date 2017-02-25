---
title: "OLE DB 使用者模板参考 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-attr.db_param"
  - "vc-attr.db_column"
  - "vc-attr.db_accessor"
  - "vc-attr.db_command"
  - "vc-attr.db_table"
  - "vc.templates.ole"
  - "vc-attr.db_source"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE DB 使用者模板, 类"
ms.assetid: cfc7f698-1a0e-4a09-a4d3-ccb99e6654fe
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# OLE DB 使用者模板参考
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OLE DB 使用者模板包含以下类。  还包含参考信息的主题。[OLE DB 使用者模板的宏](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)  
  
## 会话类  
 [CDataConnection](../../data/oledb/cdataconnection-class.md)  
 管理与数据源的连接。  这是创建客户端的一种有用类封装，因为它需要所需完成，则连接到数据源后 \(数据源和会话\) 和某些工作。  
  
 [CDataSource](../../data/oledb/cdatasource-class.md)  
 对应于 OLE DB 数据源对象，表示通过提供程序连接到数据源。  一个或多个会话对象表示数据库，`CSession` 中的每一个，在一台可以连接在运行。  
  
 [CEnumerator](../../data/oledb/cenumerator-class.md)  
 对应于 OLE DB 枚举器对象，以检索有关可用数据源中行集信息。  
  
 [CEnumeratorAccessor](../../data/oledb/cenumeratoraccessor-class.md)  
 用于 `CEnumerator` 枚举访问器从行集合中的数据。  此行集合包括数据源并枚举器显示从当前枚举器。  
  
 [CSession](../../data/oledb/csession-class.md)  
 表示单个数据库访问会话。  一个或多个会话可以与每个 `CDataSource` 对象。  
  
## 访问器类  
 [CAccessor](../../data/oledb/caccessor-class.md)  
 用于静态绑定到数据源中的记录。  在您知道数据源的结构时，使用此访问器类。  
  
 [CAccessorBase](../../data/oledb/caccessorbase-class.md)  
 所有访问器类的基类。  
  
 [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)  
 可以在运行时创建的一个访问器，该行集合的列信息。  如果不知道数据源的结构，请使用此类检索数据。  
  
 [CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md)  
 可以使用访问器，该命令类型未知。  通过调用 `ICommandWithParameters` 接口获取参数信息，如果提供程序支持接口。  
  
 [CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md)  
 在不了解数据库的基础结构时，可以访问数据源。  
  
 [CDynamicStringAccessorA](../../data/oledb/cdynamicstringaccessora-class.md)  
 类似于 `CDynamicStringAccessor`，只不过该类会从数据存储访问数据 ANSI 字符串形式的数据。  
  
 [CDynamicStringAccessorW](../../data/oledb/cdynamicstringaccessorw-class.md)  
 类似于 `CDynamicStringAccessor`，只不过该类会从数据存储访问的数据为 UNICODE 字符串数据。  
  
 [CManualAccessor](../../data/oledb/cmanualaccessor-class.md)  
 与处理列和命令参数方法的一个访问器。  此类，只要，提供程序可以转换类型，则可以使用任何数据类型。  
  
 [CNoAccessor](../../data/oledb/cnoaccessor-class.md)  
 当不希望类支持参数或输出列时，将用作模板参数。  
  
 [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)  
 类似于 `CDynamicStringAccessor`，只不过此类从数据存储访问的所有数据都转换为 XML 格式的 \(即带标记的\) 数据。  
  
## 行集合类  
 [CAccessorRowset](../../data/oledb/caccessorrowset-class.md)  
 封装行集及其关联访问器。  
  
 [CArrayRowset](../../data/oledb/carrayrowset-class.md)  
 可以使用数组语法，用于访问行集合的元素。  
  
 [CBulkRowset](../../data/oledb/cbulkrowset-class.md)  
 用于通过以下方法检索具有唯一调用的多个行句柄和操作批量取行。  
  
 [CNoRowset](../../data/oledb/cnorowset-class.md)  
 如果命令不返回行集，将用作模板参数。  
  
 [CRestrictions](../../data/oledb/crestrictions-class.md)  
 用于架构行集指定限制。  
  
 [CRowset](../../data/oledb/crowset-class.md)  
 用于操作，设置和检索数据行集。  
  
 [CStreamRowset](../../data/oledb/cstreamrowset-class.md)  
 返回 `ISequentialStream` 对象而不是行集合；然后使用 **读取** 方法检索 XML 格式的数据。\(SQL Server 2000 执行格式；请注意此功能仅适用于 SQL Server 2000 一起使用。\)  
  
 [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md)  
 为 `IRowsetNotify`提供一条假的实现，其中 `IRowsetNotify` 方法的 `OnFieldChange`、`OnRowChange`和 `OnRowsetChange`函数。空  
  
 [架构行集合类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)  
  
 OLE DB 模板提供了对应于 OLE DB 架构行集合的一组类。  
  
## 命令类  
 [CCommand](../../data/oledb/ccommand-class.md)  
 用于设置并执行基于参数的 OLE DB 命令。  只是打开一个简单行集合，请使用 `CTable`。  
  
 [CMultipleResults](../../data/oledb/cmultipleresults-class.md)  
 用作模板参数。`CCommand` 模板，您想让命令处理多个结果集。  
  
 [CNoAccessor](../../data/oledb/cnoaccessor-class.md)  
 用作模板参数的模板类，如 `CCommand` 和 `CTable`，使用参数访问器类。  如果不希望类支持参数或输出列，请使用 `CNoAccessor`。  
  
 [CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md)  
 用作模板参数。`CCommand` 模板，您想让命令处理单个行集合。  `CNoMultipleResults` 是通过模板参数的默认值。  
  
 [CNoRowset](../../data/oledb/cnorowset-class.md)  
 用作模板参数为 `CCommand` 或 `CTable`，则命令或表不返回行集合。  
  
 [CTable](../../data/oledb/ctable-class.md)  
 用于访问简单行集的不带任何参数。  
  
## 属性类  
 [CDBPropIDSet](../../data/oledb/cdbpropidset-class.md)  
 用于将数组使用者需要属性信息的属性 ID。  属性属于一属性。  
  
 [CDBPropSet](../../data/oledb/cdbpropset-class.md)  
 用于设置提供程序的属性。  
  
## 书签类  
 [CBookmark](../../data/oledb/cbookmark-class.md)  
 用作索引用于访问数据行集合中  
  
## 错误类别  
 [CDBErrorInfo](../../data/oledb/cdberrorinfo-class.md)  
 用于检索 OLE DB 错误信息。  
  
## 请参阅  
 [OLE DB 提供程序模板参考](../../data/oledb/ole-db-provider-templates-reference.md)   
 [OLE DB 模板](../../data/oledb/ole-db-templates.md)