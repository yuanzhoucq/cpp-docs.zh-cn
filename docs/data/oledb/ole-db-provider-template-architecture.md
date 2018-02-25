---
title: "OLE DB 提供程序模板体系结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB [C++], object model
- architecture [C++], OLE DB Provider
- OLE DB provider templates, object model
ms.assetid: 639304a3-f9e0-44dc-8d0c-0ebd2455b363
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 122da4031eff1cacfaf3242000cbd36eb7b75356
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="ole-db-provider-template-architecture"></a>OLE DB 提供程序模板体系结构
## <a name="data-sources-and-sessions"></a>数据源和会话  
 OLE DB 提供程序体系结构包括数据源对象和一个或多个会话。 数据源对象是每个提供程序必须实例化的初始对象。 当使用者应用程序需要数据时，它并创建要启动提供程序的数据源对象。 数据源对象创建一个会话对象 (使用**IDBCreateSession**接口) 通过使用者连接到数据源对象。 ODBC 程序员可以将数据源对象视为等效于**HENV**和会话对象等效于**HDBC**。  
  
 ![提供程序体系结构](../../data/oledb/media/vc4twb1.gif "vc4twb1")  
  
 与 OLE DB 提供程序向导创建的源文件，一起 OLE DB 模板实现数据源对象。 会话是一个对象，对应于 OLE DB **TSession**。  
  
## <a name="mandatory-and-optional-interfaces"></a>强制和可选接口  
 OLE DB 提供程序模板使你预打包实现全部所需的接口。 通过 OLE DB for 几种类型的对象定义必需和可选接口：  
  
-   [数据源](../../data/oledb/data-source-object-interfaces.md)  
  
-   [会话](../../data/oledb/session-object-interfaces.md)  
  
-   [Rowset](../../data/oledb/rowset-object-interfaces.md)  
  
-   [命令](../../data/oledb/command-object-interfaces.md)  
  
