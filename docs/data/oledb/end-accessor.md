---
title: "END_ACCESSOR | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "END_ACCESSOR"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "END_ACCESSOR 宏"
ms.assetid: 26f74167-68c4-4909-a474-73dc7ebc9542
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# END_ACCESSOR
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

标记访问函数入口的结尾。  
  
## 语法  
  
```  
  
END_ACCESSOR( )  
  
```  
  
## 备注  
 对于行集合上具有多个访问器，需要指定 `BEGIN_ACCESSOR_MAP` 和对每个单独的访问器使用 `BEGIN_ACCESSOR` 宏。  完成 `BEGIN_ACCESSOR` 宏与 `END_ACCESSOR` 宏。  完成 `BEGIN_ACCESSOR_MAP` 宏与 `END_ACCESSOR_MAP` 宏。  
  
## 示例  
 参见 [BEGIN\_ACCESSOR\_MAP](../../data/oledb/begin-accessor-map.md)。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板的宏和全局函数](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN\_ACCESSOR\_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [END\_ACCESSOR\_MAP](../../data/oledb/end-accessor-map.md)