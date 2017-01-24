---
title: "auto_inline | Microsoft Docs"
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
  - "auto_inline_CPP"
  - "vc-pragma.auto_inline"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "auto_inline 杂注"
  - "杂注, auto_inline"
ms.assetid: f7624cd1-be76-429a-881c-65c9040acf43
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# auto_inline
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将指定了 **off** 的范围内定义的所有函数从考虑为自动内联扩展的候选项中排除。  
  
## 语法  
  
```  
  
#pragma auto_inline( [{on | off}] )  
```  
  
## 备注  
 若要使用 **auto\_inline** 杂注，请将其放置在函数定义之前和紧靠定义之后（不在定义中）。  杂注在出现的位置后的第一个函数定义处生效。  
  
## 请参阅  
 [Pragma 指令和 \_\_Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)