---
title: "CAccessorRowset::Bind | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CAccessorRowset.Bind"
  - "CAccessorRowset::Bind"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Bind 方法"
ms.assetid: 42a1fc86-f570-4e54-9b82-7f7141564214
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CAccessorRowset::Bind
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如果在 [CCommand::Open](../../data/oledb/ccommand-open.md) 中指定了 **bBind** 为false，则创建绑定。  
  
## 语法  
  
```  
  
HRESULT Bind( );  
  
```  
  
## 返回值  
 标准版`HRESULT`。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CAccessorRowset 类](../../data/oledb/caccessorrowset-class.md)