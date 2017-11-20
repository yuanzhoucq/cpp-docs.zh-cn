---
title: "下标运算符: |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '[]'
dev_langs: C++
helpviewer_keywords:
- operators [C++], subscript
- postfix operators [C++]
- '[] operator'
- subscript operator [C++], syntax
ms.assetid: 69c31494-52da-4dd0-8bbe-6ccbfd50f197
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e1b40b16c3ee349419259ae1e2240e28e3e7e911
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="subscript-operator"></a>下标运算符：
## <a name="syntax"></a>语法  
  
```  
  
postfix-expression [ expression ]  
```  
  
## <a name="remarks"></a>备注  
 后缀表达式 （这也可以是主表达式） 跟下标运算符， **[]**，指定数组索引。  
  
 有关托管数组的信息，请参阅[数组](../windows/arrays-cpp-component-extensions.md)。  
  
 通常情况下，由表示的值*后缀表达式*是一个指针值，如数组标识符，和*表达式*是一个整数值 （包括枚举的类型）。 但是，从语法上来说，只需要一个表达式是指针类型，另一个表达式是整型。 因此整数值可以位于*后缀表达式*位置，指针值可以在方括号中*表达式*或下标位置。 考虑以下代码片断：  
  
```  
int nArray[5] = { 0, 1, 2, 3, 4 };  
cout << nArray[2] << endl;            // prints "2"  
cout << 2[nArray] << endl;            // prints "2"  
```  
  
 在前面的示例中，表达式 `nArray[2]` 与 `2[nArray]` 相同。 原因是下标表达式的结果*e1***[** *e2* **]**给定：  
  
 **\*((** *e2* **)**  *+*  **(***e1***))**  
  
 该表达式生成的地址不是*e2*发件人地址的字节*e1*。 相反，缩放地址以生成数组中的下一个对象*e2*。 例如:   
  
```  
double aDbl[2];  
```  
  
 地址`aDb[0]`和`aDb[1]`相距 8 字节-类型的对象的大小**double**。 根据对象类型缩放由 c + + 语言自动完成，并在中定义[相加运算符](../cpp/additive-operators-plus-and.md)其中讨论了加法和减法运算的操作数的指针类型。  
  
 下标表达式还可以有多个下标，如下所示：  
  
 *expression1* **[***expression2***] [***expression3***]**...  
  
 下标表达式从左至右关联。 首先计算最左侧的下标表达式 expression1[expression2]。 通过添加 expression1 和 expression2 得到的地址构成一个指针表达式；然后 expression3 将添加到此指针表达式，从而构成一个新的指针表达式，依此类推，直到添加最后一个下标表达式。 间接寻址运算符 (**\***) 在完成后应用的最后一个下标的表达式将计算，除非最终指针值地址数组类型。  
  
 具有多个下标的表达式引用多维数组的元素。 多维数组是其元素为数组的数组。 例如，三维数组的第一个元素是一个具有两个维度的数组。 以下示例声明并初始化字符的简单二维数组：  
  
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
  
## <a name="positive-and-negative-subscripts"></a>正下标和负下标  
 数组的第一个元素是元素 0。 C + + 数组的范围是从*数组*[0] 到*数组*[*大小*-1]。 但是，C++ 支持正负下标。 负下标必须在数组边界内；否则结果不可预知。 以下代码显示了正数组和负数组下标：  
  
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
  
 上一行中的负下标可能产生运行时错误，因为它在内存中指向比数组的原点低 256 个字节的地址。 指针 `midArray` 会初始化为 `intArray` 的中点；因此可以对其使用正数组和负数组索引。 数组下标错误不会产生编译时错误，但它们会产生不可预知的结果。  
  
 下标运算符是可交换的。 因此，表达式*数组*[*索引*] 和*数组*[*数组*] 保证都是等效只要下标未重载运算符 (请参阅[重载运算符](../cpp/operator-overloading.md))。 第一种形式是最常见的编码做法，但它们都有效。  
  
## <a name="see-also"></a>另请参阅  
 [后缀表达式](../cpp/postfix-expressions.md)   
 [C + + 内置运算符、 优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [数组](../cpp/arrays-cpp.md)   
 [一维数组](../c-language/one-dimensional-arrays.md)   
 [多维数组](../c-language/multidimensional-arrays-c.md)