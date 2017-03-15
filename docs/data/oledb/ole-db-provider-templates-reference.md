---
title: "OLE DB 提供程序模板参考 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.templates.ole"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE DB 提供程序模板"
ms.assetid: 518358f0-bab1-4de9-bce9-4062cc87c11f
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# OLE DB 提供程序模板参考
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

类和接口 OLE DB 提供程序模板中可以组合成下列类别。  参考资料还包括有关 [OLE DB 提供程序模板的宏](../../data/oledb/macros-for-ole-db-provider-templates.md)中的信息。  
  
 类使用下列命名约定：类使用 **IWidgetImpl** 命名模式将提供 **IWidget**接口的实现。  
  
## 会话类  
 [IDBCreateSessionImpl](../../data/oledb/idbcreatesessionimpl-class.md)  
 创建从数据源对象的新会话并返回在新生成的会话的请求的接口。  对数据源对象的必需的接口。  
  
 [ISessionPropertiesImpl](../../data/oledb/isessionpropertiesimpl-class.md)  
 实现会话属性通过调用静态的函数定义由属性集映射。  在会话类指定属性集映射。  在会话的必需的接口。  
  
## 行集合类  
 [CRowsetImpl](../../data/oledb/crowsetimpl-class.md)  
  
 提供标准 OLE DB 行集合，而无需实现许多实现多个接口继承。  必须提供实现的唯一方法为 **执行**。  
  
 [CSimpleRow](../../data/oledb/csimplerow-class.md)  
 对于行句柄提供默认实现，使用 `IRowsetImpl` 类。  行处理逻辑上是结果行的唯一标记。  `IRowsetImpl` 创建 `IRowsetImpl::GetNextRows`请求的每个行的新 `CSimpleRow`。  
  
 [IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)  
 OLE DB 要求提供程序实现 **HACCESSOR**，是标记为一个 **DBBINDING** 结构。  提供 **HACCESSOR**为 **BindType** 结构的地址。  必须位于行集合和命令。  
  
 [IColumnsInfoImpl](../../data/oledb/icolumnsinfoimpl-class.md)  
 提供程序列映射定义的静态函数的委托。  对行集合和命令的必需的接口。  
  
 [IConvertTypeImpl](../../data/oledb/iconverttypeimpl-class.md)  
 提供有关类型转换的状态信息命令或对行集合。  必须位于命令索引、行集合和行集合。  通过委托转换 OLE DB 提供的对象实现 **IConvertType** 接口。  
  
 [IDBSchemaRowset](../../data/oledb/idbschemarowsetimpl-class.md)  
 实现 **IDBSchemaRowset** 接口并 templatized 创建者函数 `CreateSchemaRowset`。  
  
 [IOpenRowsetImpl](../../data/oledb/iopenrowsetimpl-class.md)  
 打开并返回一个包含基表或索引中所有行的行集合。  会话对象的必需的接口。  
  
 [IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md)  
 实现 OLE DB 接口，从而启用中 [IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx) 现有行的列，删除行和插入新行的更新值。  
  
 [IRowsetCreatorImpl](../../data/oledb/irowsetcreatorimpl-class.md)  
 此类从 [IObjectWithSite](http://msdn.microsoft.com/library/windows/desktop/ms693765) 继承并重写。[IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869) `IRowsetCreatorImpl` 执行与 `IObjectWithSite` 相同，而且支持 OLE DB 属性 **DBPROPCANSCROLLBACKWARDS** 和 **DBPROPCANFETCHBACKWARDS**。  
  
 [IRowsetIdentityImpl](../../data/oledb/irowsetidentityimpl-class.md)  
 实现 **IRowsetIdentity** 接口，则可以比较数据两行是否相同。  
  
 [IRowsetImpl](../../data/oledb/irowsetimpl-class.md)  
 提供 `IRowset` 接口的实现，即基行集合接口。  
  
 [IRowsetInfoImpl](../../data/oledb/irowsetinfoimpl-class.md)  
 实现该命令类使用属性集映射定义的行集合属性。  对行集合所必须的接口。  
  
 [IRowsetLocateImpl](../../data/oledb/irowsetlocateimpl-class.md)  
 实现 OLE DB 接口，[IRowsetLocate](https://msdn.microsoft.com/en-us/library/ms721190.aspx) 获取从行集合中任意行。  要支持在 OLE DB 为行集合书签，以便此类使行集继承。  
  
 [IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md)  
 实现广播函数，将行集合内容的更改通知给连接点 IID\_IRowsetNotify 上的侦听器。  处理通知的使用者。实现 [IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx) 并将其注册该连接点。  
  
 [IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md)  
 实现 OLE DB 接口允许使用者使用 [IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx) [IRowsetUpdate](https://msdn.microsoft.com/en-us/library/ms714401.aspx)，推迟更改传输到数据源以及在传输之前撤消更改。  
  
## 命令类  
 [ICommandImpl](../../data/oledb/icommandimpl-class.md)  
 提供 `ICommand` 接口的实现。  此接口不可见，但是，由 **ICommandTextImpl**处理。  在命令的对象强制接口。  
  
 [ICommandPropertiesImpl](../../data/oledb/icommandpropertiesimpl-class.md)  
 `BEGIN_PROPSET_MAP` 宏定义的静态函数提供 **ICommandProperties** 的实现此接口。  必须位于命令。  
  
 [ICommandTextImpl](../../data/oledb/icommandtextimpl-class.md)  
 设置、存储和返回命令文本。  必须位于命令。  
  
 [IDBCreateCommandImpl](../../data/oledb/idbcreatecommandimpl-class.md)  
 创建从会话对象的新命令并返回在新生成的命令上被请求的接口。  对会话对象的可选接口。  
  
 其他命令类为 `IColumnsInfoImpl` 和 `IAccessorImpl`，它描述上述行集合类中的节。  
  
## 数据源类  
 [IDBInitializeImpl](../../data/oledb/idbinitializeimpl-class.md)  
 创建并删除与使用者的连接。  对数据源对象的强制接口和由枚举数的可选接口。  
  
 [IDBPropertiesImpl](../../data/oledb/idbpropertiesimpl-class.md)  
 `IDBProperties` 是数据源的对象强制接口和枚举器的可选接口。  但是，如果，枚举器公开 **IDBInitialize**，必须公开 `IDBProperties` \(上的数据源属性\)。  
  
 [IGetDataSourceImpl](../../data/oledb/igetdatasourceimpl-class.md)  
 获取一个接口指针到数据源对象。  在会话的必需的接口。  
  
## 其他类  
 [CUtlProps](../../data/oledb/cutlprops-class.md)  
 实现多种 OLE DB 属性接口的属性 \(例如，`IDBProperties`、**ISessionProperties**和 `IRowsetInfo`。\)  
  
 [IErrorRecordsImpl](../../data/oledb/ierrorrecordsimpl-class.md)  
  
 实现 OLE DB 接口，[IErrorRecords](https://msdn.microsoft.com/en-us/library/ms718112.aspx) 日志添加到并检索记录数据成员。  
  
## 请参阅  
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [OLE DB 模板](../../data/oledb/ole-db-templates.md)