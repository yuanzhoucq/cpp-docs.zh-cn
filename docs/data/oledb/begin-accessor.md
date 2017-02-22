---
title: "BEGIN_ACCESSOR | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BEGIN_ACCESSOR"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BEGIN_ACCESSOR 宏"
  - "BEGIN_ACCESSOR 宏, 语法"
ms.assetid: 59d0ff3e-7cfd-4ce8-9a1c-d664c0892a52
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# BEGIN_ACCESSOR
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

标记访问函数入口的开头。  
  
## 语法  
  
```  
  
BEGIN_ACCESSOR(  
num  
,   
bAuto  
 )  
  
```  
  
#### 参数  
 *num*  
 \[in\] 访问器的零数字的偏移此访问器映射。  
  
 *bAuto*  
 \[in\] 指定此访问器是否为自动访问器或手动访问器。一  如果 **true**，访问器都是自动的；如果 **false**，手动访问器。  为自动访问器这意味着数据指定要提取移动操作。  
  
## 备注  
 对于行集合上具有多个访问器，需要指定 `BEGIN_ACCESSOR_MAP` 和对每个访问器使用 `BEGIN_ACCESSOR` 宏。  完成 `BEGIN_ACCESSOR` 宏与 `END_ACCESSOR` 宏。  完成 `BEGIN_ACCESSOR_MAP` 宏与 `END_ACCESSOR_MAP` 宏。  
  
## 示例  
 参见 [BEGIN\_ACCESSOR\_MAP](../../data/oledb/begin-accessor-map.md)。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板的宏和全局函数](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN\_ACCESSOR\_MAP](../../data/oledb/begin-accessor-map.md)   
 [END\_ACCESSOR](../../data/oledb/end-accessor.md)   
 [END\_ACCESSOR\_MAP](../../data/oledb/end-accessor-map.md)