-   [事务](../../data/oledb/transaction-object-interfaces.md)  
  
 请注意，OLE DB 提供程序模板不实现行和存储对象。  
  
 下表列出了必需和可选接口，上面列出的对象根据[OLE DB 2.6 SDK 文档](https://msdn.microsoft.com/en-us/library/ms722784.aspx)。  
  
|组件|接口|注释|  
|---------------|---------------|-------------|  
|[数据源](../../data/oledb/data-source-object-interfaces.md)([CDataSource](../../data/oledb/cdatasource-class.md))|[mandatory] **IDBCreateSession**<br /><br /> [mandatory] **IDBInitialize**<br /><br /> [mandatory] `IDBProperties`<br /><br /> [mandatory] `IPersist`<br /><br /> [optional] **IConnectionPointContainer**<br /><br /> [可选]**IDBAsynchStatus**<br /><br /> [optional] **IDBDataSourceAdmin**<br /><br /> [optional] **IDBInfo**<br /><br /> [可选] `IPersistFile`<br /><br /> [可选]**ISupportErrorInfo**|从使用者到提供程序的连接。 对象用于指定用户 ID、 密码和数据源名称等连接上的属性。 对象还可以用于管理数据源 （创建、 更新、 删除、 表和等）。|  
|[会话](../../data/oledb/session-object-interfaces.md)([CSession](../../data/oledb/cdataconnection-operator-csession-amp.md))|[mandatory] **IGetDataSource**<br /><br /> [mandatory] `IOpenRowset`<br /><br /> [必需]**ISessionProperties**<br /><br /> [可选]**IAlterIndex**<br /><br /> [可选]**IAlterTable**<br /><br /> [可选]**IBindResource**<br /><br /> [optional] **ICreateRow**<br /><br /> [optional] **IDBCreateCommand**<br /><br /> [optional] **IDBSchemaRowset**<br /><br /> [可选]**IIndexDefinition**<br /><br /> [可选]**ISupportErrorInfo**<br /><br /> [可选]**ITableCreation**<br /><br /> [可选]**ITableDefinition**<br /><br /> [可选]**ITableDefinitionWithConstraints**<br /><br /> [可选]**Itransaction::**<br /><br /> [可选]**ITransactionJoin**<br /><br /> [optional] **ITransactionLocal**<br /><br /> [optional] **ITransactionObject**|会话对象表示使用者和提供程序之间的单个对话。 它是某种程度上类似于 ODBC **HSTMT**在于可以有多个同时会话处于活动状态。<br /><br /> 会话对象是主链接以获取对 OLE DB 功能。 若要获得命令、 事务或行集对象，则翻会话对象。|  
|[Rowset](../../data/oledb/rowset-object-interfaces.md) ([CRowset](../../data/oledb/crowset-class.md))|[mandatory] `IAccessor`<br /><br /> [mandatory] `IColumnsInfo`<br /><br /> [mandatory] **IConvertType**<br /><br /> [mandatory] `IRowset`<br /><br /> [mandatory] `IRowsetInfo`<br /><br /> [可选]**IChapteredRowset**<br /><br /> [可选]**IColumnsInfo2**<br /><br /> [optional] **IColumnsRowset**<br /><br /> [optional] **IConnectionPointContainer**<br /><br /> [可选]**IDBAsynchStatus**<br /><br /> [可选]**IGetRow**<br /><br /> [可选] `IRowsetChange`<br /><br /> [可选]**IRowsetChapterMember**<br /><br /> [optional] **IRowsetCurrentIndex**<br /><br /> [optional] **IRowsetFind**<br /><br /> [optional] **IRowsetIdentity**<br /><br /> [optional] **IRowsetIndex**<br /><br /> [可选] `IRowsetLocate`<br /><br /> [optional] **IRowsetRefresh**<br /><br /> [可选] `IRowsetScroll`<br /><br /> [可选] `IRowsetUpdate`<br /><br /> [可选]**IRowsetView**<br /><br /> [可选]**ISupportErrorInfo**<br /><br /> [optional] **IRowsetBookmark**|行集合对象表示从数据源的数据。 该对象负责该数据和对数据的任何基本操作 （更新、 提取、 移动和其他） 的绑定。 你始终可以用于包含和操作数据的行集的对象。|  
|[命令](../../data/oledb/command-object-interfaces.md)([CCommand](http://msdn.microsoft.com/en-us/52bef5da-c1a0-4223-b4e6-9e464b6db409))|[mandatory] `IAccessor`<br /><br /> [mandatory] `IColumnsInfo`<br /><br /> [mandatory] `ICommand`<br /><br /> [必需]**ICommandProperties**<br /><br /> [mandatory] `ICommandText`<br /><br /> [mandatory] **IConvertType**<br /><br /> [optional] **IColumnsRowset**<br /><br /> [可选]**ICommandPersist**<br /><br /> [可选]**ICommandPrepare**<br /><br /> [可选] `ICommandWithParameters`<br /><br /> [可选]**ISupportErrorInfo**<br /><br /> [可选]**ICommandStream**|命令对象处理如查询的数据上的操作。 它可以处理参数化或非参数化语句。<br /><br /> 命令对象程序还负责处理为参数和输出列的绑定。 绑定是，包含有关应如何检索列中的，在行集中，信息的结构。 它包含如序号、 数据类型、 长度和状态的信息。|  
|[事务](../../data/oledb/transaction-object-interfaces.md)（可选）|[mandatory] **IConnectionPointContainer**<br /><br /> [必需]**Itransaction::**<br /><br /> [可选]**ISupportErrorInfo**|事务对象数据源上定义工作的原子单元，并确定每个这些工作单元之间的关系。 OLE DB 提供程序模板不直接支持此对象 （即，创建你自己的对象）。|  
  
 有关详细信息，请参阅下列主题：  
  
-   [属性映射](../../data/oledb/property-maps.md)  
  
-   [用户记录](../../data/oledb/user-record.md)  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 接口](https://msdn.microsoft.com/en-us/library/ms709709.aspx)