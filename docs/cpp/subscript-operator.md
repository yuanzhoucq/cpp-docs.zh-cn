---
title: "下标运算符： | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "[]"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "运算符 [C++]，下标"
  - "后缀运算符"
  - "[] 运算符"
  - "下标运算符，语法"
ms.assetid: 69c31494-52da-4dd0-8bbe-6ccbfd50f197
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 下标运算符：
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
  
postfix-expression [ expression ]  
```  
  
## 备注  
 后跟下标运算符 **\[ \]** 的后缀表达式（也可为主表达式）指定数组索引。  
  
 有关托管数组的详细信息，请参阅 [数组](../windows/arrays-cpp-component-extensions.md)。  
  
 通常，*postfix\-expression* 表示的值是一个指针值（如数组标识符），*expression* 是一个整数值（包括枚举类型）。  但是，从语法上来说，只需要一个表达式是指针类型，另一个表达式是整型。  因此整数值可以位于 *postfix\-expression* 位置，指针值可以位于 *expression* 的方括号中或下标位置。  考虑以下代码片断：  
  
```  
int nArray[5] = { 0, 1, 2, 3, 4 };  
cout << nArray[2] << endl;            // prints "2"  
cout << 2[nArray] << endl;            // prints "2"  
```  
  
 在前面的示例中，表达式 `nArray[2]` 与 `2[nArray]` 相同。  原因是下标表达式 *e1***\[** *e2* **\]** 的结果由以下所示给定：  
  
 **\*\( \(** *e2* **\)** *\+* **\(***e1***\) \)**  
  
 该表达式生成的地址不是 *e1* 地址中的 *e2* 字节。  相反，该地址将进行缩放以生成数组 *e2* 中的下一个对象。  例如:  
  
```  
double aDbl[2];  
```  
  
 `aDb[0]` 和 `aDb[1]` 的地址相距 8 字节 \- **double** 类型的对象的大小。  根据对象类型进行的缩放将由 C\+\+ 语言自动完成，并在其中讨论了指针类型的操作数的加减法的[相加运算符](../cpp/additive-operators-plus-and.md)中定义。  
  
 下标表达式还可以有多个下标，如下所示：  
  
 *expression1* **\[***expression2***\] \[***expression3***\]**...  
  
 下标表达式从左至右关联。  首先计算最左侧的下标表达式 *expression1***\[***expression2***\]**。  通过添加 *expression1* 和 *expression2* 得到的地址构成一个指针表达式；然后 *expression3* 将添加到此指针表达式，从而构成一个新的指针表达式，依此类推，直到添加最后一个下标表达式。  在计算了最后的 subscripted 表达式后，将应用间接寻址运算符 \(**\***\)，除非最终指针值将为数组类型寻址。  
  
 具有多个下标的表达式引用多维数组的元素。  多维数组是其元素为数组的数组。  例如，三维数组的第一个元素是一个具有两个维度的数组。  以下示例声明并初始化字符的简单二维数组：  
  
```  
// expre_Subscript_Operator.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
#define MAX_ROWS 2  
#define MAX_COLS 2  
  
int main() {  
   char c[ MAX_ROWS ][ MAX_COLS ] = { { 'a', 'b' }, { 'c', 'd' } };  
   for ( int i = 0; i < MAX_ROWS; i++ )  
      for ( int j = 0; j < MAX_COLS; j++ )  
         cout << c[ i ][ j ] << endl;  
}  
```  
  
## 正下标和负下标  
 数组的第一个元素是元素 0。  C\+\+ 数组的范围是从 *array*\[0\] 到 *array*\[*size* – 1\]。  但是，C\+\+ 支持正负下标。  负下标必须在数组边界内；否则结果不可预知。  以下代码显示了正数组和负数组下标：  
  
```  
#include <iostream>  
using namespace std;  
  
int main() {  
    int intArray[1024];  
    for (int i = 0, j = 0; i < 1024; i++)  
    {  
        intArray[i] = j++;  
    }  
  
    cout << intArray[512] << endl;// 512  
  
    int *midArray = &intArray[512];  // pointer to the middle of the array  
  
    cout << midArray[-256] << endl;   // 256  
  
    cout << intArray[-256] << endl; // unpredictable  
}  
```  
  
 上一行中的负下标可能产生运行时错误，因为它在内存中指向比数组的原点低 256 个字节的地址。  指针 `midArray` 会初始化为 `intArray` 的中点；因此可以对其使用正数组和负数组索引。  数组下标错误不会产生编译时错误，但它们会产生不可预知的结果。  
  
 下标运算符是可交换的。  因此，只要没有重载下标运算符（请参阅*重载运算符* ），表达式 *array*\[*index*\] 和 *array*\[[array](../cpp/operator-overloading.md)\] 就一定等效。  第一种形式是最常见的编码做法，但它们都有效。  
  
## 请参阅  
 [后缀表达式](../cpp/postfix-expressions.md)   
 [C\+\+ 运算符](../misc/cpp-operators.md)   
 [C\+\+ 运算符优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [数组](../cpp/arrays-cpp.md)   
 [一维数组](../c-language/one-dimensional-arrays.md)   
 [多维数组](../c-language/multidimensional-arrays-c.md)