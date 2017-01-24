---
title: "错误 C1054 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1054"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1054"
ms.assetid: 9cfb7307-b22a-4418-b7c0-2621b0ab5b1b
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 错误 C1054
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

编译器限制 : 初始值设定项嵌套太深  
  
 代码超过初始值设定项的嵌套限制（10 到 15 级，取决于初始化的类型组合）。  
  
### 通过使用下面可能的解决方案进行修复  
  
1.  简化初始化的数据类型以减少嵌套。  
  
2.  声明后在单独的语句中初始化变量。