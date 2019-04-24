---
title: OLE DB 提供程序模板参考
ms.date: 11/04/2016
f1_keywords:
- vc.templates.ole
helpviewer_keywords:
- OLE DB provider templates
ms.assetid: 518358f0-bab1-4de9-bce9-4062cc87c11f
ms.openlocfilehash: e1d6be9687085361edd9141d8fb471e21b6f6376
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59038670"
---
# <a name="ole-db-provider-templates-reference"></a>OLE DB 提供程序模板参考

类和接口的 OLE DB 提供程序模板可分为以下类别。 参考资料还包括有关的信息[OLE DB 提供程序模板宏](../../data/oledb/macros-for-ole-db-provider-templates.md)。

类使用以下命名约定： 名为使用模式的类`IWidgetImpl`将提供接口的实现`IWidget`。

## <a name="session-classes"></a>会话类

[IDBCreateSessionImpl](../../data/oledb/idbcreatesessionimpl-class.md)<br/>
从数据源对象创建一个新的会话并返回所请求的接口上新创建的会话。 对数据源对象的必需接口。

[ISessionPropertiesImpl](../../data/oledb/isessionpropertiesimpl-class.md)<br/>
通过调用静态函数定义的属性集映射实现会话属性。 应在会话类中指定的属性集映射。 会话的必需接口。

## <a name="rowset-classes"></a>行集类

[CRowsetImpl](../../data/oledb/crowsetimpl-class.md)

提供标准的 OLE DB 行集实现，而无需许多实现接口的多个继承。 必须为其提供实现的唯一方法`Execute`。

[CSimpleRow](../../data/oledb/csimplerow-class.md)<br/>
提供的行控点，在中使用的默认实现`IRowsetImpl`类。 行控点在逻辑上就结果行的唯一标记。 `IRowsetImpl` 创建一个新`CSimpleRow`为每个行中请求`IRowsetImpl::GetNextRows`。

[IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)<br/>
OLE DB 要求提供程序实现`HACCESSOR`，这是指向数组的一个标记`DBBINDING`结构。 提供了`HACCESSOR`s 是地址`BindType`结构。 强制针对行集和命令参数。

[IColumnsInfoImpl](../../data/oledb/icolumnsinfoimpl-class.md)<br/>
由提供程序列映射定义的静态函数委托。 针对行集和命令的必需接口。

[IConvertTypeImpl](../../data/oledb/iconverttypeimpl-class.md)<br/>
命令或上一个行集提供类型转换的可用性的信息。 命令、 行集和索引行集上为强制参数。 实现`IConvertType`通过委托给 OLE db 提供的转换对象的接口。

[IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md)<br/>
实现`IDBSchemaRowset`接口和模板化创建程序函数`CreateSchemaRowset`。

[IOpenRowsetImpl](../../data/oledb/iopenrowsetimpl-class.md)<br/>
打开并返回包含来自单个基表或索引的所有行的行集。 会话对象的必需接口。

[IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md)<br/>
实现 OLE DB [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85))接口，可更新的现有行，删除行，并将插入新行中列的值。

[IRowsetCreatorImpl](../../data/oledb/irowsetcreatorimpl-class.md)<br/>
此类继承自[IObjectWithSite](/windows/desktop/api/ocidl/nn-ocidl-iobjectwithsite)并重写[IObjectWithSite::SetSite](/windows/desktop/api/ocidl/nf-ocidl-iobjectwithsite-setsite)。 `IRowsetCreatorImpl` 执行相同的功能`IObjectWithSite`还可以启用 OLE DB 属性，但`DBPROPCANSCROLLBACKWARDS`和`DBPROPCANFETCHBACKWARDS`。

[IRowsetIdentityImpl](../../data/oledb/irowsetidentityimpl-class.md)<br/>
实现`IRowsetIdentity`接口，可用于比较无论两行数据是否相同。

[IRowsetImpl](../../data/oledb/irowsetimpl-class.md)<br/>
提供的实现`IRowset`接口，这是基础行集接口。

[IRowsetInfoImpl](../../data/oledb/irowsetinfoimpl-class.md)<br/>
实现通过使用属性的行集属性设置命令类中定义的映射。 行集的必需接口。

[IRowsetLocateImpl](../../data/oledb/irowsetlocateimpl-class.md)<br/>
实现 OLE DB [IRowsetLocate](/previous-versions/windows/desktop/ms721190(v=vs.85))接口，从行集提取任意行。 若要在行集中支持 OLE DB 的书签，请从此类继承的行集。

[IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md)<br/>
实现广播函数向侦听器建议的连接点`IID_IRowsetNotify`对行集的内容的更改。 处理通知的使用者实现[IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85))并将其注册对该连接点。

[IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md)<br/>
实现 OLE DB [IRowsetUpdate](/previous-versions/windows/desktop/ms714401(v=vs.85))接口，可让使用者要延迟所做的更改传输[IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85))到数据源，并撤消在传输之前的更改。

## <a name="command-classes"></a>命令类

[ICommandImpl](../../data/oledb/icommandimpl-class.md)<br/>
提供 `ICommand` 接口的实现。 此接口是不可见，但由处理`ICommandTextImpl`。 命令对象上的必需接口。

[ICommandPropertiesImpl](../../data/oledb/icommandpropertiesimpl-class.md)<br/>
此实现`ICommandProperties`接口提供的定义的一个静态函数`BEGIN_PROPSET_MAP`宏。 命令为强制参数。

[ICommandTextImpl](../../data/oledb/icommandtextimpl-class.md)<br/>
设置、 存储，并返回命令文本。 命令为强制参数。

[IDBCreateCommandImpl](../../data/oledb/idbcreatecommandimpl-class.md)<br/>
从会话对象创建新的命令，并返回所请求的接口上新创建的命令。 会话对象的可选接口。

其他命令类的`IColumnsInfoImpl`和`IAccessorImpl`上面的行集类部分中所述。

## <a name="data-source-classes"></a>数据源类

[IDBInitializeImpl](../../data/oledb/idbinitializeimpl-class.md)<br/>
创建和删除与使用者的连接。 数据源对象和枚举器上使用的可选接口上的必需接口。

[IDBPropertiesImpl](../../data/oledb/idbpropertiesimpl-class.md)<br/>
`IDBProperties` 是数据源对象的必需接口和枚举器的可选接口。 但是，如果一个枚举器公开`IDBInitialize`，则它必须公开`IDBProperties`（数据源上的属性）。

[IGetDataSourceImpl](../../data/oledb/igetdatasourceimpl-class.md)<br/>
获取与数据源对象的接口指针。 在会话上必需的接口。

## <a name="other-classes"></a>其他类

[CUtlProps](../../data/oledb/cutlprops-class.md)<br/>
实现多个 OLE DB 属性接口的属性 (例如， `IDBProperties`， `ISessionProperties`，和`IRowsetInfo`)。

[IErrorRecordsImpl](../../data/oledb/ierrorrecordsimpl-class.md)

实现 OLE DB [IErrorRecords](/previous-versions/windows/desktop/ms718112(v=vs.85))接口添加到的记录并从数据成员中检索的记录。

## <a name="see-also"></a>请参阅

[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[OLE DB 模板](../../data/oledb/ole-db-templates.md)