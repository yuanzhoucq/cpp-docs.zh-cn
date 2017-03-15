---
title: "编译器警告（等级 2）C4244 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4244"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4244"
ms.assetid: 2c19d157-21d1-42c2-a6c0-3f30f2ce3813
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器警告（等级 2）C4244
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“argument”: 从“type1”转换到“type2”可能丢失数据  
  
 浮点类型已转换为 integer 类型。可能发生了数据丢失。  
  
 如果获取 C4244，则应将程序更改为使用兼容类型，或向代码中添加一些逻辑，以确保可能值的范围始终与所使用的类型兼容。  
  
 C4244 也会在等级 3 和等级 4 激发；有关更多信息，请参见 [编译器警告（等级 3 和等级 4）C4244](../../error-messages/compiler-warnings/compiler-warning-levels-3-and-4-c4244.md)。  
  
## 示例  
 下面的示例生成 C4244：  
  
```  
// C4244_level2.cpp  
// compile with: /W2  
  
int f(int x){ return 0; }  
int main() {  
   double x = 10.1;  
   int i = 10;  
   return (f(x));   // C4244  
   // try the following line instead  
   // return (f(i));  
}  
```