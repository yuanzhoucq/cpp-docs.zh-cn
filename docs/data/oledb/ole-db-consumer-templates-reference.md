---
title: OLE DB 使用者模板参考
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB consumer templates, classes
ms.assetid: cfc7f698-1a0e-4a09-a4d3-ccb99e6654fe
ms.openlocfilehash: 13805ab1dc2c2b4792fd05c9140006c610b42f75
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210101"
---
# <a name="ole-db-consumer-templates-reference"></a>OLE DB 使用者模板参考

OLE DB 使用者模板包含以下类。 参考资料还包括有关[OLE DB 使用者模板的宏](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)的主题。

## <a name="session-classes"></a>会话类

[CDataConnection](../../data/oledb/cdataconnection-class.md)<br/>
管理与数据源的连接。 这是一个用于创建客户端的有用类，因为它封装了必需的对象（数据源和会话）以及连接到数据源时需要执行的一些工作。

[CDataSource](../../data/oledb/cdatasource-class.md)<br/>
对应于一个 OLE DB 数据源对象，该对象表示通过提供程序到数据源的连接。 一个或多个数据库会话（每个由 `CSession` 对象表示）可在单个连接上发生。

[CEnumerator](../../data/oledb/cenumerator-class.md)<br/>
对应于一个 OLE DB 枚举器对象，该对象检索有关可用数据源的行集信息。

[CEnumeratorAccessor](../../data/oledb/cenumeratoraccessor-class.md)<br/>
由 `CEnumerator` 用来访问枚举器行集中的数据。 此行集包含当前枚举器中可见的数据源和枚举器。

[CSession](../../data/oledb/csession-class.md)<br/>
表示单个数据库访问会话。 一个或多个会话可以与每个 `CDataSource` 对象相关联。

## <a name="accessor-classes"></a>访问器类

[CAccessor](../../data/oledb/caccessor-class.md)<br/>
用于静态绑定到数据源的记录。 如果知道数据源的结构，请使用此访问器类。

[CAccessorBase](../../data/oledb/caccessorbase-class.md)<br/>
所有访问器类的基类。

[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)<br/>
可在运行时根据行集的列信息创建的访问器。 如果不知道数据源的结构，请使用此类检索数据。

[CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
可在命令类型未知时使用的访问器。 如果访问接口支持接口，则通过调用 `ICommandWithParameters` 接口获取参数信息。

[CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
当您不知道数据库的基础结构时，允许您访问数据源。

[CDynamicStringAccessorA](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
与 `CDynamicStringAccessor` 类似，不同之处在于此类请求将数据从数据存储区作为 ANSI 字符串数据进行访问。

[CDynamicStringAccessorW](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
与 `CDynamicStringAccessor` 类似，不同之处在于此类请求将数据从数据存储区作为 UNICODE 字符串数据进行访问。

[CManualAccessor](../../data/oledb/cmanualaccessor-class.md)<br/>
具有处理列和命令参数的方法的访问器。 使用此类，只要提供程序可以转换类型，就可以使用任何数据类型。

[CNoAccessor](../../data/oledb/cnoaccessor-class.md)<br/>
当您不希望类支持参数或输出列时，可以将用作模板参数。

[CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)<br/>
与 `CDynamicStringAccessor` 类似，只不过此类会将从数据存储访问的所有数据都转换为 XML 格式（标记）的数据。

## <a name="rowset-classes"></a>行集类

[CAccessorRowset](../../data/oledb/caccessorrowset-class.md)<br/>
封装行集及其关联的访问器。

[CArrayRowset](../../data/oledb/carrayrowset-class.md)<br/>
用于使用数组语法访问行集的元素。

[CBulkRowset](../../data/oledb/cbulkrowset-class.md)<br/>
用于通过单个调用检索多个行句柄，批量提取和操作行。

[CNoRowset](../../data/oledb/cnorowset-class.md)<br/>
如果命令不返回行集，则可将其用作模板参数。

[CRestrictions](../../data/oledb/crestrictions-class.md)<br/>
用于指定架构行集的限制。

[CRowset](../../data/oledb/crowset-class.md)<br/>
用于操作、设置和检索行集数据。

[CStreamRowset](../../data/oledb/cstreamrowset-class.md)<br/>
返回 `ISequentialStream` 对象，而不是行集;然后，使用 `Read` 方法以 XML 格式检索数据。 （SQL Server 2000 格式设置; 请注意，此功能仅适用于 SQL Server 2000。）

[IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md)<br/>
为 `IRowsetNotify`提供了虚拟实现，`IRowsetNotify` 方法使用空函数 `OnFieldChange`、`OnRowChange`和 `OnRowsetChange`。

[架构行集类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)

OLE DB 模板为您提供了一组与 OLE DB 架构行集相对应的类。

## <a name="command-classes"></a>命令类

[CCommand](../../data/oledb/ccommand-class.md)<br/>
用于设置和执行基于参数的 OLE DB 命令。 若要仅打开一个简单的行集，请改用 `CTable`。

[CMultipleResults](../../data/oledb/cmultipleresults-class.md)<br/>
当你希望命令处理多个结果集时，用作 `CCommand` 模板的模板参数。

[CNoAccessor](../../data/oledb/cnoaccessor-class.md)<br/>
用作模板类的模板参数，如 `CCommand` 和 `CTable`，它采用访问器类参数。 如果你不希望类支持参数或输出列，请使用 `CNoAccessor`。

[CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md)<br/>
当你希望命令处理单个行集时，用作 `CCommand` 模板的模板参数。 `CNoMultipleResults` 是模板参数的默认值。

[CNoRowset](../../data/oledb/cnorowset-class.md)<br/>
用作 `CCommand` 的模板参数，如果命令或表未返回行集，则为 `CTable`。

[CTable](../../data/oledb/ctable-class.md)<br/>
用于访问没有参数的简单行集。

## <a name="property-classes"></a>属性类

[CDBPropIDSet](../../data/oledb/cdbpropidset-class.md)<br/>
用于传递使用者需要其属性信息的属性 Id 的数组。 属性属于一个属性集。

[CDBPropSet](../../data/oledb/cdbpropset-class.md)<br/>
用于设置提供程序的属性。

## <a name="bookmark-class"></a>Bookmark 类

[CBookmark](../../data/oledb/cbookmark-class.md)<br/>
用作访问行集中的数据的索引。

## <a name="error-class"></a>Error 类

[CDBErrorInfo](../../data/oledb/cdberrorinfo-class.md)<br/>
用于检索 OLE DB 错误信息。

## <a name="see-also"></a>另请参阅

[OLE DB 提供程序模板参考](../../data/oledb/ole-db-provider-templates-reference.md)<br/>
[OLE DB 模板](../../data/oledb/ole-db-templates.md)
