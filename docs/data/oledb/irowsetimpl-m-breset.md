---
title: "IRowsetImpl::m_bReset | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.IRowsetImpl.m_bReset"
  - "IRowsetImpl.m_bReset"
  - "m_bReset"
  - "IRowsetImpl::m_bReset"
  - "ATL::IRowsetImpl::m_bReset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "m_bReset"
ms.assetid: d423f9f3-4d48-4d0c-b152-684c81a0b34e
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# IRowsetImpl::m_bReset
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用于的位标志光标位置是否定义对行集合。  
  
## 语法  
  
```  
  
unsigned m_bReset:1;  
  
```  
  
## 备注  
 如果使用者调用 [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md) 使用负 `lOffset` 或 *乌鸦* 和 `m_bReset` 为 true，`GetNextRows` 移到行集合的末尾。  如果 `m_bReset` 为 false，使用者策略 OLE DB 规范接收，错误代码。  `m_bReset` 标志集具有 **true**，而行集中首次创建时，并且，当使用者调用 [IRowsetImpl::RestartPosition](../../data/oledb/irowsetimpl-restartposition.md)时。  当您调用 `GetNextRows`时，其 **false** 集。  
  
## 要求  
 **页眉：** atldb.h  
  
## 请参阅  
 [IRowsetImpl 类](../../data/oledb/irowsetimpl-class.md)