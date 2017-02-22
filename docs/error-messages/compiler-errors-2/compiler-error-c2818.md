---
title: "编译器错误 C2818 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2818"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2818"
ms.assetid: 715fc7c9-0c6d-452b-b7f5-1682cea5e907
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C2818
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

重载“operator \-\>”的应用程序通过类型“type”进行递归  
  
 类成员访问运算符的重定义包含递归的 `return` 语句。  若要重新定义具有递归的 `->` 运算符，则必须将递归例程移动到从该运算符重写函数调用的单独函数中。