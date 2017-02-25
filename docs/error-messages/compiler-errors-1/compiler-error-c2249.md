---
title: "编译器错误 C2249 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2249"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2249"
ms.assetid: bdd6697c-e04b-49b9-8e40-d9eb6d74f2b6
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 编译器错误 C2249
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“member”: 没有到 access member \(在“class”虚拟基中声明\)的访问路径  
  
 该 `member` 是从非公共 `virtual` 基类或结构继承的。  
  
## 示例  
 下面的示例生成 C2249。  
  
```  
// C2249.cpp  
class A {  
private:  
   void privFunc( void ) {};  
public:  
   void pubFunc( void ) {};  
};  
  
class B : virtual public A {} b;  
  
int main() {  
   b.privFunc();    // C2249, private member of A  
   b.pubFunc();    // OK  
}  
```  
  
## 示例  
 如果尝试从标准 C\+\+ 库中将一个流分配给另一个流，则也可能发生 C2249 错误。下面的示例生成 C2249。  
  
```  
// C2249_2.cpp  
#include <iostream>  
using namespace std;  
int main() {  
   cout = cerr;   // C2249  
   #define cout cerr;   // OK  
}  
```