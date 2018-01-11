---
title: "OLE DB 使用者模板参考 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-attr.db_param
- vc-attr.db_column
- vc-attr.db_accessor
- vc-attr.db_command
- vc-attr.db_table
- vc.templates.ole
- vc-attr.db_source
dev_langs: C++
helpviewer_keywords: OLE DB consumer templates, classes
ms.assetid: cfc7f698-1a0e-4a09-a4d3-ccb99e6654fe
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 681654f79f0cb3574b0893bb9f726bea78435e74
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ole-db-consumer-templates-reference"></a>OLE DB 使用者模板参考
OLE DB 使用者模板包含以下类。 参考材料也包括主题上[用于 OLE DB 使用者模板的宏](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)。  
  
## <a name="session-classes"></a>会话类  
 [CDataConnection](../../data/oledb/cdataconnection-class.md)  
 管理与数据源的连接。 这是有用的类，用于创建客户端，因为它封装必要的对象 （数据源和会话） 和一些操作，你需要连接到数据源时执行的操作。  
  
 [CDataSource](../../data/oledb/cdatasource-class.md)  
 对应于 OLE DB 数据源对象，表示通过提供商连接到数据源。 一个或多个数据库会话，每个由`CSession`对象，会在单个连接上的发生。  
  
 [CEnumerator](../../data/oledb/cenumerator-class.md)  
 对应于一个 OLE DB 枚举器对象，它检索有关可用数据源的行集信息。  
  
 [CEnumeratorAccessor](../../data/oledb/cenumeratoraccessor-class.md)  
 使用`CEnumerator`从枚举器行集访问数据。 下一个行集合组成的数据源和当前的枚举器中可见的枚举器。  
  
 [CSession](../../data/oledb/csession-class.md)  
 表示单个数据库访问会话。 一个或多个会话可以与每个相关联`CDataSource`对象。  
  
## <a name="accessor-classes"></a>访问器类  
 [CAccessor](../../data/oledb/caccessor-class.md)  
 用于静态绑定到数据源的记录。 当你知道数据源的结构时，请使用此访问器类。  
  
 [CAccessorBase](../../data/oledb/caccessorbase-class.md)  
 所有访问器类的基类。  
  
 [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)  
 访问器可用于创建在运行时，基于行集的列信息。 此类用于检索数据，如果你不知道数据源的结构。  
  
 [CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md)  
 未知命令类型时可以使用访问器。 通过调用获取的参数信息`ICommandWithParameters`接口，如果该提供程序支持的接口。  
  
 [CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md)  
 可以在不知道数据库的基础结构时访问数据源。  
  
 [CDynamicStringAccessorA](../../data/oledb/cdynamicstringaccessora-class.md)  
 类似于`CDynamicStringAccessor`只不过此类请求数据从数据存储区作为 ANSI 字符串数据访问。  
  
 [CDynamicStringAccessorW](../../data/oledb/cdynamicstringaccessorw-class.md)  
 类似于`CDynamicStringAccessor`只不过此类请求数据从数据存储为 UNICODE 字符串数据访问。  
  
 [CManualAccessor](../../data/oledb/cmanualaccessor-class.md)  
 访问器使用的方法可处理列和命令参数。 与此类中，你可以使用任何数据类型，只要提供程序可以将类型转换。  
  
 [CNoAccessor](../../data/oledb/cnoaccessor-class.md)  
 可以用作模板自变量时你不想要支持参数或输出列的类。  
  
 [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)  
 类似于`CDynamicStringAccessor`只不过此类将转换从数据存储为 XML 格式 （有标记） 数据访问的所有数据。  
  
## <a name="rowset-classes"></a>行集类  
 [CAccessorRowset](../../data/oledb/caccessorrowset-class.md)  
 封装一个行集和其关联的访问器。  
  
 [CArrayRowset](../../data/oledb/carrayrowset-class.md)  
 用于访问行集使用数组语法的元素。  
  
 [CBulkRowset](../../data/oledb/cbulkrowset-class.md)  
 用于提取，并将通过检索一次调用的多个行句柄操作成批的行。  
  
 [CNoRowset](../../data/oledb/cnorowset-class.md)  
 可以将用作模板自变量，如果该命令不返回行集。  
  
 [CRestrictions](../../data/oledb/crestrictions-class.md)  
 用于指定架构行集的限制。  
  
 [CRowset](../../data/oledb/crowset-class.md)  
 用于操作、 设置和检索行集数据。  
  
 [CStreamRowset](../../data/oledb/cstreamrowset-class.md)  
 返回`ISequentialStream`对象而不是行集; 然后使用**读取**方法来检索 XML 格式的数据。 （SQL Server 2000 进行格式设置; 请注意，此功能只可使用 SQL Server 2000。）  
  
 [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md)  
 提供的虚拟实现`IRowsetNotify`，具有可实现的空功能`IRowsetNotify`方法`OnFieldChange`， `OnRowChange`，和`OnRowsetChange`。  
  
 [架构行集类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)  
  
 OLE DB 模板为你提供了一组对应的 OLE DB 架构行集的类。  
  
## <a name="command-classes"></a>命令类  
 [CCommand](../../data/oledb/ccommand-class.md)  
 用于设置和执行基于参数的 OLE DB 命令。 若要仅打开简单行集合，使用`CTable`相反。  
  
 [CMultipleResults](../../data/oledb/cmultipleresults-class.md)  
 用作模板参数`CCommand`模板时想要处理多个结果集的命令。  
  
 [CNoAccessor](../../data/oledb/cnoaccessor-class.md)  
 用于作为模板参数的模板类，如`CCommand`和`CTable`，采用的访问器类自变量。 使用`CNoAccessor`如果你不想要支持参数或输出列的类。  
  
 [CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md)  
 用作模板参数`CCommand`模板时想要处理单个行集的命令。 `CNoMultipleResults`是模板参数的默认值。  
  
 [CNoRowset](../../data/oledb/cnorowset-class.md)  
 用作模板参数`CCommand`或`CTable`如果命令或表不返回行集。  
  
 [CTable](../../data/oledb/ctable-class.md)  
 用于访问简单行集合不带任何参数。  
  
## <a name="property-classes"></a>属性类  
 [CDBPropIDSet](../../data/oledb/cdbpropidset-class.md)  
 使用传递的属性 Id 为其使用者想属性信息的数组。 这些属性属于一个属性集。  
  
 [CDBPropSet](../../data/oledb/cdbpropset-class.md)  
 用于在提供程序上设置属性。  
  
## <a name="bookmark-class"></a>书签类  
 [CBookmark](../../data/oledb/cbookmark-class.md)  
 用于作为索引访问在行集中的数据。  
  
## <a name="error-class"></a>错误类  
 [CDBErrorInfo](../../data/oledb/cdberrorinfo-class.md)  
 用于检索 OLE DB 错误信息。  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板参考](../../data/oledb/ole-db-provider-templates-reference.md)   
 [OLE DB 模板](../../data/oledb/ole-db-templates.md)