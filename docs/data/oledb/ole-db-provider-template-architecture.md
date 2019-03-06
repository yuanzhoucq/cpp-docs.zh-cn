---
title: OLE DB 提供程序模板体系结构
ms.date: 11/19/2018
helpviewer_keywords:
- OLE DB [C++], object model
- architecture [C++], OLE DB Provider
- OLE DB provider templates, object model
ms.assetid: 639304a3-f9e0-44dc-8d0c-0ebd2455b363
ms.openlocfilehash: b6d177d793451b7c5e9c19f6d40add973a627d60
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422996"
---
# <a name="ole-db-provider-template-architecture"></a>OLE DB 提供程序模板体系结构

## <a name="data-sources-and-sessions"></a>数据源和会话

OLE DB 提供程序体系结构包括数据源对象和一个或多个会话。 数据源对象是每个提供程序必须实例化的初始对象。 当使用者应用程序需要数据时，它共同创建要启动该提供程序的数据源对象。 数据源对象创建一个会话对象 (使用`IDBCreateSession`接口) 通过它使用者连接到数据源对象。 ODBC 程序员可以将数据源对象视为等效于`HENV`和会话对象等效于`HDBC`。

![提供程序体系结构](../../data/oledb/media/vc4twb1.gif "提供程序体系结构")

与创建的源文件一起**OLE DB 提供程序向导**，OLE DB 模板实现数据源对象。 会话是一个对象，对应于 OLE DB `TSession`。

## <a name="mandatory-and-optional-interfaces"></a>必需和可选接口

OLE DB 提供程序模板提供预打包实现所有所需的接口。 通过 OLE DB for 多种类型的对象定义必需和可选接口：

- [数据源](../../data/oledb/data-source-object-interfaces.md)

- [会话](../../data/oledb/session-object-interfaces.md)

- [Rowset](../../data/oledb/rowset-object-interfaces.md)

- [命令](../../data/oledb/command-object-interfaces.md)

- [事务](../../data/oledb/transaction-object-interfaces.md)

OLE DB 提供程序模板不会实现的行和存储对象。

下表列出了必需和可选接口，上面列出的对象根据[OLE DB 2.6 SDK 文档](/previous-versions/windows/desktop/ms722784(v=vs.85))。

