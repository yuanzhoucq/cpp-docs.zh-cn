---
title: "IRowsetImpl::m_bCanFetchBack | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.IRowsetImpl.m_bCanFetchBack"
  - "ATL::IRowsetImpl::m_bCanFetchBack"
  - "IRowsetImpl.m_bCanFetchBack"
  - "IRowsetImpl::m_bCanFetchBack"
  - "m_bCanFetchBack"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "m_bCanFetchBack"
ms.assetid: cfa007b0-7ba5-48a3-9d05-9f1916305fb7
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# IRowsetImpl::m_bCanFetchBack
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指示提供程序是否支持向后获取。  
  
## 语法  
  
```  
  
unsigned m_bCanFetchBack:1;  
  
```  
  
## 备注  
 指向 **DBPROP\_CANFETCHBACKWARDS** 属性。**DBPROPSET\_ROWSET** 组中。  提供程序必须支持 **m\_bCanFetchBackwards** 的 **DBPROP\_CANFETCHBACKWARDS** 都是如此。  
  
## 要求  
 **页眉：** atldb.h  
  
## 请参阅  
 [IRowsetImpl 类](../../data/oledb/irowsetimpl-class.md)   
 [IRowsetImpl::m\_bCanScrollBack](../../data/oledb/irowsetimpl-m-bcanscrollback.md)