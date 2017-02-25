---
title: "编译器错误 C3540 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3540"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3540"
ms.assetid: 3c0c959c-e3b7-40eb-b922-ccac44bd9d85
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C3540
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”: sizeof 不能应用于包含“auto”的类型  
  
 [sizeof](../../cpp/sizeof-operator.md) 运算符不能应用于指定的类型，因为它包含 `auto` 说明符。  
  
## 示例  
 下面的示例会产生 C3540。  
  
```  
// C3540.cpp  
// Compile with /Zc:auto  
int main() {  
    auto x = 123;  
    sizeof(x);    // OK  
    sizeof(auto); // C3540  
    return 0;  
}  
```  
  
## 请参阅  
 [auto 关键字](../../cpp/auto-keyword.md)   
 [\/Zc:auto（推导变量类型）](../../build/reference/zc-auto-deduce-variable-type.md)   
 [sizeof 运算符](../../cpp/sizeof-operator.md)