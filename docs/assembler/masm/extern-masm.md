---
title: "EXTERN (MASM) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "extern"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "EXTERN directive"
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# EXTERN (MASM)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

定义名为类型是 `type`*名称的* 一个或多个外部变量、标签或符号。  
  
## 语法  
  
```  
  
   EXTERN [[langtype]] name [[(altid)]] :  
type [[, [[langtype]] name [[(altid)]] :type]]...  
```  
  
## 备注  
 `type` 可以是 [abs](../../assembler/masm/operator-abs.md)，导入 *名称* 为常数。  和 [EXTRN](../../assembler/masm/extrn.md)相同。  
  
## 请参阅  
 [Directives Reference](../../assembler/masm/directives-reference.md)