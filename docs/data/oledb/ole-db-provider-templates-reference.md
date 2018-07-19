---
title: OLE DB 提供程序模板参考 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- vc.templates.ole
dev_langs:
- C++
helpviewer_keywords:
- OLE DB provider templates
ms.assetid: 518358f0-bab1-4de9-bce9-4062cc87c11f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 040e8a5e244b7978a2b9ead394e243207939655c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33112415"
---
# <a name="ole-db-provider-templates-reference"></a>OLE DB 提供程序模板参考
可以为以下类别分组的类和接口的 OLE DB 提供程序模板。 参考材料还包含下列相关信息[OLE DB 提供程序模板宏](../../data/oledb/macros-for-ole-db-provider-templates.md)。  
  
 类使用以下命名约定： 名为使用模式的类**IWidgetImpl**将提供接口的实现**IWidget**。  
  
## <a name="session-classes"></a>会话类  
 [IDBCreateSessionImpl](../../data/oledb/idbcreatesessionimpl-class.md)  
 从数据源对象创建新的会话并在新创建的会话上返回所请求的接口。 对数据源对象的必需接口。  
  
 [ISessionPropertiesImpl](../../data/oledb/isessionpropertiesimpl-class.md)  
 通过调用由属性集映射中定义的静态函数实现的会话属性。 应在会话类中指定属性集映射。 会话的必需接口。  
  
## <a name="rowset-classes"></a>行集类  
 [CRowsetImpl](../../data/oledb/crowsetimpl-class.md)  
  
 提供标准 OLE DB 行集实现，而无需许多实现接口的多个继承。 必须为其提供实现的唯一方法**执行**。  
  
 [CSimpleRow](../../data/oledb/csimplerow-class.md)  
 提供的默认实现中使用行句柄，`IRowsetImpl`类。 在逻辑上是结果行的唯一标记的行句柄。 `IRowsetImpl` 创建一个新`CSimpleRow`为每个行中请求`IRowsetImpl::GetNextRows`。  
  
 [IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)  
 OLE DB 需要提供程序实现**HACCESSOR**，即指向数组的标记**DBBINDING**结构。 提供**HACCESSOR**是的地址的 s **BindType**结构。 行集和命令上为强制参数。  
  
 [IColumnsInfoImpl](../../data/oledb/icolumnsinfoimpl-class.md)  
 委托给由提供程序列映射定义的静态函数。 行集和命令的必需接口。  
  
 [IConvertTypeImpl](../../data/oledb/iconverttypeimpl-class.md)  
 命令或行集上，为提供的可用性的类型转换的信息。 命令、 行集和索引行集上为强制参数。 实现**IConvertType**通过委派到由 OLE DB 提供的转换对象的接口。  
  
 [IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md)  
 实现**IDBSchemaRowset**接口和模板化创建程序函数`CreateSchemaRowset`。  
  
 [IOpenRowsetImpl](../../data/oledb/iopenrowsetimpl-class.md)  
 打开并返回一个包括来自一个基表或索引的所有行的行集。 会话对象的必需接口。  
  
 [IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md)  
 实现 OLE DB [IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx)接口，可更新的现有行，删除行，并将插入新行中的列的值。  
  
 [IRowsetCreatorImpl](../../data/oledb/irowsetcreatorimpl-class.md)  
 此类继承自[IObjectWithSite](http://msdn.microsoft.com/library/windows/desktop/ms693765)和替代[IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869)。 `IRowsetCreatorImpl` 执行与相同的功能`IObjectWithSite`但使 OLE DB 属性还**DBPROPCANSCROLLBACKWARDS**和**DBPROPCANFETCHBACKWARDS**。  
  
 [IRowsetIdentityImpl](../../data/oledb/irowsetidentityimpl-class.md)  
 实现**IRowsetIdentity**接口，允许你进行比较，无论两行数据是否相同。  
  
 [IRowsetImpl](../../data/oledb/irowsetimpl-class.md)  
 提供的实现`IRowset`接口，该基行集接口。  
  
 [IRowsetInfoImpl](../../data/oledb/irowsetinfoimpl-class.md)  
 实现使用属性的行集属性集命令类中定义的映射。 行集的必需接口。  
  
 [IRowsetLocateImpl](../../data/oledb/irowsetlocateimpl-class.md)  
 实现 OLE DB [IRowsetLocate](https://msdn.microsoft.com/en-us/library/ms721190.aspx)接口，从行集提取任意行。 若要在行集中支持 OLE DB 书签，请从此类继承的行集。  
  
 [IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md)  
 实现广播函数向侦听器建议的连接点**IID_IRowsetNotify**对行集的内容的更改。 处理通知的使用者都实现[IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx)并将其注册对该连接点。  
  
 [IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md)  
 实现 OLE DB [IRowsetUpdate](https://msdn.microsoft.com/en-us/library/ms714401.aspx)接口，可使用者延迟所做的更改传输[IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx)到数据源，并撤消在传输之前的更改。  
  
## <a name="command-classes"></a>命令类  
 [ICommandImpl](../../data/oledb/icommandimpl-class.md)  
 提供 `ICommand` 接口的实现。 此接口不可见，但由处理**ICommandTextImpl**。 命令对象上的必需接口。  
  
 [ICommandPropertiesImpl](../../data/oledb/icommandpropertiesimpl-class.md)  
 此实现的**ICommandProperties**由所定义的静态函数提供接口`BEGIN_PROPSET_MAP`宏。 在命令上为强制参数。  
  
 [ICommandTextImpl](../../data/oledb/icommandtextimpl-class.md)  
 设置、 存储，并返回命令文本。 在命令上为强制参数。  
  
 [IDBCreateCommandImpl](../../data/oledb/idbcreatecommandimpl-class.md)  
 从会话对象创建一个新的命令，然后返回所请求的接口上新创建的命令。 会话对象的可选接口。  
  
 其他命令类是`IColumnsInfoImpl`和`IAccessorImpl`，上面的行集类部分中所述。  
  
## <a name="data-source-classes"></a>数据源类  
 [IDBInitializeImpl](../../data/oledb/idbinitializeimpl-class.md)  
 创建和删除与使用者的连接。 在数据源对象和枚举器上的可选接口上的必需接口。  
  
 [IDBPropertiesImpl](../../data/oledb/idbpropertiesimpl-class.md)  
 `IDBProperties` 是数据源对象的必需接口和枚举器的可选接口。 但是，如果一个枚举器公开**IDBInitialize**，它必须公开`IDBProperties`（对数据源的属性）。  
  
 [IGetDataSourceImpl](../../data/oledb/igetdatasourceimpl-class.md)  
 获取与数据源对象的接口指针。 对该会话的必需接口。  
  
## <a name="other-classes"></a>其他类  
 [CUtlProps](../../data/oledb/cutlprops-class.md)  
 实现各种不同的 OLE DB 属性接口属性 (例如， `IDBProperties`， **ISessionProperties**，和`IRowsetInfo`)。  
  
 [IErrorRecordsImpl](../../data/oledb/ierrorrecordsimpl-class.md)  
  
 实现 OLE DB [IErrorRecords](https://msdn.microsoft.com/en-us/library/ms718112.aspx)接口，添加到的记录并从数据成员中检索的记录。  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [OLE DB 模板](../../data/oledb/ole-db-templates.md)