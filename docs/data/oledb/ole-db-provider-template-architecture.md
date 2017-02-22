---
title: "OLE DB 提供程序模板体系结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "体系结构 [C++], OLE DB 提供程序"
  - "OLE DB [C++], 对象模型"
  - "OLE DB 提供程序模板, 对象模型"
ms.assetid: 639304a3-f9e0-44dc-8d0c-0ebd2455b363
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# OLE DB 提供程序模板体系结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## 数据源和会话  
 OLE DB 提供程序结构包括一个数据源对象和一个或多个会话。  数据源对象是每个提供程序必须实例化的初始对象。  当使用者应用程序需要数据时，它创建数据源对象以启动提供程序。  数据源对象（使用 **IDBCreateSession** 接口）创建使用者用来连接到数据源对象的会话对象。  ODBC 程序员可以将数据源对象看成等效于 **HENV**，将会话对象看成等效于 **HDBC**。  
  
 ![提供程序体系结构](../../data/oledb/media/vc4twb1.gif "vc4TWB1")  
  
 OLE DB 模板与“OLE DB 提供程序向导”创建的源文件一起实现数据源对象。  会话是对应于 OLE DB **TSession** 的对象。  
  
## 强制接口和可选接口  
 OLE DB 提供程序模板为您提供了所有必需接口的预封装实现。  OLE DB 为若干对象类型定义了强制和可选接口：  
  
-   [数据源](../../data/oledb/data-source-object-interfaces.md)  
  
-   [会话](../../data/oledb/session-object-interfaces.md)  
  
-   [行集合](../../data/oledb/rowset-object-interfaces.md)  
  
-   [命令](../../data/oledb/command-object-interfaces.md)  
  
