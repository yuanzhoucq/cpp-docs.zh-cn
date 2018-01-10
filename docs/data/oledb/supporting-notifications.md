---
title: "支持通知 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- notifications [C++], OLE DB consumers
- events [C++], notifications in OLE DB
- OLE DB consumers, notifications
- rowsets, event notifications
- OLE DB provider templates, notifications
- OLE DB providers, notifications
ms.assetid: 76e875fd-2bfd-4e4e-9f43-dbe5a3fa7382
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9a859a9f3b2061d1cb18c93cd9f46d30600ada28
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="supporting-notifications"></a>支持通知
## <a name="implementing-connection-point-interfaces-on-the-provider-and-consumer"></a>实现连接点接口上的提供程序和使用者  
 若要实现通知，提供程序类必须继承自[IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md)和[IConnectionPointContainer](../../atl/reference/iconnectionpointcontainerimpl-class.md)。  
  
 `IRowsetNotifyCP`实现连接点接口的提供程序站点[IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx)。 `IRowsetNotifyCP`实现广播函数向侦听器建议的连接点**IID_IRowsetNotify**对行集的内容的更改。  
  
 请注意，你还必须实现并注册`IRowsetNotify`上使用使用者 （也称为接收器） [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md)以便使用者可以处理通知。 有关实现上使用者连接点接口的信息，请参阅[接收通知](../../data/oledb/receiving-notifications.md)。  
  
 此外，类还必须包含定义连接点条目，如下图所示：  
  
```  
BEGIN_CONNECTION_POINT_MAP  
   CONNECTIONPOINT_ENTRY (IID_IRowsetNotify)  
END_CONNECTION_POINT_MAP  
```  
  
## <a name="adding-irowsetnotify"></a>添加 IRowsetNotify  
 若要添加`IRowsetNotify`，你需要添加`IConnectionPointContainerImpl<rowset-name>`和`IRowsetNotifyCP<rowset-name>`到继承链。  
  
 例如，下面是的继承链`RUpdateRowset`中[UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f):  
  
> [!NOTE]
>  示例代码可能会与不同列出的内容此处;你应将示例代码视为多最新版本。  
  
```  
///////////////////////////////////////////////////////////////////////////  
// class RUpdateRowset (in rowset.h)  
  
class RUpdateRowset :   
public CRowsetImpl< RUpdateRowset, CAgentMan, CUpdateCommand,   
         CAtlArray< CAgentMan, CAtlArray<CAgentMan> >, CSimpleRow,   
         IRowsetScrollImpl< RUpdateRowset, IRowsetScroll > >,  
      public IRowsetUpdateImpl< RUpdateRowset, CAgentMan >,  
      public IConnectionPointContainerImpl<RUpdateRowset>,  
      public IRowsetNotifyCP<RUpdateRowset>  
```  
  
### <a name="setting-com-map-entries"></a>设置 COM 映射项  
 你还需要将以下代码添加到行集合中的 COM 映射：  
  
```  
COM_INTERFACE_ENTRY(IConnectionPointContainer)  
COM_INTERFACE_ENTRY_IMPL(IConnectionPointContainer)  
```  
  
 这些宏允许任何人调用`QueryInterface`连接点容器 (的基础`IRowsetNotify`) 若要查找你的提供商上请求的接口。 有关如何使用连接点的示例，请参阅的 ATL 多边形示例和教程。  
  
### <a name="setting-connection-point-map-entries"></a>设置连接点的映射条目  
 你还需要添加连接点映射。 其外观应类似于：  
  
```  
BEGIN_CONNECTION_POINT_MAP(rowset-name)  
     CONNECTION_POINT_ENTRY(_uuidof(IRowsetNotify))  
END_CONNECTION_POINT_MAP()  
```  
  
 此连接点映射，寻找组件`IRowsetNotify`接口来在你的提供商中找到它。  
  
### <a name="setting-properties"></a>设置属性  
 你还需要将以下属性添加到你的提供商。 只需添加基于你支持在接口上的属性。  
  
|属性|如果支持则添加|  
|--------------|------------------------|  
|**DBPROP_IConnectionPointContainer**|Always|  
|**DBPROP_NOTIFICATIONGRANULARITY**|Always|  
|**DBPROP_NOTIFICATIONPHASES**|Always|  
|**DBPROP_NOTIFYCOLUMNSET**|`IRowsetChange`|  
|**DBPROP_NOTIFYROWDELETE**|`IRowsetChange`|  
|**DBPROP_NOTIFYROWINSERT**|`IRowsetChange`|  
|**DBPROP_NOTIFYROWSETFETCHPOSITIONCHANGE**|Always|  
|**DBPROP_NOTIFYROWFIRSTCHANGE**|`IRowsetUpdate`|  
|**DBPROP_NOTIFYROWSETRELEASE**|Always|  
|**DBPROP_NOTIFYROWUNDOCHANGE**|`IRowsetUpdate`|  
|**DBPROP_NOTIFYROWUNDODELETE**|`IRowsetUpdate`|  
|**DBPROP_NOTIFYROWUNDOINSERT**|`IRowsetUpdate`|  
|**DBPROP_NOTIFYROWUPDATE**|`IRowsetUpdate`|  
  
 在 OLE DB 提供程序模板中已嵌入大部分通知的实现。 如果不希望添加`IRowsetNotifyCP`到您的继承链，编译器将移除该代码从编译流，从而使代码大小较小。  
  
## <a name="see-also"></a>请参阅  
 [高级提供程序技术](../../data/oledb/advanced-provider-techniques.md)