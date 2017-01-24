---
title: "加法运算符：+ 和 - | Microsoft Docs"
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
  - "-"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "- 运算符, C++ 中的加法运算符"
  - "+ 运算符, 加法运算符"
  - "加法运算符"
  - "算术运算符 [C++], 加法运算符"
  - "运算符 [C++], 加法"
  - "减法运算符, 加法运算符"
ms.assetid: d4afafe7-e201-4c69-a649-37f17756e784
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 加法运算符：+ 和 -
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
expression + expression   
expression – expression  
```  
  
## 备注  
 相加运算符为：  
  
-   加 \(**\+**\)  
  
-   减 \(**–**\)  
  
 这些二进制运算符具有从左至右的关联性。  
  
 相加运算符采用算术或指针类型的操作数。  加法 \(**\+**\) 运算符的结果是操作数之和。  减法 \(**–**\) 运算符的结果是操作数之差。  如果一个操作数是指针或两个操作数都是指针，则它们必须是指向对象的指针，而不是指向函数的指针。  如果两个操作数都是指针，则结果没有意义，除非它们是指向同一数组中的对象的指针。  
  
 相加运算符采用 *arithmetic*、*integral* 和 *scalar* 类型的操作数。  下表定义了这些操作数。  
  
### 用于相加运算符的类型  
  
|类型|含义|  
|--------|--------|  
|*arithmetic*|整型和浮点类型统称为“算术”类型。|  
|*integral*|所有大小（long、short）和枚举数的 char 和 int 类型为“整数”类型。|  
|*scalar*|标量操作数是算术类型或指针类型的操作数。|  
  
 这些运算符的合法组合为：  
  
 *算术* \+ *算术*  
  
 *标量* \+ *整数*  
  
 *整数* \+ *标量*  
  
 *算术* – *算术*  
  
 *标量* – *标量*  
  
 请注意，加法和减法不是等效运算。  
  
 如果两个操作数都是算术类型，则[算术转换](../misc/arithmetic-conversions.md)中介绍的转换适用于这两个操作数，并且结果为已转换的类型。  
  
## 示例  
  
```  
// expre_Additive_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
#define SIZE 5  
using namespace std;  
int main() {  
   int i = 5, j = 10;  
   int n[SIZE] = { 0, 1, 2, 3, 4 };  
   cout  << "5 + 10 = " << i + j << endl  
         << "5 - 10 = " << i - j << endl;  
  
   // use pointer arithmetic on array  
  
   cout << "n[3] = " << *( n + 3 ) << endl;  
}  
```  
  
## 指针加法  
 在加法运算中，如果其中一个操作数是指向对象数组的指针，则另一个操作数必须是整型。  结果为与原始指针类型相同的指针和指向另一个数组元素的指针。  以下代码片段阐述了此概念：  
  
```  
short IntArray[10]; // Objects of type short occupy 2 bytes  
short *pIntArray = IntArray;  
  
for( int i = 0; i < 10; ++i )  
{  
    *pIntArray = i;  
    cout << *pIntArray << "\n";  
    pIntArray = pIntArray + 1;  
}  
```  
  
 虽然将整数值 1 添加到 `pIntArray`，但这并不表示“将 1 添加到该地址”，而是指“调整指针使其指向数组中的下一个对象”，而该对象恰好是在 2 字节（或者 `sizeof( int )`）之外。  
  
> [!NOTE]
>  在 C\+\+ 程序中很少找到 `pIntArray = pIntArray + 1` 形式的代码；若要实现递增，以下形式更可取：`pIntArray++` 或 `pIntArray += 1`。  
  
## 指针减法  
 如果两个操作数都是指针，则减法运算的结果就是两个操作数之差（在数组元素中）。  减法表达式产生类型 ptrdiff\_t（在标准包含文件 STDDEF.H 中定义）的带符号的整数结果。  
  
 其中一个操作数可以是整型，条件是该操作数是第二操作数。  减法的结果的类型与原始指针的类型相同。  减法的值是指向第 \(*n* – *i*\) 个数组元素的指针，其中 *n* 是由原始指针指向的元素，而 *i* 是第二操作数的整数值。  
  
## 请参阅  
 [使用二元运算符的表达式](../cpp/expressions-with-binary-operators.md)   
 [C\+\+ 运算符](../misc/cpp-operators.md)   
 [C\+\+ 运算符优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [指针加法类型](../misc/addition-of-pointer-types.md)   
 [指针减法类型](../misc/subtraction-of-pointer-types.md)   
 [C 加法运算符](../c-language/c-additive-operators.md)