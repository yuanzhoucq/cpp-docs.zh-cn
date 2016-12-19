---
title: "CRowsetImpl::m_rgRowData | Microsoft Docs"
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
  - "CRowsetImpl.m_rgRowData"
  - "CRowsetImpl::m_rgRowData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "m_rgRowData"
ms.assetid: e4e75ca7-12e8-4a0b-94e8-e395c21385b2
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowsetImpl::m_rgRowData
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

默认情况下，在用户记录模板参数 templatizes 为 `CRowsetImpl`的 `CAtlArray`。  
  
## 语法  
  
```  
  
ArrayType CRowsetBaseImpl::m_rgRowData;  
  
```  
  
## 备注  
 **ArrayType** 是一个模板参数设置为 `CRowsetImpl`。  
  
## 要求  
 **页眉：** atldb.h  
  
## 请参阅  
 [CRowsetImpl 类](../../data/oledb/crowsetimpl-class.md)   
 [CRowsetImpl::m\_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)   
 [CRowsetImpl::m\_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)