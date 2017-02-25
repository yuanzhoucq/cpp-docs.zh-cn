---
title: "push_macro | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-pragma.push_macro"
  - "push_macro_CPP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "杂注, push_macro"
  - "push_macro 杂注"
ms.assetid: ac89efc9-afd1-4dfe-bfd1-497229b3e81d
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# push_macro
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在堆栈顶端为此宏保存 *macro\_name* 宏的值。  
  
## 语法  
  
```  
  
#pragma push_macro("  
macro_name  
")  
  
```  
  
## 备注  
 可以使用 **pop\_macro** 检索 *macro\_name* 的值。  
  
 有关示例，请参阅 [pop\_macro](../preprocessor/pop-macro.md)。  
  
## 请参阅  
 [Pragma 指令和 \_\_Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)