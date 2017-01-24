---
title: "简单赋值 (C) | Microsoft Docs"
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
  - "赋值运算符 [C++], 简单"
  - "数据类型转换 [C++], 简单赋值"
  - "等号"
  - "运算符 [C], 简单赋值"
  - "简单赋值运算符"
  - "类型转换 [C++], 简单赋值"
ms.assetid: e7140a0a-7104-4b3a-b293-7adcc1fdd52b
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 简单赋值 (C)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

简单赋值运算符可将其右操作数赋给其左操作数。  右操作数的值将转换为赋值表达式的类型，并替换存储在左侧操作数指定的对象中的值。  用于赋值的转换规则适用（请参阅[赋值转换](../c-language/assignment-conversions.md)）。  
  
```  
double x;  
int y;  
  
x = y;  
```  
  
 在此示例中，`y` 将转换为类型 **double** 并赋给 `x`。  
  
## 请参阅  
 [C 赋值运算符](../c-language/c-assignment-operators.md)