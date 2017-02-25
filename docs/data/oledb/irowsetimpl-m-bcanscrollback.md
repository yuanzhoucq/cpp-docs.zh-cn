---
title: "IRowsetImpl::m_bCanScrollBack | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IRowsetImpl::m_bCanScrollBack"
  - "ATL::IRowsetImpl::m_bCanScrollBack"
  - "IRowsetImpl.m_bCanScrollBack"
  - "ATL.IRowsetImpl.m_bCanScrollBack"
  - "m_bCanScrollBack"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "m_bCanScrollBack"
ms.assetid: 69de3179-bf56-415e-935f-e98bcb34debe
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# IRowsetImpl::m_bCanScrollBack
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指示提供程序是否可以排列其反转光标移动。  
  
## 语法  
  
```  
  
unsigned  m_bCanScrollBack:1;  
  
```  
  
## 备注  
 指向 **DBPROP\_CANSCROLLBACKWARDS** 属性。**DBPROPSET\_ROWSET** 组中。  提供程序必须支持 **m\_bCanFetchBackwards** 的 **DBPROP\_CANSCROLLBACKWARDS** 都是如此。  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [IRowsetImpl 类](../../data/oledb/irowsetimpl-class.md)   
 [IRowsetImpl::m\_bCanFetchBack](../../data/oledb/irowsetimpl-m-bcanfetchback.md)