---
title: "接收通知 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- notifications [C++], OLE DB consumers
- receiving notifications in OLE DB
- events [C++], notifications in OLE DB
- notifications [C++], events
- OLE DB consumers, notifications
- rowsets, event notifications
- OLE DB providers, notifications
ms.assetid: 305a1103-0c87-40c8-94bc-7fbbdd52ae32
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 29e82458f56c9b1f321f7a82afeb6f041be27854
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="receiving-notifications"></a>接收通知
OLE DB 提供用于在事件发生时接收通知的接口。 描述了这些内容在[OLE DB 对象通知](https://msdn.microsoft.com/en-us/library/ms725406.aspx)中*OLE DB 程序员参考*。 这些事件的安装程序将使用的标准的 COM 连接点机制。 例如，想要检索通过事件的 ATL 对象`IRowsetNotify`实现`IRowsetNotify`接口通过添加`IRowsetNotify`到派生类的列表并将其通过公开**COM_INTERFACE_ENTRY**宏。  
  
 `IRowsetNotify` 有三种方法，可以在不同时间调用。 如果你想要对这些方法之一做出响应，则可以使用[IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md)类，它将返回**E_NOTIMPL**你不感兴趣的方法。  
  
 在创建行集时，你必须告知提供程序想要返回的行集对象支持**IConnectionPointContainer**，所需设置通知。  
  
 下面的代码演示如何从 ATL 对象打开行集和使用`AtlAdvise`函数设置通知接收器。 `AtlAdvise` 返回在调用时使用 cookie `AtlUnadvise`。  
  
```  
CDBPropSet propset(DBPROPSET_ROWSET);  

propset.AddProperty(DBPROP_IConnectionPointContainer, true);  
  

product.Open(session, _T("Products"), &propset);  
  

AtlAdvise(product.m_spRowset, GetUnknown(), IID_IRowsetNotify, &m_dwCookie);  
```  
  
## <a name="see-also"></a>请参阅  
 [使用访问器](../../data/oledb/using-accessors.md)