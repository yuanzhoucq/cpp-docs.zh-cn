---
title: OLE DB 提供程序模板参考
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB provider templates
ms.assetid: 518358f0-bab1-4de9-bce9-4062cc87c11f
ms.openlocfilehash: 567d4131229ee25d0d69ff4456398e05af387f0e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210036"
---
# <a name="ole-db-provider-templates-reference"></a>OLE DB 提供程序模板参考

OLE DB 提供程序模板的类和接口可以分为以下类别。 参考材料还包括有关[OLE DB 提供程序模板的宏](../../data/oledb/macros-for-ole-db-provider-templates.md)的信息。

类使用以下命名约定：一个名为的类，其中的模式 `IWidgetImpl` 会提供接口的实现 `IWidget`。

## <a name="session-classes"></a>会话类

[IDBCreateSessionImpl](../../data/oledb/idbcreatesessionimpl-class.md)<br/>
从数据源对象创建新的会话，并返回新创建的会话上所请求的接口。 数据源对象上的必需接口。

[ISessionPropertiesImpl](../../data/oledb/isessionpropertiesimpl-class.md)<br/>
通过调用由属性集映射定义的静态函数来实现会话属性。 应在会话类中指定属性集映射。 会话上的必需接口。

## <a name="rowset-classes"></a>行集类

[CRowsetImpl](../../data/oledb/crowsetimpl-class.md)

提供标准 OLE DB 行集实现，无需多次继承多个实现接口。 您必须为其提供实现的唯一方法是 `Execute`。

[CSimpleRow](../../data/oledb/csimplerow-class.md)<br/>
提供行句柄的默认实现，该实现在 `IRowsetImpl` 类中使用。 行句柄以逻辑方式为结果行的唯一标记。 `IRowsetImpl` 为 `IRowsetImpl::GetNextRows`中请求的每个行创建新 `CSimpleRow`。

[IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)<br/>
OLE DB 要求提供程序实现 `HACCESSOR`，这是 `DBBINDING` 结构的数组的标记。 提供 `BindType` 结构的地址 `HACCESSOR`。 对于行集和命令是必需的。

[IColumnsInfoImpl](../../data/oledb/icolumnsinfoimpl-class.md)<br/>
委托给提供程序列映射定义的静态函数。 行集和命令的必需接口。

[IConvertTypeImpl](../../data/oledb/iconverttypeimpl-class.md)<br/>
提供有关命令或行集上类型转换的可用性的信息。 对命令、行集和索引行集是必需的。 通过委托到 OLE DB 提供的转换对象来实现 `IConvertType` 接口。

[IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md)<br/>
实现 `IDBSchemaRowset` 接口，并 `CreateSchemaRowset`模板化创建者函数。

[IOpenRowsetImpl](../../data/oledb/iopenrowsetimpl-class.md)<br/>
打开并返回一个行集，其中包括单个基表或索引中的所有行。 会话对象的必需接口。

[IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md)<br/>
实现 OLE DB [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85))接口，该接口允许更新现有行中列的值、删除行和插入新行。

[IRowsetCreatorImpl](../../data/oledb/irowsetcreatorimpl-class.md)<br/>
此类继承自[IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite) ，并重写[IObjectWithSite：： SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite)。 `IRowsetCreatorImpl` 执行与 `IObjectWithSite` 相同的功能，但同时启用 OLE DB 属性 `DBPROPCANSCROLLBACKWARDS` 和 `DBPROPCANFETCHBACKWARDS`。

[IRowsetIdentityImpl](../../data/oledb/irowsetidentityimpl-class.md)<br/>
实现 `IRowsetIdentity` 接口，该接口允许您比较两行数据是否相同。

[IRowsetImpl](../../data/oledb/irowsetimpl-class.md)<br/>
提供 `IRowset` 接口的实现，该接口是基行集接口。

[IRowsetInfoImpl](../../data/oledb/irowsetinfoimpl-class.md)<br/>
使用在命令类中定义的属性集映射实现行集属性。 行集上的必需接口。

[IRowsetLocateImpl](../../data/oledb/irowsetlocateimpl-class.md)<br/>
实现 OLE DB [IRowsetLocate](/previous-versions/windows/desktop/ms721190(v=vs.85))接口，该接口从行集中提取任意行。 若要支持在行集中 OLE DB 书签，请将行集继承此类。

[IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md)<br/>
实现广播函数以便在连接点上通知侦听器 `IID_IRowsetNotify` 对行集的内容进行更改。 处理通知的使用者实现[IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85))并将其注册到该连接点。

[IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md)<br/>
实现 OLE DB [IRowsetUpdate](/previous-versions/windows/desktop/ms714401(v=vs.85))接口，该接口允许使用者延迟向数据源发出的[IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85))更改，并在传输前撤消更改。

## <a name="command-classes"></a>命令类

[ICommandImpl](../../data/oledb/icommandimpl-class.md)<br/>
提供 `ICommand` 接口的实现。 此接口不可见，但由 `ICommandTextImpl`处理。 命令对象的必需接口。

[ICommandPropertiesImpl](../../data/oledb/icommandpropertiesimpl-class.md)<br/>
此 `ICommandProperties` 接口的实现由 `BEGIN_PROPSET_MAP` 宏定义的静态函数提供。 对命令是必需的。

[ICommandTextImpl](../../data/oledb/icommandtextimpl-class.md)<br/>
设置、存储并返回命令文本。 对命令是必需的。

[IDBCreateCommandImpl](../../data/oledb/idbcreatecommandimpl-class.md)<br/>
从 session 对象创建一个新的命令，并在新创建的命令上返回所请求的接口。 会话对象上的可选接口。

其他命令类 `IColumnsInfoImpl` 和 `IAccessorImpl`中，如上面的行集类部分所述。

## <a name="data-source-classes"></a>数据源类

[IDBInitializeImpl](../../data/oledb/idbinitializeimpl-class.md)<br/>
创建和删除与使用者的连接。 数据源对象上的必需接口和枚举器上的可选接口。

[IDBPropertiesImpl](../../data/oledb/idbpropertiesimpl-class.md)<br/>
`IDBProperties` 是数据源对象的必需接口和枚举器的可选接口。 但是，如果枚举器公开 `IDBInitialize`，则它必须公开 `IDBProperties` （数据源上的属性）。

[IGetDataSourceImpl](../../data/oledb/igetdatasourceimpl-class.md)<br/>
获取指向数据源对象的接口指针。 会话上的必需接口。

## <a name="other-classes"></a>其他类

[CUtlProps](../../data/oledb/cutlprops-class.md)<br/>
实现多种 OLE DB 属性接口的属性（例如，`IDBProperties`、`ISessionProperties`和 `IRowsetInfo`）。

[IErrorRecordsImpl](../../data/oledb/ierrorrecordsimpl-class.md)

实现 OLE DB [IErrorRecords](/previous-versions/windows/desktop/ms718112(v=vs.85))接口，向数据成员添加记录并从中检索记录。

## <a name="see-also"></a>另请参阅

[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[OLE DB 模板](../../data/oledb/ole-db-templates.md)
