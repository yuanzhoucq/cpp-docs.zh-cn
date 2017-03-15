---
title: "IRowsetNotifyImpl::OnRowChange | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IRowsetNotifyImpl::OnRowChange"
  - "IRowsetNotifyImpl.OnRowChange"
  - "OnRowChange"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OnRowChange 方法"
ms.assetid: 148bee03-3707-4bbf-8c51-657efc63645f
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# IRowsetNotifyImpl::OnRowChange
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将对行的第一个更改或影响整个行的任何更改通知给使用方。  
  
## 语法  
  
```  
  
STDMETHOD(OnRowChange)(   
/* [in] */ IRowset* /* pRowset */,  
/* [in] */ DBCOUNTITEM /* cRows */,  
/* [size_is][in] */ const HROW /* rghRows*/ [] ,  
/* [in] */ DBREASON /* eReason */,  
/* [in] */ DBEVENTPHASE /* ePhase */,  
/* [in] */ BOOL /* fCantDeny */)  
```  
  
#### 参数  
 为说明参数，参见 [IRowsetNotify::OnRowsetChange](https://msdn.microsoft.com/en-us/library/ms722694.aspx)。  
  
## 返回值  
 关于返回值的阐释，参见 [IRowsetNotify::OnRowsetChange](https://msdn.microsoft.com/en-us/library/ms722694.aspx)。  
  
## 备注  
 此方法包装 [IRowsetNotify::OnRowsetChange](https://msdn.microsoft.com/en-us/library/ms722694.aspx)方法。  有关详细信息，请参阅OLE DB 程序员引用的该方法描述。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [IRowsetNotifyImpl 类](../../data/oledb/irowsetnotifyimpl-class.md)   
 [IRowsetNotify::OnRowChange](https://msdn.microsoft.com/en-us/library/ms722694.aspx)