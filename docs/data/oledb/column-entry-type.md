---
title: "COLUMN_ENTRY_TYPE | Microsoft Docs"
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
  - "COLUMN_ENTRY_TYPE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COLUMN_ENTRY_TYPE 宏"
ms.assetid: ac424261-ff6c-443b-a197-2cec8d78d738
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COLUMN_ENTRY_TYPE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示绑定到数据库中的特定列。  支持 `type` 参数。  
  
## 语法  
  
```  
  
COLUMN_ENTRY_TYPE (  
nOrdinal  
,   
wType  
,   
data  
 )  
  
```  
  
#### 参数  
 `nOrdinal`  
 \[in\] 列号。  
  
 `wType`  
 \[in\] 列输入数据类型。  
  
 `data`  
 \[in\] 用户记录的相应数据成员。  
  
## 备注  
 此宏是指定数据类型提供方法 [COLUMN\_ENTRY](../../data/oledb/column-entry.md) 宏的专用变量。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板的宏和全局函数](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md)   
 [END\_COLUMN\_MAP](../../data/oledb/end-column-map.md)