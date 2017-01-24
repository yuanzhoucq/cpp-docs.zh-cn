---
title: "CRowsetImpl::NameFromDBID | Microsoft Docs"
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
  - "CRowsetImpl.NameFromDBID"
  - "CRowsetImpl::NameFromDBID"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "NameFromDBID 方法"
ms.assetid: 6aa5b074-90c7-4434-adfd-c64c13e76c78
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowsetImpl::NameFromDBID
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从 **DBID** 的字符串并将它传递的 `bstr`。  
  
## 语法  
  
```  
  
      HRESULT CRowsetBaseImpl::NameFromDBID(  
   DBID* pDBID,  
   CComBSTR& bstr,  
   bool bIndex   
);  
```  
  
#### 参数  
 *pDBID*  
 \[in\] 该提取字符串 **DBID** 的指针。  
  
 `bstr`  
 \[in\] 将 **DBID** 字符串的副本的 [CComBSTR](../../atl/reference/ccombstr-class.md) 引用。  
  
 `bIndex`  
 \[in\] **true**，**DBID**;如果索引 **false** 表，则 **DBID**。  
  
## 返回值  
 标准版`HRESULT`。  根据 **DBID** 是否是表或索引 \(表示 `bIndex`\) 方法，将返回 **DB\_E\_NOINDEX** 或 **DB\_E\_NOTABLE**。  
  
## 备注  
 此方法由和 [ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md) [GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md)的 `CRowsetImpl` 实现调用。  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [CRowsetImpl 类](../../data/oledb/crowsetimpl-class.md)