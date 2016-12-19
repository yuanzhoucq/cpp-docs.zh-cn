---
title: "IRowsetNotifyImpl 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.IRowsetNotifyImpl"
  - "ATL::IRowsetNotifyImpl"
  - "IRowsetNotifyImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IRowsetNotifyImpl 类"
ms.assetid: fbfd0cb2-38ff-4b42-899a-8de902f834b8
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetNotifyImpl 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现并注册在使用者 \(也称“接收”\) [IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx)，以便可以处理通知。  
  
## 语法  
  
```  
class ATL_NO_VTABLE IRowsetNotifyImpl : public IRowsetNotify  
```  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[OnFieldChange](../../data/oledb/irowsetnotifyimpl-onfieldchange.md)|将对列值所做的任何更改通知给使用方。|  
|[OnRowChange](../../data/oledb/irowsetnotifyimpl-onrowchange.md)|将对行的第一个更改或影响整个行的任何更改通知给使用方。|  
|[OnRowsetChange](../../data/oledb/irowsetnotifyimpl-onrowsetchange.md)|将影响整个行集合的任何更改通知给使用方。|  
  
## 备注  
 请参见有关实现连接点的 [接收通知](../../data/oledb/receiving-notifications.md) 连接到使用者。  
  
 `IRowsetNotifyImpl` 为 `IRowsetNotify`提供一条假的实现，其中 `IRowsetNotify` 的方法、[OnFieldChange](https://msdn.microsoft.com/en-us/library/ms715961.aspx)[OnRowChange](https://msdn.microsoft.com/en-us/library/ms722694.aspx)和 [OnRowsetChange](https://msdn.microsoft.com/en-us/library/ms722669.aspx)空函数中。  如果您从该类继承，则实现 `IRowsetNotify` 接口时，可以执行您仅需要的方法。  还需要对其他方法提供空的实现。  
  
## 要求  
 **页眉：**atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx)   
 [IRowsetNotifyCP 类](../../data/oledb/irowsetnotifycp-class.md)