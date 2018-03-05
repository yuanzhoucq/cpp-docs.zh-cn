---
title: "运算符重载 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- operator_cpp
- operator
dev_langs:
- C++
helpviewer_keywords:
- redefinable operators [C++]
- non-redefinable operators [C++]
- operator keyword [C++]
- operators [C++], overloading
- operator overloading
ms.assetid: 56ad4c4f-dd0c-45e0-adaa-08fe98cb1f8e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 617236d30f3c4473f6c7785db97789105d6cd565
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="operator-overloading"></a>运算符重载
当应用于类的实例时，`operator` 关键字将声明一个用于指定 `operator-symbol` 含义的函数。 这将为运算符提供多个含义，或者将“重载”它。 编译器通过检查其操作数类型来区分运算符不同的含义。  
  
## <a name="syntax"></a>语法  
  
```  
  
type operator operator-symbol ( parameter-list )  
```  
  
## <a name="remarks"></a>备注  
 你可以在全局或为各个类重新定义大多数内置运算符的函数。 重载运算符作为函数来实现。  
  
 重载运算符的名称是`operator x`，其中`x`是运算符下, 表中所示。 例如，若要重载加法运算符，则可以对称为 `operator+` 的函数进行定义。 同样，若要重载加法/赋值运算符 `+=`，则可以对称为 `operator+=` 的函数进行定义。  
  
### <a name="redefinable-operators"></a>可重定义的运算符  
  
|运算符|名称|类型|  
|--------------|----------|----------|  
|`,`|逗号|二进制|  
|`!`|逻辑“非”|一元|  
|`!=`|不相等|二进制|  
|`%`|取模|二进制|  
|`%=`|取模赋值|二进制|  
|`&`|按位“与”|二进制|  
|`&`|address-of|一元|  
|`&&`|逻辑“与”|二进制|  
|`&=`|按位“与”赋值|二进制|  
|`( )`|函数调用 |—|  
|`( )`|强制转换运算符|一元|  
|`*`|乘法|二进制|  
|`*`|指针取消引用|一元|  
|`*=`|乘法赋值|二进制|  
|`+`|添加|二进制|  
|`+`|一元加|一元|  
|`++`|递增<sup>1</sup>|一元|  
|`+=`|加法赋值|二进制|  
|`-`|减法|二进制|  
|`-`|一元求反|一元|  
|`--`|递减<sup>1</sup>|一元|  
|`-=`|减法赋值|二进制|  
|`->`|成员选择|二进制|  
|`->*`|指向成员的指针选定内容|二进制|  
|`/`|除法|二进制|  
|`/=`|除法赋值|二进制|  
|`<`|小于|二进制|  
|`<<`|左移|二进制|  
|`<<=`|左移赋值|二进制|  
|`<=`|小于或等于|二进制|  
|`=`|赋值|二进制|  
|`==`|相等|二进制|  
|`>`|大于|二进制|  
|`>=`|大于或等于|二进制|  
|`>>`|右移|二进制|  
|`>>=`|右移赋值|二进制|  
|`[ ]`|数组下标|—|  
|`^`|异或|二进制|  
|`^=`|异或赋值|二进制|  
|`&#124;`|按位“与或”|二进制|  
|`&#124;=`|按位“与或”赋值|二进制|  
|`&#124;&#124;`|逻辑“或”|二进制|  
|`~`|二进制反码|一元|  
|`delete`|`Delete`|—|  
|`new`|`New`|—|  
|`conversion operators`|转换运算符|一元|  
  
 1 两个版本的一元递增和递减运算符存在： 前置递增和后置递增。  
  
 请参阅[运算符重载的一般规则](../cpp/general-rules-for-operator-overloading.md)有关详细信息。 以下主题对各种类别的重载运算符的约束进行了介绍：  
  
-   [一元运算符](../cpp/overloading-unary-operators.md)  
  
-   [二元运算符](../cpp/binary-operators.md)  
  
-   [赋值](../cpp/assignment.md)  
  
-   [函数调用](../cpp/function-call-cpp.md)  
  
-   [下标](../cpp/subscripting.md)  
  
-   [类成员访问](../cpp/member-access.md)  
  
-   [递增和递减](../cpp/increment-and-decrement-operator-overloading-cpp.md)。  
  
-   [用户定义类型转换](../cpp/user-defined-type-conversions-cpp.md)  
  
 无法重载下表中显示的运算符。 该表包括预处理器符号 `#` 和 `##`。  
  
### <a name="nonredefinable-operators"></a>不可重定义的运算符  
  
|||  
|-|-|  
|`Operator`|`Name`|  
|`.`|成员选择|  
|`.*`|指向成员的指针选定内容|  
|`::`|范围解析|  
|`? :`|条件运算|  
|`#`|预处理器转换为字符串|  
|`##`|预处理器串联|  
  
 尽管通常是在代码中遇到重载运算符时由编译器对其进行隐式调用，但也可以按照与调用任何成员或非成员函数相同的方式来显式调用重载运算符：  
  
```  
Point pt;  
pt.operator+( 3 );  // Call addition operator to add 3 to pt.  
```  
  
## <a name="example"></a>示例  
 以下示例重载 `+` 运算符以添加两个复数并返回结果。  
  
```  
// operator_overloading.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
struct Complex {  
   Complex( double r, double i ) : re(r), im(i) {}  
   Complex operator+( Complex &other );  
   void Display( ) {   cout << re << ", " << im << endl; }  
private:  
   double re, im;  
};  
  
// Operator overloaded using a member function  
Complex Complex::operator+( Complex &other ) {  
   return Complex( re + other.re, im + other.im );  
}  
  
int main() {  
   Complex a = Complex( 1.2, 3.4 );  
   Complex b = Complex( 5.6, 7.8 );  
   Complex c = Complex( 0.0, 0.0 );  
  
   c = a + b;  
   c.Display();  
}  
```  
  
## <a name="output"></a>输出  
  
```  
6.8, 11.2  
```  
  
## <a name="in-this-section"></a>本节内容  
  
1.  [运算符重载的一般规则](../cpp/general-rules-for-operator-overloading.md)  
  
2.  [重载一元运算符](../cpp/overloading-unary-operators.md)  
  
3.  [二元运算符](../cpp/binary-operators.md)  
  
4.  [赋值](../cpp/assignment.md)  
  
5.  [函数调用](../cpp/function-call-cpp.md)  
  
6.  [下标](../cpp/subscripting.md)  
  
7.  [成员访问](../cpp/member-access.md)  
  
## <a name="see-also"></a>请参阅  
 [C + + 内置运算符、 优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [关键字](../cpp/keywords-cpp.md)