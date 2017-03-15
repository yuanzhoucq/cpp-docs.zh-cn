---
title: "IRowsetNotifyCP 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IRowsetNotifyCP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IRowsetNotifyCP 类"
ms.assetid: ccef402b-94a0-4c2e-9a13-7e854ef82390
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# IRowsetNotifyCP 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现连接点接口中的 [IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx)提供程序网站。  
  
## 语法  
  
```  
template <  
   class T,   
   class ReentrantEventSync = CComSharedMutex   
>  
class IRowsetNotifyCP :   
   public IConnectionPointImpl<  
      T,   
      piid = &__uuidof(IRowsetNotify),   
      CComDynamicUnkArray DynamicUnkArray  
   >,  
   public ReentrantEventSync  
```  
  
#### 参数  
 `T`  
 从 `IRowsetNotifyCP`派生的类。  
  
 `ReentrantEventSync`  
 支持重新进入的 mutex 类 \(默认值即为 **CComSharedMutex**\)。  mutex 是一个允许一个线程以互相排斥资源的访问的同步对象。  
  
 `piid`  
 一个接口 ID 指针 \(**IID\***\) 连接点的 **IRowsetNotify** 接口。  默认值为 **&\_\_uuidof\(IRowsetNotify\)**。  
  
 `DynamicUnkArray`  
 数组类型，[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)是动态分配的 **IUnknown** 数组的指针。客户端接收接口。  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[Fire\_OnFieldChange](../../data/oledb/irowsetnotifycp-fire-onfieldchange.md)|更改通知的使用者该列的值。|  
|[Fire\_OnRowChange](../../data/oledb/irowsetnotifycp-fire-onrowchange.md)|影响行通知的使用者。|  
|[Fire\_OnRowsetChange](../../data/oledb/irowsetnotifycp-fire-onrowsetchange.md)|通知影响整行集的使用者。|  
  
## 备注  
 `IRowsetNotifyCP` 实现广播函数，将行集合内容的更改通知给连接点 **IID\_IRowsetNotify** 上的侦听器。  
  
 请注意您还必须实现和使用者上注册 \(aka 接收器“”\)，以便 `IRowsetNotify` 可以使用 [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) 使用者处理通知。  请参见有关实现连接点的 [接收通知](../../data/oledb/receiving-notifications.md) 连接到使用者。  
  
 通知关于实现的详细信息，请参见“”中的 [创建可更新的提供程序](../../data/oledb/creating-an-updatable-provider.md)。支持通知  
  
## 要求  
 **页眉：**atldb.h  
  
## 请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Notifications \(COM\)](http://msdn.microsoft.com/library/windows/desktop/ms678433)   
 [Overview of Notifications \(OLE DB\)](https://msdn.microsoft.com/en-us/library/ms725406.aspx)   
 [BEGIN\_CONNECTION\_POINT\_MAP](../Topic/BEGIN_CONNECTION_POINT_MAP.md)   
 [END\_CONNECTION\_POINT\_MAP](../Topic/END_CONNECTION_POINT_MAP.md)   
 [CONNECTION\_POINT\_ENTRY](../Topic/CONNECTION_POINT_ENTRY.md)   
 [创建可更新的提供程序](../../data/oledb/creating-an-updatable-provider.md)