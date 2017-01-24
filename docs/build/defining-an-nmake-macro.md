---
title: "定义 NMAKE 宏 | Microsoft Docs"
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
  - "定义 NMAKE 宏"
  - "宏, NMAKE"
  - "NMAKE 宏, 定义"
ms.assetid: 45aae451-9d33-4a3d-8799-2e0cae17070d
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 定义 NMAKE 宏
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
  
macroname=string  
```  
  
## 备注  
 *macroname* 是字母、数字和下划线 \(\_\) 的组合，最多 1,024 个字符且区分大小写。  *macroname* 可以包含调用的宏。  如果 *macroname* 完全是由调用的宏组成的，则正调用的宏不能为空或未定义。  
  
 `string` 可以是零个或多个字符的任意序列。  空字符串包含零个字符或只有空格或制表符。  `string` 可以包含宏调用。  
  
## 您想进一步了解什么？  
 [宏内的特殊字符](../build/special-characters-in-macros.md)  
  
 [空宏和未定义的宏](../build/null-and-undefined-macros.md)  
  
 [定义宏的位置](../build/where-to-define-macros.md)  
  
 [宏定义中的优先级](../build/precedence-in-macro-definitions.md)  
  
## 请参阅  
 [宏和 NMAKE](../build/macros-and-nmake.md)