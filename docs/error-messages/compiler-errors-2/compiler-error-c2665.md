---
title: "编译器错误 C2665 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2665"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2665"
ms.assetid: a7f99b61-2eae-4f2b-ba75-ea68fd1e8312
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 编译器错误 C2665
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: number1 个重载中没有一个可以转换参数 number2 \(从“type”类型\)  
  
 该重载函数的参数无法转换为所需类型。可能的解决方案：  
  
-   提供转换运算符。  
  
-   使用显式转换。  
  
## 示例  
 下面的示例生成 C2665。  
  
```  
// C2665.cpp  
void func(short, char*){}  
void func(char*, char*){}  
  
int main() {  
   func(0, 1);   // C2665  
   func((short)0, (char*)1);   // OK  
}  
```