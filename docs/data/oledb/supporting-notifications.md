---
title: 支持通知 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- notifications [C++], OLE DB consumers
- events [C++], notifications in OLE DB
- OLE DB consumers, notifications
- rowsets, event notifications
- OLE DB provider templates, notifications
- OLE DB providers, notifications
ms.assetid: 76e875fd-2bfd-4e4e-9f43-dbe5a3fa7382
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a98848799163fd31037dc137b92b94878a1ee675
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2018
ms.locfileid: "49082457"
---
# <a name="supporting-notifications"></a>支持通知

## <a name="implementing-connection-point-interfaces-on-the-provider-and-consumer"></a>实现连接点接口上的提供程序和使用者  

若要实现通知，提供程序类必须继承[IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md)并[IConnectionPointContainer](../../atl/reference/iconnectionpointcontainerimpl-class.md)。  
  
`IRowsetNotifyCP` 实现连接点接口的提供程序站点[IRowsetNotify](/previous-versions/windows/desktop/ms712959)。 `IRowsetNotifyCP` 实现广播函数向侦听器建议的连接点`IID_IRowsetNotify`对行集的内容的更改。  
  
请注意，您还必须实现和注册`IRowsetNotify`上使用使用者 （也称为接收器） [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) ，以便使用者可以处理通知。 有关实现上使用者连接点接口的信息，请参阅[接收通知](../../data/oledb/receiving-notifications.md)。  
  
此外，类还必须包含一个映射，以定义连接点条目，如下：  
  
```  
BEGIN_CONNECTION_POINT_MAP  
   CONNECTIONPOINT_ENTRY (IID_IRowsetNotify)  
END_CONNECTION_POINT_MAP  
```  
  
## <a name="adding-irowsetnotify"></a>添加 IRowsetNotify  

若要添加`IRowsetNotify`，您需要添加`IConnectionPointContainerImpl<rowset-name>`和`IRowsetNotifyCP<rowset-name>`到继承链。  
  
例如，下面是有关继承链`RUpdateRowset`中[UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV):  
  
> [!NOTE]
>  示例代码可能不同于此处; 列出示例代码应视为较新版本。  
  
```cpp
///////////////////////////////////////////////////////////////////////////  
// class RUpdateRowset (in rowset.h)  
  
class RUpdateRowset :   
public CRowsetImpl< RUpdateRowset, CAgentMan, CUpdateCommand,   
         CAtlArray< CAgentMan, CAtlArray<CAgentMan>>, CSimpleRow,   
         IRowsetScrollImpl< RUpdateRowset, IRowsetScroll >>,  
      public IRowsetUpdateImpl< RUpdateRowset, CAgentMan >,  
      public IConnectionPointContainerImpl<RUpdateRowset>,  
      public IRowsetNotifyCP<RUpdateRowset>  
```  
  
### <a name="setting-com-map-entries"></a>设置 COM 映射项  

此外需要将以下代码添加到行集合中的 COM 映射：  
  
```  
COM_INTERFACE_ENTRY(IConnectionPointContainer)  
COM_INTERFACE_ENTRY_IMPL(IConnectionPointContainer)  
```  
  
这些宏允许任何人调用`QueryInterface`连接点容器 (的基础`IRowsetNotify`) 若要查找您的提供程序上请求的接口。 有关如何使用连接点的示例，请参阅 ATL 多边形示例和教程。  
  
### <a name="setting-connection-point-map-entries"></a>设置连接点的映射条目  

此外需要添加连接点映射。 它应如下所示：  
  
```  
BEGIN_CONNECTION_POINT_MAP(rowset-name)  
     CONNECTION_POINT_ENTRY(_uuidof(IRowsetNotify))  
END_CONNECTION_POINT_MAP()  
```  
  
此连接点映射允许组件寻找`IRowsetNotify`接口提供程序中找到它。  
  
### <a name="setting-properties"></a>设置属性  

此外需要将以下属性添加到您的提供程序。 只需添加基于支持的接口的属性。  
  
|属性|如果支持则添加|  
|--------------|------------------------|  
|`DBPROP_IConnectionPointContainer`|Always|  
|`DBPROP_NOTIFICATIONGRANULARITY`|Always|  
|`DBPROP_NOTIFICATIONPHASES`|Always|  
|`DBPROP_NOTIFYCOLUMNSET`|`IRowsetChange`|  
|`DBPROP_NOTIFYROWDELETE`|`IRowsetChange`|  
|`DBPROP_NOTIFYROWINSERT`|`IRowsetChange`|  
|`DBPROP_NOTIFYROWSETFETCHPOSITIONCHANGE`|Always|  
|`DBPROP_NOTIFYROWFIRSTCHANGE`|`IRowsetUpdate`|  
|`DBPROP_NOTIFYROWSETRELEASE`|Always|  
|`DBPROP_NOTIFYROWUNDOCHANGE`|`IRowsetUpdate`|  
|`DBPROP_NOTIFYROWUNDODELETE`|`IRowsetUpdate`|  
|`DBPROP_NOTIFYROWUNDOINSERT`|`IRowsetUpdate`|  
|`DBPROP_NOTIFYROWUPDATE`|`IRowsetUpdate`|  
  
在 OLE DB 提供程序模板中已嵌入大部分通知的实现。 如果不添加`IRowsetNotifyCP`到继承链，编译器将移除所有代码从编译流，从而使你的代码大小较小。  
  
## <a name="see-also"></a>请参阅  

[高级提供程序技术](../../data/oledb/advanced-provider-techniques.md)