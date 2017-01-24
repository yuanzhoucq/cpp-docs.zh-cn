---
title: "函数调用转换 | Microsoft Docs"
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
  - "C"
helpviewer_keywords: 
  - "函数调用, 参数类型转换"
  - "函数调用, 转换"
  - "函数 [C], 参数转换"
ms.assetid: 04ea0f81-509a-4913-8b12-0937a81babcf
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 函数调用转换
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

对函数调用中的参数执行的转换的类型取决于是否存在具有调用的函数的声明参数类型的函数原型（前向声明）。  
  
 如果函数原型存在并包含声明的参数类型，编译器将执行类型检查（请参阅[函数](../c-language/functions-c.md)）。  
  
 如果函数原型不存在，则只对函数调用中的参数执行常用算术转换。  这些转换独立于调用中的每个参数执行。  这意味着 **float** 值被转换为 **double**；`char` 或 **short** 值被转换为 `int`；并且 `unsigned char` 或 **unsigned short** 被转换为 `unsigned int`。  
  
## 请参阅  
 [类型转换](../c-language/type-conversions-c.md)