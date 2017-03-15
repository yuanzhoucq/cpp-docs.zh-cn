---
title: "IRowsetNotifyImpl::OnRowsetChange | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OnRowsetChange"
  - "IRowsetNotifyImpl::OnRowsetChange"
  - "IRowsetNotifyImpl.OnRowsetChange"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OnRowsetChange 方法"
ms.assetid: 5125b0c8-f175-4ee6-befa-8df2c904d5e0
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# IRowsetNotifyImpl::OnRowsetChange
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将影响整个行集合的任何更改通知给使用方。  
  
## 语法  
  
```  
  
   STDMETHOD(OnRowsetChange)(   
/* [in] */ IRowset* /* pRowset */,  
/* [in] */ DBREASON /* eReason */,  
/* [in] */ DBEVENTPHASE /* ePhase */,  
/* [in] */ BOOL /* fCantDeny */)  
```  
  
#### 参数  
 为说明参数参见 [IRowsetNotify::OnRowsetChange](https://msdn.microsoft.com/en-us/library/ms722669.aspx)。  
  
## 返回值  
 返回值用于阐释参见 [IRowsetNotify::OnRowsetChange](https://msdn.microsoft.com/en-us/library/ms722669.aspx)。  
  
## 备注  
 此方法包装方法 [IRowsetNotify::OnRowsetChange](https://msdn.microsoft.com/en-us/library/ms722669.aspx)。  参阅《OLE DB 程序员参考该方法的说明。有关详细信息。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [IRowsetNotifyImpl 类](../../data/oledb/irowsetnotifyimpl-class.md)   
 [IRowsetNotify::OnRowsetChange](https://msdn.microsoft.com/en-us/library/ms722669.aspx)