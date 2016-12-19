---
title: "IRowsetImpl::m_rgRowHandles | Microsoft Docs"
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
  - "IRowsetImpl::m_rgRowHandles"
  - "IRowsetImpl.m_rgRowHandles"
  - "m_rgRowHandles"
  - "ATL::IRowsetImpl::m_rgRowHandles"
  - "ATL.IRowsetImpl.m_rgRowHandles"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "m_rgRowHandles"
ms.assetid: d3c2578f-58c4-4301-bf59-cf101a523a95
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetImpl::m_rgRowHandles
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

行处理映射提供程序当前包含的响应 `GetNextRows`。  
  
## 语法  
  
```  
  
MapClass  
 m_rgRowHandles;  
  
```  
  
## 备注  
 调用 `ReleaseRows`中移除行句柄。  为定义 *的 MapClass*参见 [IRowsetImpl 概述](../../data/oledb/irowsetimpl-class.md)。  
  
## 要求  
 **页眉：** atldb.h  
  
## 请参阅  
 [IRowsetImpl 类](../../data/oledb/irowsetimpl-class.md)