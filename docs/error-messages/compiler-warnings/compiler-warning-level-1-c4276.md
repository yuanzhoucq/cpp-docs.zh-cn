---
title: "编译器警告（等级 1）C4276 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4276"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4276"
ms.assetid: 9d738c2d-29e5-408a-b9ff-be1a850b2238
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告（等级 1）C4276
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 不提供原型；假定无参数  
  
 当使用 [\_\_stdcall](../../cpp/stdcall.md) 调用约定获取函数地址时，必须提供原型，以便编译器可以创建函数的修饰名。  由于 *function* 没有原型，编译器在创建修饰名时假定函数没有参数。