---
title: 支持通知
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [C++], OLE DB consumers
- events [C++], notifications in OLE DB
- OLE DB consumers, notifications
- rowsets, event notifications
- OLE DB provider templates, notifications
- OLE DB providers, notifications
ms.assetid: 76e875fd-2bfd-4e4e-9f43-dbe5a3fa7382
ms.openlocfilehash: d29f84a0a5b33d55c0a04a4c758050cf9746f72a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209533"
---
# <a name="supporting-notifications"></a>支持通知

## <a name="implementing-connection-point-interfaces-on-the-provider-and-consumer"></a>在提供程序和使用者上实现连接点接口

若要实现通知，提供程序类必须从[IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md)和[IConnectionPointContainer](../../atl/reference/iconnectionpointcontainerimpl-class.md)继承。

`IRowsetNotifyCP` 实现连接点接口[IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85))的提供程序站点。 `IRowsetNotifyCP` 实现广播函数，以便在连接点上通知侦听器 `IID_IRowsetNotify` 行集内容的更改。

还必须使用[IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md)在使用者（也称为接收器）上实现并注册 `IRowsetNotify`，以便使用者可以处理通知。 有关在使用者上实现连接点接口的信息，请参阅[接收通知](../../data/oledb/receiving-notifications.md)。

此外，类必须有一个定义连接点项的映射，如下所示：

```cpp
BEGIN_CONNECTION_POINT_MAP
   CONNECTIONPOINT_ENTRY (IID_IRowsetNotify)
END_CONNECTION_POINT_MAP
```

## <a name="adding-irowsetnotify"></a>添加 IRowsetNotify

若要添加 `IRowsetNotify`，需要向继承链添加 `IConnectionPointContainerImpl<rowset-name>` 和 `IRowsetNotifyCP<rowset-name>`。

例如，下面是[UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)中 `RUpdateRowset` 的继承链：

> [!NOTE]
> 示例代码可能与本文列出的代码不同；应将示例代码视为最新版本。

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

还需要将以下内容添加到行集中的 COM 映射：

```cpp
COM_INTERFACE_ENTRY(IConnectionPointContainer)
COM_INTERFACE_ENTRY_IMPL(IConnectionPointContainer)
```

这些宏允许为连接点容器调用 `QueryInterface` 的任何人（`IRowsetNotify`的基础），以便在提供程序中查找请求的接口。 有关如何使用连接点的示例，请参阅 ATL 多边形示例和教程。

### <a name="setting-connection-point-map-entries"></a>设置连接点映射项

还需要添加连接点映射。 其外观应如下所示：

```cpp
BEGIN_CONNECTION_POINT_MAP(rowset-name)
     CONNECTION_POINT_ENTRY(_uuidof(IRowsetNotify))
END_CONNECTION_POINT_MAP()
```

此连接点映射允许组件查找 `IRowsetNotify` 接口，以在提供程序中查找它。

### <a name="setting-properties"></a>设置属性

还需要将以下属性添加到提供程序。 只需根据所支持的接口添加属性。

|properties|添加（如果支持）|
|--------------|------------------------|
|DBPROP_IConnectionPointContainer|始终|
|DBPROP_NOTIFICATIONGRANULARITY|始终|
|DBPROP_NOTIFICATIONPHASES|始终|
|DBPROP_NOTIFYCOLUMNSET|`IRowsetChange`|
|DBPROP_NOTIFYROWDELETE|`IRowsetChange`|
|DBPROP_NOTIFYROWINSERT|`IRowsetChange`|
|DBPROP_NOTIFYROWSETFETCHPOSITIONCHANGE|始终|
|DBPROP_NOTIFYROWFIRSTCHANGE|`IRowsetUpdate`|
|DBPROP_NOTIFYROWSETRELEASE|始终|
|DBPROP_NOTIFYROWUNDOCHANGE|`IRowsetUpdate`|
|DBPROP_NOTIFYROWUNDODELETE|`IRowsetUpdate`|
|DBPROP_NOTIFYROWUNDOINSERT|`IRowsetUpdate`|
|DBPROP_NOTIFYROWUPDATE|`IRowsetUpdate`|

大多数通知实现已嵌入 OLE DB 提供程序模板中。 如果不将 `IRowsetNotifyCP` 添加到继承链，编译器将从编译流中删除所有代码，从而使代码大小更小。

## <a name="see-also"></a>另请参阅

[高级提供程序技术](../../data/oledb/advanced-provider-techniques.md)
