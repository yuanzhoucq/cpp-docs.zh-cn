---
title: "CRowset::MovePrev | Microsoft Docs"
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
  - "CRowset<TAccessor>.MovePrev"
  - "CRowset.MovePrev"
  - "MovePrev"
  - "CRowset::MovePrev"
  - "ATL.CRowset.MovePrev"
  - "ATL::CRowset<TAccessor>::MovePrev"
  - "ATL::CRowset::MovePrev"
  - "ATL.CRowset<TAccessor>.MovePrev"
  - "CRowset<TAccessor>::MovePrev"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MovePrev 方法"
ms.assetid: 7ced2bfb-f556-40fc-97ea-0d4e7213e114
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowset::MovePrev
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将光标移回到上一记录。  
  
## 语法  
  
```  
  
HRESULT MovePrev( ) throw( );  
  
```  
  
## 返回值  
 标准版`HRESULT`。  
  
## 备注  
 此方法需要您将 **DBPROP\_CANFETCHBACKWARDS** 或包含行集合的 **DBPROP\_CANSCROLLBACKWARDS** 将 `VARIANT_TRUE` 表上或在调用 **打开** 前命令。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CRowset 类](../../data/oledb/crowset-class.md)   
 [CRowset::MoveNext](../../data/oledb/crowset-movenext.md)   
 [CRowset::MoveToBookmark](../../data/oledb/crowset-movetobookmark.md)   
 [CRowset::MoveLast](../../data/oledb/crowset-movelast.md)