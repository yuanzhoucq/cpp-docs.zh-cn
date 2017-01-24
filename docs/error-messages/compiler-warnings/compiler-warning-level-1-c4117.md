---
title: "编译器警告（等级 1）C4117 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4117"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4117"
ms.assetid: c45aa281-4cc1-4dfd-bd32-bd7a60ddd577
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4117
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

保留“name”宏名；已忽略“Command”  
  
### 通过检查以下可能的原因进行修复  
  
1.  尝试定义或取消定义预定义的宏。  
  
2.  尝试定义或取消定义预处理器运算符 **defined**。  
  
 以下示例生成 C4117：  
  
```  
// C4117.cpp // compile with: /W1 #define __FILE__ test         // C4117. __FILE__ is a predefined macro #define ValidMacroName test   // ok int main() { }  
```