|组件|接口|注释|
|---------------|---------------|-------------|
|[数据源](../../data/oledb/data-source-object-interfaces.md)([CDataSource](../../data/oledb/cdatasource-class.md))|[mandatory] `IDBCreateSession`<br /><br /> [mandatory] `IDBInitialize`<br /><br /> [mandatory] `IDBProperties`<br /><br /> [mandatory] `IPersist`<br /><br /> [optional] `IConnectionPointContainer`<br /><br /> [optional] `IDBAsynchStatus`<br /><br /> [optional] `IDBDataSourceAdmin`<br /><br /> [optional] `IDBInfo`<br /><br /> [optional] `IPersistFile`<br /><br /> [optional] `ISupportErrorInfo`|与提供程序从使用者连接。 该对象用于指定用户 ID、 密码和数据源名称等连接上的属性。 该对象还可以用来管理数据源 （创建、 更新、 删除表，等）。|
|[会话](../../data/oledb/session-object-interfaces.md)([CSession](../../data/oledb/cdataconnection-operator-csession-amp.md))|[mandatory] `IGetDataSource`<br /><br /> [mandatory] `IOpenRowset`<br /><br /> [mandatory] `ISessionProperties`<br /><br /> [optional] `IAlterIndex`<br /><br /> [optional] `IAlterTable`<br /><br /> [optional] `IBindResource`<br /><br /> [optional] `ICreateRow`<br /><br /> [optional] `IDBCreateCommand`<br /><br /> [optional] `IDBSchemaRowset`<br /><br /> [optional] `IIndexDefinition`<br /><br /> [optional] `ISupportErrorInfo`<br /><br /> [optional] `ITableCreation`<br /><br /> [optional] `ITableDefinition`<br /><br /> [optional] `ITableDefinitionWithConstraints`<br /><br /> [optional] `ITransaction`<br /><br /> [optional] `ITransactionJoin`<br /><br /> [optional] `ITransactionLocal`<br /><br /> [optional] `ITransactionObject`|会话对象是使用者和提供程序之间的单个对话。 它是类似于 ODBC `HSTMT` ，可以有多个同时会话活动。<br /><br /> 会话对象是主链接以获取对 OLE DB 功能。 若要进入命令、 事务或行集对象，则翻会话对象。|
|[Rowset](../../data/oledb/rowset-object-interfaces.md) ([CRowset](../../data/oledb/crowset-class.md))|[mandatory] `IAccessor`<br /><br /> [mandatory] `IColumnsInfo`<br /><br /> [mandatory] `IConvertType`<br /><br /> [mandatory] `IRowset`<br /><br /> [mandatory] `IRowsetInfo`<br /><br /> [optional] `IChapteredRowset`<br /><br /> [optional] `IColumnsInfo2`<br /><br /> [optional] `IColumnsRowset`<br /><br /> [optional] `IConnectionPointContainer`<br /><br /> [optional] `IDBAsynchStatus`<br /><br /> [optional] `IGetRow`<br /><br /> [optional] `IRowsetChange`<br /><br /> [optional] `IRowsetChapterMember`<br /><br /> [optional] `IRowsetCurrentIndex`<br /><br /> [optional] `IRowsetFind`<br /><br /> [optional] `IRowsetIdentity`<br /><br /> [optional] `IRowsetIndex`<br /><br /> [optional] `IRowsetLocate`<br /><br /> [optional] `IRowsetRefresh`<br /><br /> [optional] `IRowsetScroll`<br /><br /> [optional] `IRowsetUpdate`<br /><br /> [optional] `IRowsetView`<br /><br /> [optional] `ISupportErrorInfo`<br /><br /> [optional] `IRowsetBookmark`|行集对象是从数据源的数据。 该对象用于该数据和对数据的任何基本操作 （更新、 fetch、 移动和其他人） 的绑定。 始终具有一个行集对象来保留和处理数据。|
|[命令](../../data/oledb/command-object-interfaces.md)([CCommand](ccommand-class.md))|[mandatory] `IAccessor`<br /><br /> [mandatory] `IColumnsInfo`<br /><br /> [mandatory] `ICommand`<br /><br /> [mandatory] `ICommandProperties`<br /><br /> [mandatory] `ICommandText`<br /><br /> [mandatory] `IConvertType`<br /><br /> [optional] `IColumnsRowset`<br /><br /> [optional] `ICommandPersist`<br /><br /> [optional] `ICommandPrepare`<br /><br /> [optional] `ICommandWithParameters`<br /><br /> [optional] `ISupportErrorInfo`<br /><br /> [optional] `ICommandStream`|命令对象处理数据，例如查询上的操作。 它可以处理参数化或非参数化语句。<br /><br /> 命令对象也是负责处理参数和输出列的绑定的。 绑定是包含有关应如何检索行集中的列信息的结构。 它包含如序号、 数据类型、 长度和状态信息。|
|[事务](../../data/oledb/transaction-object-interfaces.md)（可选）|[mandatory] `IConnectionPointContainer`<br /><br /> [mandatory] `ITransaction`<br /><br /> [optional] `ISupportErrorInfo`|事务对象上的数据源定义原子工作单元，并确定每个这些工作单元之间的关系。 OLE DB 提供程序模板不直接支持此对象 （即，创建你自己的对象）。|

有关详细信息，请参阅下列主题：

- [属性映射](../../data/oledb/property-maps.md)

- [用户记录](../../data/oledb/user-record.md)

## <a name="see-also"></a>请参阅

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 接口](/previous-versions/windows/desktop/ms709709(v=vs.85))<br/>
