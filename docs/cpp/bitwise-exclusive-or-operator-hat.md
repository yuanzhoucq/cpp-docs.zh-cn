---
title: "按位异或运算符：^ | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "^ 运算符"
  - "按位运算符, OR 运算符"
  - "异或运算符"
  - "运算符 [C++], 按位"
  - "运算符 [C++], 逻辑"
  - "OR 运算符, 按位异"
  - "XOR 运算符"
ms.assetid: f9185d85-65d5-4f64-a6d6-679758d52217
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 按位异或运算符：^
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
expression ^ expression  
```  
  
## 备注  
 按位“异或”运算符 \(**^**\) 将第一操作数的每个位与第二操作数的相应位进行比较。  如果一个位是 0，另一个位是 1，则相应的结果位将设置为 1。  否则，将对应的结果位设置为 0。  
  
 按位“异或”运算符的两个操作数都必须为整型。  [算术转换](../misc/arithmetic-conversions.md)中涵盖的常用算术转换适用于操作数。  
  
## ^ 的运算符关键字  
 **xor** 运算符是与 **^** 等效的文本。  在您的程序中，可通过两种方法访问 **xor** 运算符：包含头文件 `iso646.h`，或使用 [\/Za](../build/reference/za-ze-disable-language-extensions.md)（禁用语言扩展）编译器选项进行编译。  
  
## 示例  
  
```  
// expre_Bitwise_Exclusive_OR_Operator.cpp  
// compile with: /EHsc  
// Demonstrate bitwise exclusive OR  
#include <iostream>  
using namespace std;  
int main() {  
   unsigned short a = 0x5555;      // pattern 0101 ...  
   unsigned short b = 0xFFFF;      // pattern 1111 ...  
  
   cout  << hex << ( a ^ b ) << endl;   // prints "aaaa" pattern 1010 ...  
}  
```  
  
## 请参阅  
 [C\+\+ 按位运算符](../misc/cpp-bitwise-operators.md)   
 [C\+\+ 运算符](../misc/cpp-operators.md)   
 [C\+\+ 运算符优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [C 按位运算符](../c-language/c-bitwise-operators.md)