---
title: "宏替换 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "宏, NMAKE"
  - "NMAKE 程序, 宏替换"
  - "NMAKE 中的替换宏"
ms.assetid: 47465cfe-fd92-49db-aebe-7c2d7ecceb73
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 宏替换
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

调用 *macroname* 时，其定义字符串中 *string1* 的每个匹配项由 *string2* 替换。  
  
## 语法  
  
```  
$(macroname:string1=string2)  
```  
  
## 备注  
 宏替换区分大小写，并且是文本；*string1* 和 *string2* 不能调用宏。  替换不修改原始定义。  可以替换任何预定义宏（[$$@](../build/filename-macros.md)除外）中的文本。  
  
 冒号前面没有空格或制表符；冒号后面的任何空格或制表符均被解释为文本。  如果 *string2* 为空，将从宏的定义字符串中删除 *string1* 的所有匹配项。  
  
## 请参阅  
 [使用 NMAKE 宏](../build/using-an-nmake-macro.md)