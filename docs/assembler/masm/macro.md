---
title: "MACRO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MACRO"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MACRO directive"
ms.assetid: 89434f7c-bc2c-4e91-8940-fe2db8785233
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# MACRO
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

，当宏调用时，标记宏块调用的 *名称* 并建立传递的参数的 *参数* 占位符。  
  
## 语法  
  
```  
  
   name MACRO [[parameter [[:REQ | :=default | :VARARG]]]]...  
statements  
ENDM [[value]]  
```  
  
## 备注  
 宏将 *值* 返回给调用语句。  
  
## 请参阅  
 [Directives Reference](../../assembler/masm/directives-reference.md)