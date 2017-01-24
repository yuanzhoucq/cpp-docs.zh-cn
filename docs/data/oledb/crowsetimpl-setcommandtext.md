---
title: "CRowsetImpl::SetCommandText | Microsoft Docs"
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
  - "CRowsetImpl.SetCommandText"
  - "CRowsetImpl::SetCommandText"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetCommandText 方法"
ms.assetid: e016d7df-c1a0-4dee-b19b-c876680221fd
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowsetImpl::SetCommandText
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

验证和存储在两字符串的 **DBID**。[m\_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) \(和\)。[m\_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)  
  
## 语法  
  
```  
  
      HRESULT CRowsetBaseImpl::SetCommandText(  
   DBID* pTableID,  
   DBID* pIndexID   
);  
```  
  
#### 参数  
 `pTableID`  
 \[in\] 指向表示表 . ID 的 **DBID** 的指针  
  
 `pIndexID`  
 \[in\] 对 ID. 索引表示 **DBID** 的指针  
  
## 返回值  
 标准 `HRESULT`。  
  
## 备注  
 **SetCommentText** 方法通过 `CreateRowset`，静态 `IOpenRowsetImpl`templatized 方法调用。  
  
 此方法通过调用 [ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md) 和 [GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md) 将其工作委托给 upcasted 通过一个指针。  
  
## 要求  
 **页眉：** atldb.h  
  
## 请参阅  
 [CRowsetImpl 类](../../data/oledb/crowsetimpl-class.md)