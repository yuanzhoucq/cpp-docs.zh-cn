---
title: "BEGIN_COLUMN_MAP | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BEGIN_COLUMN_MAP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BEGIN_COLUMN_MAP 宏"
ms.assetid: d6ffe633-e0da-4e33-8faa-f7f259d05420
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# BEGIN_COLUMN_MAP
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

标记列映射条目的开头。  
  
## 语法  
  
```  
  
BEGIN_COLUMN_MAP(  
x  
 )  
  
```  
  
#### 参数  
 *x*  
 \[in\] 派生自 `CAccessor` 的用户记录类的名称。  
  
## 备注  
 在行集上存在单个访问器的情况下使用此宏。 如果行集上有多个访问器，则使用 [BEGIN\_ACCESSOR\_MAP](../../data/oledb/begin-accessor-map.md)。  
  
 `BEGIN_COLUMN_MAP` 宏以 `END_COLUMN_MAP` 宏结束。 当用户记录中只需要一个访问器时才使用此宏。  
  
 列对应行集中你希望绑定的字段。  
  
## 示例  
 以下是示例列和参数映射：  
  
 [!CODE [NVC_OLEDB_Consumer#16](../CodeSnippet/VS_Snippets_Cpp/NVC_OLEDB_Consumer#16)]  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板的宏和全局函数](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [END\_COLUMN\_MAP](../../data/oledb/end-column-map.md)   
 [COLUMN\_ENTRY](../../data/oledb/column-entry.md)   
 [COLUMN\_ENTRY\_EX](../../data/oledb/column-entry-ex.md)