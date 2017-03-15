---
title: "COLUMN_ENTRY_TYPE_SIZE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "COLUMN_ENTRY_TYPE_SIZE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COLUMN_ENTRY_TYPE_SIZE 宏"
ms.assetid: d8b169e8-af22-464b-8cb3-eaa346f7a739
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# COLUMN_ENTRY_TYPE_SIZE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示绑定到数据库中的特定列。  支持 `type` 和 `size` 参数。  
  
## 语法  
  
```  
  
COLUMN_ENTRY_TYPE_SIZE(  
nOrdinal  
,   
wType  
,   
nLength  
,   
data  
 )  
  
```  
  
#### 参数  
 `nOrdinal`  
 \[in\] 列数。  
  
 `wType`  
 \[in\] 列输入数据类型。  
  
 `nLength`  
 \[in\] 输入列的大小 \(以字节为单位\)。  
  
 `data`  
 \[in\] 用户记录的相应数据成员。  
  
## 备注  
 此宏是提供指定数据类型和大小方法 [COLUMN\_ENTRY](../../data/oledb/column-entry.md) 宏的专用变量。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板的宏和全局函数](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md)   
 [END\_COLUMN\_MAP](../../data/oledb/end-column-map.md)