---
title: "编译器错误 C2677 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2677"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2677"
ms.assetid: 76bc0b65-f52a-45a6-b6d6-0555f89da9a8
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C2677
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

二元“operator”: 没有找到接受“type”类型的全局运算符\(或没有可接受的转换\)  
  
 若要使用该运算符，必须针对指定类型将其重载，或者定义一个到某个类型（该运算符已针对此类型进行了定义）的转换。  
  
 下面的示例生成 C2677：  
  
```  
// C2677.cpp  
class C {  
public:  
   C(){}  
} c;  
  
class D {  
public:  
   D(){}  
   operator int(){return 0;}  
} d;  
  
int main() {  
   int i = 1 >> c;   // C2677  
   int j = 1 >> d;   // OK operator int() defined  
}  
```