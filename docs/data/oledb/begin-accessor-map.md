---
title: "BEGIN_ACCESSOR_MAP | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BEGIN_ACCESSOR_MAP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BEGIN_ACCESSOR_MAP 宏"
ms.assetid: e6d6e3a4-62fa-4e49-8c53-caf8c9d20091
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# BEGIN_ACCESSOR_MAP
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

标记取值函数映射条目的开始。  
  
## 语法  
  
```  
  
BEGIN_ACCESSOR_MAP(  
x  
,   
num  
 )  
  
```  
  
#### 参数  
 *x*  
 \[in\] 用户记录类的名称。  
  
 *num*  
 \[in\] 此取值函数映射中的取值函数数目。  
  
## 备注  
 如果某个行集上有多个取值函数，则需要在开头指定 `BEGIN_ACCESSOR_MAP` 并对每个单独的取值函数使用 `BEGIN_ACCESSOR` 宏。`BEGIN_ACCESSOR` 宏以 `END_ACCESSOR` 宏结束。 取值函数映射以 `END_ACCESSOR_MAP` 宏结束。  
  
 如果在用户记录中只有一个取值函数，则使用宏 [BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md)。  
  
## 示例  
 [!CODE [NVC_OLEDB_Consumer#15](../CodeSnippet/VS_Snippets_Cpp/NVC_OLEDB_Consumer#15)]  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板的宏和全局函数](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [END\_ACCESSOR](../../data/oledb/end-accessor.md)   
 [END\_ACCESSOR\_MAP](../../data/oledb/end-accessor-map.md)