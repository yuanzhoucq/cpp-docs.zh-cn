---
title: "IRowsetNotifyImpl::OnFieldChange | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IRowsetNotifyImpl.OnFieldChange"
  - "IRowsetNotifyImpl::OnFieldChange"
  - "OnFieldChange"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OnFieldChange 方法"
ms.assetid: f26b492c-c86e-423b-9374-175e510a2860
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# IRowsetNotifyImpl::OnFieldChange
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将对列值所做的任何更改通知给使用方。  
  
## 语法  
  
```  
  
STDMETHOD(OnFieldChange)(   
/* [in] */ IRowset* /* pRowset */,  
/* [in] */ HROW /* hRow */,  
/* [in] */ DBORDINAL /* cColumns */,  
/* [size_is][in] */ DBORDINAL /* rgColumns */ [] ,  
/* [in] */ DBREASON /* eReason */,  
/* [in] */ DBEVENTPHASE /* ePhase */,  
/* [in] */ BOOL /* fCantDeny */)  
```  
  
#### 参数  
 为说明参数参见 [IRowsetNotify::OnFieldChange](https://msdn.microsoft.com/en-us/library/ms715961.aspx)。  
  
## 返回值  
 返回值用于阐释参见 [IRowsetNotify::OnFieldChange](https://msdn.microsoft.com/en-us/library/ms715961.aspx)。  
  
## 备注  
 此方法包装方法 [IRowsetNotify::OnFieldChange](https://msdn.microsoft.com/en-us/library/ms715961.aspx)。  参阅《OLE DB 程序员参考该方法的说明。有关详细信息。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [IRowsetNotifyImpl 类](../../data/oledb/irowsetnotifyimpl-class.md)   
 [IRowsetNotify::OnFieldChange](https://msdn.microsoft.com/en-us/library/ms715961.aspx)