---
title: "IRowsetUpdateImpl::m_mapCachedData | Microsoft Docs"
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
  - "IRowsetUpdateImpl.m_mapCachedData"
  - "IRowsetUpdateImpl::m_mapCachedData"
  - "m_mapCachedData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "m_mapCachedData"
ms.assetid: 65131743-8580-48c8-bb22-68f17c9dfa13
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetUpdateImpl::m_mapCachedData
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

一个包含原始数据的延迟操作映射。  
  
## 语法  
  
```  
  
      CAtlMap<   
   HROW hRow,    
   Storage* pData   
>   
m_mapCachedData;  
```  
  
#### 参数  
 `hRow`  
 要处理的数据行。  
  
 `pData`  
 一个指向要缓存的数据的指针。  数据是 *存储* 类型\(用户记录类\)。  参阅 [IRowsetUpdateImpl Class](../../data/oledb/irowsetupdateimpl-class.md) 的 *存储* 模板参数。  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [IRowsetUpdateImpl 类](../../data/oledb/irowsetupdateimpl-class.md)