---
title: "支持通知 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "事件 [C++], OLE DB 中的通知"
  - " [C++], OLE DB 使用者"
  - "OLE DB 使用者, 通知"
  - "OLE DB 提供程序模板, 通知"
  - "OLE DB 提供程序, 通知"
  - "行集合, 事件通知"
ms.assetid: 76e875fd-2bfd-4e4e-9f43-dbe5a3fa7382
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 支持通知
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## 在提供程序和使用者上实现连接点接口  
 若要实现通知，提供程序类必须从 [IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md) 和 [IConnectionPointContainer](../../atl/reference/iconnectionpointcontainerimpl-class.md) 继承。  
  
 `IRowsetNotifyCP` 实现连接点接口 [IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx) 的提供程序站点。  `IRowsetNotifyCP` 实现广播函数，将行集合内容的更改通知给连接点 **IID\_IRowsetNotify** 上的侦听器。  
  
 注意，还必须使用 [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) 实现和注册使用者上的 `IRowsetNotify`（也称为“接收”），以便使用者处理通知。  有关如何实现使用者上的连接点接口的信息，请参见[接收通知](../../data/oledb/receiving-notifications.md)。  
  
 另外，该类还必须包含定义连接点项的映射，如下所示：  
  
```  
BEGIN_CONNECTION_POINT_MAP  
   CONNECTIONPOINT_ENTRY (IID_IRowsetNotify)  
END_CONNECTION_POINT_MAP  
```  
  
## 添加 IRowsetNotify  
 若要添加 `IRowsetNotify`，需要将 `IConnectionPointContainerImpl<rowset-name>` 和 `IRowsetNotifyCP<rowset-name>` 添加到继承链。  
  
 例如，下面是 [UpdatePV](http://msdn.microsoft.com/zh-cn/c8bed873-223c-4a7d-af55-f90138c6f38f) 中 `RUpdateRowset` 的继承链：  
  
> [!NOTE]
>  代码示例可能与此处列出的不同；此代码示例应视为较新版本。  
  
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
  
### 设置 COM 映射项  
 还需要将以下代码添加到行集合中的 COM 映射：  
  
```  
COM_INTERFACE_ENTRY(IConnectionPointContainer)  
COM_INTERFACE_ENTRY_IMPL(IConnectionPointContainer)  
```  
  
 这些宏允许任何为连接点容器（`IRowsetNotify` 的基）调用 `QueryInterface` 的人查找提供程序上被请求的接口。  有关如何使用连接点的示例，请参见 ATL POLYGON 示例和教程。  
  
### 设置连接点映射项  
 还需要添加连接点映射。  它看起来应像：  
  
```  
BEGIN_CONNECTION_POINT_MAP(rowset-name)  
     CONNECTION_POINT_ENTRY(_uuidof(IRowsetNotify))  
END_CONNECTION_POINT_MAP()  
```  
  
 此连接点映射允许查找 `IRowsetNotify` 接口的组件在提供程序中查找它。  
  
### 设置属性  
 还需要将以下属性添加到提供程序。  只需要添加基于所支持接口的属性。  
  
|Property|如果支持则添加|  
|--------------|-------------|  
|**DBPROP\_IConnectionPointContainer**|始终|  
|**DBPROP\_NOTIFICATIONGRANULARITY**|始终|  
|**DBPROP\_NOTIFICATIONPHASES**|始终|  
|**DBPROP\_NOTIFYCOLUMNSET**|`IRowsetChange`|  
|**DBPROP\_NOTIFYROWDELETE**|`IRowsetChange`|  
|**DBPROP\_NOTIFYROWINSERT**|`IRowsetChange`|  
|**DBPROP\_NOTIFYROWSETFETCHPOSITIONCHANGE**|始终|  
|**DBPROP\_NOTIFYROWFIRSTCHANGE**|`IRowsetUpdate`|  
|**DBPROP\_NOTIFYROWSETRELEASE**|始终|  
|**DBPROP\_NOTIFYROWUNDOCHANGE**|`IRowsetUpdate`|  
|**DBPROP\_NOTIFYROWUNDODELETE**|`IRowsetUpdate`|  
|**DBPROP\_NOTIFYROWUNDOINSERT**|`IRowsetUpdate`|  
|**DBPROP\_NOTIFYROWUPDATE**|`IRowsetUpdate`|  
  
 通知的大部分实现已嵌入在 OLE DB 提供程序模板中。  由于 Visual C\+\+ .NET 中某个编译器功能的原因，如果不将 `IRowsetNotifyCP` 添加到继承链，编译器将从编译流中移除所有那些代码，从而使代码大小变小。  
  
## 请参阅  
 [高级提供程序技术](../../data/oledb/advanced-provider-techniques.md)