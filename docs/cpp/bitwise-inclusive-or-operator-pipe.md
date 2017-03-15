---
title: "按位与或运算符：| | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "bitor"
  - "|"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "| 运算符"
  - "按位运算符, OR 运算符"
  - "与或运算符"
  - "OR 运算符, 按位与"
ms.assetid: 4c8a6a68-d828-447d-875a-aedb4ce3aa9a
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 按位与或运算符：|
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
  
expression   
|  
 expression  
  
```  
  
## 备注  
 按位“与或”运算符 \(         **&#124;** \) 将第一个操作数的每个位与第二个操作数的对应位进行比较。  如果其中一个位是 1，则将对应的结果位设置为 1。  否则，将对应的结果位设置为 0。  
  
 按位“与或”运算符的两个操作数必须为整型。  [算术转换](../misc/arithmetic-conversions.md)中涵盖的常用算术转换适用于操作数。  
  
## &#124; 的运算符关键字  
 `bitor` 运算符是             **&#124;** 的文本等效项。  访问程序中的 `bitor` 运算符有两种方式：包括头文件 `iso646.h`，或使用 [\/Za](../build/reference/za-ze-disable-language-extensions.md)（禁用语言扩展）编译器选项进行编译。  
  
## 示例  
  
```  
// expre_Bitwise_Inclusive_OR_Operator.cpp  
// compile with: /EHsc  
// Demonstrate bitwise inclusive OR  
#include <iostream>  
using namespace std;  
  
int main() {  
   unsigned short a = 0x5555;      // pattern 0101 ...  
   unsigned short b = 0xAAAA;      // pattern 1010 ...  
  
   cout  << hex << ( a | b ) << endl;   // prints "ffff" pattern 1111 ...  
}  
```  
  
## 请参阅  
 [C\+\+ 按位运算符](../misc/cpp-bitwise-operators.md)   
 [C\+\+ 运算符](../misc/cpp-operators.md)   
 [C\+\+ 运算符优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [C 按位运算符](../c-language/c-bitwise-operators.md)