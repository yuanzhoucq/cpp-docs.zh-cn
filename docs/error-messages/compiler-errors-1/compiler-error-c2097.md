---
title: "编译器错误 C2097 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2097"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2097"
ms.assetid: 7e5b2fd4-f61c-4b8a-b265-93e987a04bd3
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器错误 C2097
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

非法的初始化  
  
### 通过检查以下可能的原因进行修复  
  
1.  使用非常数值初始化变量。  
  
2.  用长地址初始化短地址。  
  
3.  在用 **\/Za** 编译时，用非常数表达式初始化局部结构、联合或数组。  
  
4.  用包含逗号运算符的表达式初始化。  
  
5.  用既非常数又非符号的表达式初始化。