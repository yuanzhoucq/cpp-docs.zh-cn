---
title: "编译器错误 C3536 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3536"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3536"
ms.assetid: 8d866075-866b-49eb-9979-ee27b308f7e3
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器错误 C3536
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“symbol”: 不能在初始化之前使用  
  
 指定的符号不能在初始化之前使用。  实际上，这意味着变量不能用来对自身进行初始化。  
  
### 更正此错误  
  
1.  不要使用变量对其自身进行初始化。  
  
## 示例  
 下面的示例会产生 C3536，因为每个变量都对其自身进行初始化。  
  
```  
// C3536.cpp  
// Compile with /Zc:auto  
int main()  
{  
   auto a = a;     //C3536  
   auto b = &b;    //C3536  
   auto c = c + 1; //C3536  
   auto* d = &d;   //C3536  
   auto& e = e;    //C3536  
   return 0;  
};  
```  
  
## 请参阅  
 [auto 关键字](../../cpp/auto-keyword.md)