-   [事务](../../data/oledb/transaction-object-interfaces.md)  
  
 注意 OLE DB 提供程序模板不实现行对象和存储对象。  
  
 根据 [OLE DB 2.6 SDK 文档](https://msdn.microsoft.com/en-us/library/ms722784.aspx)，下表列出了上述对象的强制和可选接口。  
  
|组件|接口|注释|  
|--------|--------|--------|  
|[数据源](../../data/oledb/data-source-object-interfaces.md) \([CDataSource](../../data/oledb/cdatasource-class.md)\)|\[强制\] **IDBCreateSession**<br /><br /> \[强制\] **IDBInitialize**<br /><br /> \[强制\] `IDBProperties`<br /><br /> \[强制\] `IPersist`<br /><br /> \[可选\] **IConnectionPointContainer**<br /><br /> \[可选\] **IDBAsynchStatus**<br /><br /> \[可选\] **IDBDataSourceAdmin**<br /><br /> \[可选\] **IDBInfo**<br /><br /> \[可选\] `IPersistFile`<br /><br /> \[可选\] **ISupportErrorInfo**|从使用者到提供程序的连接。  此对象用于指定有关连接的属性，如用户 ID、密码和数据源名称。  此对象也可以用于管理数据源（创建、更新、删除、表等）。|  
|[会话](../../data/oledb/session-object-interfaces.md) \([CSession](../../data/oledb/cdataconnection-operator-csession-amp.md)\)|\[强制\] **IGetDataSource**<br /><br /> \[强制\] `IOpenRowset`<br /><br /> \[强制\] **ISessionProperties**<br /><br /> \[可选\] **IAlterIndex**<br /><br /> \[可选\] **IAlterTable**<br /><br /> \[可选\] **IBindResource**<br /><br /> \[可选\] **ICreateRow**<br /><br /> \[可选\] **IDBCreateCommand**<br /><br /> \[可选\] **IDBSchemaRowset**<br /><br /> \[可选\] **IIndexDefinition**<br /><br /> \[可选\] **ISupportErrorInfo**<br /><br /> \[可选\] **ITableCreation**<br /><br /> \[可选\] **ITableDefinition**<br /><br /> \[可选\] **ITableDefinitionWithConstraints**<br /><br /> \[可选\] **ITransaction**<br /><br /> \[可选\] **ITransactionJoin**<br /><br /> \[可选\] **ITransactionLocal**<br /><br /> \[可选\] **ITransactionObject**|会话对象表示使用者和提供程序之间的单个对话。  它有些类似于 ODBC **HSTMT**，因为可以有许多同时活动的会话。<br /><br /> 会话对象是到达 OLE DB 功能的主链接。  为到达命令、事务或行集合对象，需要经过会话对象。|  
|[行集合](../../data/oledb/rowset-object-interfaces.md) \([CRowset](../../data/oledb/crowset-class.md)\)|\[强制\] `IAccessor`<br /><br /> \[强制\] `IColumnsInfo`<br /><br /> \[强制\] **IConvertType**<br /><br /> \[强制\] `IRowset`<br /><br /> \[强制\] `IRowsetInfo`<br /><br /> \[可选\] **IChapteredRowset**<br /><br /> \[可选\] **IColumnsInfo2**<br /><br /> \[可选\] **IColumnsRowset**<br /><br /> \[可选\] **IConnectionPointContainer**<br /><br /> \[可选\] **IDBAsynchStatus**<br /><br /> \[可选\] **IGetRow**<br /><br /> \[可选\] `IRowsetChange`<br /><br /> \[可选\] **IRowsetChapterMember**<br /><br /> \[可选\] **IRowsetCurrentIndex**<br /><br /> \[可选\] **IRowsetFind**<br /><br /> \[可选\] **IRowsetIdentity**<br /><br /> \[可选\] **IRowsetIndex**<br /><br /> \[可选\] `IRowsetLocate`<br /><br /> \[可选\] **IRowsetRefresh**<br /><br /> \[可选\] `IRowsetScroll`<br /><br /> \[可选\] `IRowsetUpdate`<br /><br /> \[可选\] **IRowsetView**<br /><br /> \[可选\] **ISupportErrorInfo**<br /><br /> \[可选\] **IRowsetBookmark**|行集合对象表示来自数据源的数据。  此对象负责这些数据的绑定和数据上的任何基本操作（更新、获取、移动，等等）。  始终有一个行集合对象包含和操作数据。|  
|[命令](../../data/oledb/command-object-interfaces.md) \([CCommand](http://msdn.microsoft.com/zh-cn/52bef5da-c1a0-4223-b4e6-9e464b6db409)\)|\[强制\] `IAccessor`<br /><br /> \[强制\] `IColumnsInfo`<br /><br /> \[强制\] `ICommand`<br /><br /> \[强制\] **ICommandProperties**<br /><br /> \[强制\] `ICommandText`<br /><br /> \[强制\] **IConvertType**<br /><br /> \[可选\] **IColumnsRowset**<br /><br /> \[可选\] **ICommandPersist**<br /><br /> \[可选\] **ICommandPrepare**<br /><br /> \[可选\] `ICommandWithParameters`<br /><br /> \[可选\] **ISupportErrorInfo**<br /><br /> \[可选\] **ICommandStream**|命令对象处理数据上的操作，如查询。  它可以处理参数化语句或非参数化语句。<br /><br /> 命令对象也负责处理参数和输出列的绑定。  绑定是包含有关如何在行集合中检索列的信息的结构。  它包含序号、数据类型、长度、状态等信息。|  
|[事务](../../data/oledb/transaction-object-interfaces.md)（可选）|\[强制\] **IConnectionPointContainer**<br /><br /> \[强制\] **ITransaction**<br /><br /> \[可选\] **ISupportErrorInfo**|事务对象定义数据源上的原子工作单元并确定这些工作单元如何相关。  此对象不直接受 OLE DB 提供程序模板的支持（即您创建自己的对象）。|  
  
 有关详细信息，请参见下列主题：  
  
-   [属性映射](../../data/oledb/property-maps.md)  
  
-   [用户记录](../../data/oledb/user-record.md)  
  
## 请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB Interfaces](https://msdn.microsoft.com/en-us/library/ms709709.aspx)