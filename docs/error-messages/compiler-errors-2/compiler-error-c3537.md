---
title: "编译器错误 C3537 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3537"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3537"
ms.assetid: f537ebd1-4fb0-4e09-a453-4f38db2c6881
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器错误 C3537
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”: 不能强制转换为包含“auto”的类型  
  
 不能将变量强制转换为指定的类型，因为该类型包含 `auto` 关键字并且默认 [\/Zc:auto](../../build/reference/zc-auto-deduce-variable-type.md) 编译器选项有效。  
  
## 示例  
 下面的代码会产生 C3537，因为这些变量强制转换为包含 `auto` 关键字的类型。  
  
```  
// C3537.cpp  
// Compile with /Zc:auto  
int main()  
{  
   int value = 123;  
   auto(value);                        // C3537  
   (auto)value;                        // C3537  
   auto x1 = auto(value);              // C3537  
   auto x2 = (auto)value;              // C3537  
   auto x3 = static_cast<auto>(value); // C3537  
   return 0;  
}  
```  
  
## 请参阅  
 [auto 关键字](../../cpp/auto-keyword.md)