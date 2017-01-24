---
title: "Variadic 宏 | Microsoft Docs"
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
  - "variadic 宏 [C++]"
  - "__VA_ARGS__ variadic 宏说明符"
ms.assetid: 51e757dc-0134-4bb2-bb74-64ea5ad75134
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Variadic 宏
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Variadic 宏是包含了数量不定的参数类似于函数的宏。  
  
## 备注  
 若要使用 variadic 宏，省略号可以在宏定义中被指定为最终的正式自变量，并且替换标识符 `__VA_ARGS__` 可用于定义插入额外的参数。`__VA_ARGS__`并被相匹配的省略号，包括他们之间的逗号等所有的自变量所替换  
  
 C 标准指定必须将至少一个参数分配省略号，确保该宏不能解析为与一个尾随逗号的表达式。如果没有参数传递给省略号，Visual C\+\+ 实现会禁止尾随逗号。  
  
## 示例  
  
```cpp  
// variadic_macros.cpp  
#include <stdio.h>  
#define EMPTY  
  
#define CHECK1(x, ...) if (!(x)) { printf(__VA_ARGS__); }  
#define CHECK2(x, ...) if ((x)) { printf(__VA_ARGS__); }  
#define CHECK3(...) { printf(__VA_ARGS__); }  
#define MACRO(s, ...) printf(s, __VA_ARGS__)  
  
int main() {  
    CHECK1(0, "here %s %s %s", "are", "some", "varargs1(1)\n");  
    CHECK1(1, "here %s %s %s", "are", "some", "varargs1(2)\n");   // won't print  
  
    CHECK2(0, "here %s %s %s", "are", "some", "varargs2(3)\n");   // won't print  
    CHECK2(1, "here %s %s %s", "are", "some", "varargs2(4)\n");  
  
    // always invokes printf in the macro  
    CHECK3("here %s %s %s", "are", "some", "varargs3(5)\n");  
  
    MACRO("hello, world\n");  
  
    MACRO("error\n", EMPTY); // would cause error C2059, except VC++   
                             // suppresses the trailing comma  
}  
```  
  
## Output  
  
```  
here are some varargs1(1)  
here are some varargs2(4)  
here are some varargs3(5)  
hello, world  
error  
  
```  
  
## 请参阅  
 [宏](../preprocessor/macros-c-cpp.md)