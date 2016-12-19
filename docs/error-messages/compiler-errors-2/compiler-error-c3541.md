---
title: "编译器错误 C3541 | Microsoft Docs"
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
  - "C3541"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3541"
ms.assetid: 252cfd4c-5fd2-415e-a17d-6b0c254350db
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3541
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”: typeid 不能应用于包含“auto”的类型  
  
 [typeid](../../windows/typeid-cpp-component-extensions.md) 运算符不能应用于指定的类型，因为它包含 `auto` 说明符。  
  
## 示例  
 下面的示例会产生 C3541。  
  
```  
// C3541.cpp  
// Compile with /Zc:auto  
#include <typeinfo>  
int main() {  
    auto x = 123;  
    typeid(x);    // OK  
    typeid(auto); // C3541  
    return 0;  
}  
```  
  
## 请参阅  
 [auto 关键字](../../cpp/auto-keyword.md)   
 [\/Zc:auto（推导变量类型）](../../build/reference/zc-auto-deduce-variable-type.md)   
 [typeid](../../windows/typeid-cpp-component-extensions.md)