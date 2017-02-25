---
title: "编译器错误 C2653 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2653"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2653"
  - "CDaoRecordset 类, 添加记录"
ms.assetid: 3f49e731-affd-43a0-a8d0-181db7650bc3
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C2653
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 不是类或命名空间名称  
  
 语法需要类、结构、联合或命名空间名称。  
  
 下面的示例生成 C2653：  
  
```  
// C2653.cpp  
// compile with: /c  
class yy {  
   void func1(int i);  
};  
  
void xx::func1(int m) {}   // C2653  
void yy::func1(int m) {}   // OK  
```  
  
 如果尝试定义复合命名空间，也可能会发生 C2653；C\+\+ 中不允许复合命名空间：  
  
```  
// C2653b.cpp  
namespace a::b {int i;}   // C2653  
  
namespace a {  
   namespace b {  
      int i;  
   }  
}  
  
int main() {  
   a::b::i = 2;  
}  
```