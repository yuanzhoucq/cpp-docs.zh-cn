---
title: OLE DB 使用者模板参考 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- vc-attr.db_param
- vc-attr.db_column
- vc-attr.db_accessor
- vc-attr.db_command
- vc-attr.db_table
- vc.templates.ole
- vc-attr.db_source
dev_langs:
- C++
helpviewer_keywords:
- OLE DB consumer templates, classes
ms.assetid: cfc7f698-1a0e-4a09-a4d3-ccb99e6654fe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1218ddeea688299578ce046f58229f4a6a0cf5a1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059012"
---
# <a name="ole-db-consumer-templates-reference"></a>OLE DB 使用者模板参考

OLE DB 使用者模板包含以下类。 参考资料也包括在主题[OLE DB 使用者模板的宏](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)。  
  
## <a name="session-classes"></a>会话类  

[CDataConnection](../../data/oledb/cdataconnection-class.md)<br/>
管理与数据源的连接。 这是用于创建客户端，因为它封装必要的对象 （数据源和会话） 和一些操作，您需要连接到数据源时执行的操作的有用类。  
  
[CDataSource](../../data/oledb/cdatasource-class.md)<br/>
对应于 OLE DB 数据源对象，表示通过提供商连接到数据源。 一个或多个数据库会话，每个由`CSession`对象，可以在单个连接上发生。  
  
[CEnumerator](../../data/oledb/cenumerator-class.md)<br/>
对应的 OLE DB 枚举器对象，检索有关可用数据源的行集信息。  
  
[CEnumeratorAccessor](../../data/oledb/cenumeratoraccessor-class.md)<br/>
由`CEnumerator`从枚举器行集访问数据。 此行包含数据源和枚举器当前枚举器中可见。  
  
[CSession](../../data/oledb/csession-class.md)<br/>
表示单个数据库访问会话。 一个或多个会话可以与每个关联`CDataSource`对象。  
  
## <a name="accessor-classes"></a>访问器类  

[CAccessor](../../data/oledb/caccessor-class.md)<br/>
用于以静态方式绑定到数据源的记录。 当你知道数据源的结构时，请使用此访问器类。  
  
[CAccessorBase](../../data/oledb/caccessorbase-class.md)<br/>
所有访问器类的基类。  
  
[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)<br/>
取值函数可用于创建在运行时，根据在行集中的列信息。 此类用于检索数据，如果不知道数据源的结构。  
  
[CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
未知命令类型时可以使用访问器。 通过调用获取参数信息`ICommandWithParameters`接口，如果访问接口支持该接口。  
  
[CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
可以在不知道数据库的基础结构时访问数据源。  
  
[CDynamicStringAccessorA](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
类似于`CDynamicStringAccessor`不同之处在于此类请求从 ANSI 字符串数据作为数据存储区访问的数据。  
  
[CDynamicStringAccessorW](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
类似于`CDynamicStringAccessor`不同之处在于此类请求访问数据存储为 UNICODE 字符串数据中的数据。  
  
[CManualAccessor](../../data/oledb/cmanualaccessor-class.md)<br/>
取值函数方法来处理列和命令参数。 通过此类，可以使用任何数据类型，只要该提供程序可以将类型转换。  
  
[CNoAccessor](../../data/oledb/cnoaccessor-class.md)<br/>
可以用作模板自变量，如果不想要支持参数或输出列的类。  
  
[CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)<br/>
类似于`CDynamicStringAccessor`不同之处在于此类转换从数据存储为 XML 格式 （标记） 的数据访问的所有数据。  
  
## <a name="rowset-classes"></a>行集类  

[CAccessorRowset](../../data/oledb/caccessorrowset-class.md)<br/>
封装一个行集和其关联的访问器。  
  
[CArrayRowset](../../data/oledb/carrayrowset-class.md)<br/>
用于访问的行集使用数组语法元素。  
  
[CBulkRowset](../../data/oledb/cbulkrowset-class.md)<br/>
用于提取和通过检索多个行句柄，通过调用一次操作中大容量的行。  
  
[CNoRowset](../../data/oledb/cnorowset-class.md)<br/>
可以将用作模板自变量，如果该命令不返回行集。  
  
[cRestrictions](../../data/oledb/crestrictions-class.md)<br/>
使用指定的架构行集的限制。  
  
[CRowset](../../data/oledb/crowset-class.md)<br/>
用于操作、 设置和检索行集数据。  
  
[CStreamRowset](../../data/oledb/cstreamrowset-class.md)<br/>
返回`ISequentialStream`而不是行集对象; 然后，使用`Read`方法来检索 XML 格式的数据。 （SQL Server 2000 进行格式设置; 请注意，此功能适用于 SQL Server 2000 仅。）  
  
[IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md)<br/>
提供有关虚拟实现`IRowsetNotify`，具有可实现空功能`IRowsetNotify`方法`OnFieldChange`， `OnRowChange`，和`OnRowsetChange`。  
  
[架构行集类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)  
  
OLE DB 模板为您提供了一组对应的 OLE DB 架构行集的类。  
  
## <a name="command-classes"></a>命令类  

[CCommand](../../data/oledb/ccommand-class.md)<br/>
用于设置和执行基于参数的 OLE DB 命令。 若要只是打开简单行集合，请使用`CTable`相反。  
  
[CMultipleResults](../../data/oledb/cmultipleresults-class.md)<br/>
用作模板参数`CCommand`模板时想要处理多个结果集的命令。  
  
[CNoAccessor](../../data/oledb/cnoaccessor-class.md)<br/>
使用作为模板参数的模板类，如`CCommand`和`CTable`，采用的访问器类参数。 使用`CNoAccessor`如果你确实想要支持参数或输出列的类。  
  
[CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md)<br/>
用作模板参数`CCommand`模板时想要处理单个行集的命令。 `CNoMultipleResults` 是模板参数的默认值。  
  
[CNoRowset](../../data/oledb/cnorowset-class.md)<br/>
用作模板参数`CCommand`或`CTable`如果命令或表不返回行集。  
  
[CTable](../../data/oledb/ctable-class.md)<br/>
用于访问简单行集合不带任何参数。  
  
## <a name="property-classes"></a>属性类  

[CDBPropIDSet](../../data/oledb/cdbpropidset-class.md)<br/>
用于为其使用者想属性信息的属性 Id 的数组传递。 属性属于一个属性集。  
  
[CDBPropSet](../../data/oledb/cdbpropset-class.md)<br/>
用于在提供程序上设置属性。  
  
## <a name="bookmark-class"></a>书签类  

[CBookmark](../../data/oledb/cbookmark-class.md)<br/>
用于作为索引访问行集中的数据。  
  
## <a name="error-class"></a>错误类  

[CDBErrorInfo](../../data/oledb/cdberrorinfo-class.md)<br/>
用于检索 OLE DB 错误的信息。  
  
## <a name="see-also"></a>请参阅  

[OLE DB 提供程序模板参考](../../data/oledb/ole-db-provider-templates-reference.md)<br/>
[OLE DB 模板](../../data/oledb/ole-db-templates.md)