---
title: "编译器错误 C2781 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2781"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2781"
ms.assetid: f29b9963-f55b-427c-8db6-50f37713df5a
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C2781
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“declaration”: 应输入至少 value1 个参数，却提供了 value2 个  
  
 具有变量参数列表的函数模板的参数太少。  
  
 下面的示例生成 C2781：  
  
```  
// C2781.cpp  
template<typename T>  
void f(T, T, ...){}  
  
int main() {  
   f(1);   // C2781  
  
   // try the following line instead  
   f(1,1);  
}  
```