---
title: "接收通知 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - " [C++], 事件"
  - " [C++], OLE DB 使用者"
  - "OLE DB 使用者, 通知"
  - "OLE DB 提供程序, 通知"
  - "在 OLE DB 中接收通知"
  - "行集合, 事件通知"
ms.assetid: 305a1103-0c87-40c8-94bc-7fbbdd52ae32
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 接收通知
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OLE DB 提供用于在事件发生时接收通知的接口。  这些接口在“OLE DB 程序员参考”的 [OLE DB 对象通知](https://msdn.microsoft.com/en-us/library/ms725406.aspx)中进行了描述。  这些事件的设置使用标准的 COM 连接点机制。  例如，希望通过 `IRowsetNotify` 检索事件的 ATL 对象通过将 `IRowsetNotify` 添加到类派生列表中并通过 **COM\_INTERFACE\_ENTRY** 宏将其公开，从而实现 `IRowsetNotify` 接口。  
  
 `IRowsetNotify` 具有三种方法，可以在不同时间进行调用。  如果只想响应其中的一种方法，则可以使用 [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) 类，它对您不感兴趣的方法返回 **E\_NOTIMPL**。  
  
 创建行集合时，必须告知提供程序希望使返回的行集合对象支持 **IConnectionPointContainer**（需要用它设置通知）。  
  
 下面的代码演示如何从 ATL 对象打开行集合并使用 `AtlAdvise` 函数设置通知接收器。  `AtlAdvise` 返回调用 `AtlUnadvise` 时使用的 Cookie。  
  
```  
CDBPropSet propset(DBPROPSET_ROWSET);  
propset.AddProperty(DBPROP_IConnectionPointContainer, true);  
  
product.Open(session, _T("Products"), &propset);  
  
AtlAdvise(product.m_spRowset, GetUnknown(), IID_IRowsetNotify, &m_dwCookie);  
```  
  
## 请参阅  
 [使用访问器](../../data/oledb/using-accessors.md)