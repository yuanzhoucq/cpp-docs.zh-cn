---
title: "Compiler Error C2919 | Microsoft Docs"
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
  - "C2919"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2919"
ms.assetid: 140a6db9-eb48-4c5e-84a7-a09d2653605b
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Compiler Error C2919
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”：不能在 WinRT 类型的发布接口上使用运算符  
  
 Windows 运行时类型系统不支持某类型的发布接口中的运算符成员函数。  这是因为并非所有语言都能使用运算符成员函数。  你可以创建可从相同类或编译单元中的 C\+\+ 代码调用的私有或内部运算符成员函数。  
  
 要修复此问题，请将运算符成员函数从公共接口中删除，或将其更改为命名成员函数。  例如，将成员函数命名为 `Equals`，而不是使用 `operator==`。