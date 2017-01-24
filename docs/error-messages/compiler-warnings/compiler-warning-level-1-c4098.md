---
title: "编译器警告（等级 1）C4098 | Microsoft Docs"
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
  - "C4098"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4098"
ms.assetid: 8c8aef1c-1639-44ec-a3dd-c0dfe9aa727d
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4098
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: void 函数返回一个值  
  
 用返回类型 [void](../../cpp/void-cpp.md) 声明的函数有 `return` 语句，该语句返回一个值。  编译器假定该函数返回类型为 `int` 的值。