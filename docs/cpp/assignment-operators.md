---
title: 赋值运算符 |Microsoft 文档
ms.custom: ''
ms.date: 03/05/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- =
- '*='
- /=
- '%='
- +=
- -=
- <<=
- '>>='
- '&='
- ^=
- '|='
- '&&='
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], assignment
- assignment operators [C++], C++
- '&= operator'
- '&&= operator'
- ^= operator
- += operator
- '>>= operator'
- '|= operator'
- operator>>=
- '*= operator'
- '%= operator'
- ^= operator
- operator >>=
- = operator
- -= operator
- /= operator
- <<= operator
ms.assetid: b028cf35-2ff1-4f14-9027-fd53ebec8aa0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4318d7913b180c3fbadcf9d655e402c9b0ad7ccc
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="assignment-operators"></a>赋值运算符
## <a name="syntax"></a>语法  
  
```  
expression assignment-operator expression   
assignment-operator : one of  
   =   *=   /=   %=   +=   -=   <<=   >>=   &=   ^=   |=  &&=
```  
  
## <a name="remarks"></a>备注  
 赋值运算符将值存储在左操作数指定的对象中。 有三种类型的赋值操作： 

1. 简单赋值，在其中第二个操作数的值存储在第一个操作数指定的对象中。 1. 复合赋值，算术、 移位或位运算执行再存储结果。
1. 中的资源传输而不复制移动 （对于类类型） 的分配。


下表中的所有赋值运算符都除外 = 和 & & = 运算符是复合赋值运算符。  
  
### <a name="assignment-operators"></a>赋值运算符  
  
|运算符|含义|  
|--------------|-------------|  
|**=**|将第二个操作数的值存储在由第一个操作数指定的对象中（简单赋值）。|  
|**\*=**|将第一个操作数的值与第二个操作数的值相乘；将结果存储在第一个操作数指定的对象中。|  
|**/=**|将第一个操作数的值与第二个操作数的值相除；将结果存储在第一个操作数指定的对象中。|  
|**%=**|对第二个操作数的值所指定的第一个操作数进行取模；将结果存储在第一个操作数指定的对象中。|  
|**+=**|将第二个操作数的值与第一个操作数的值相加；将结果存储在第一个操作数指定的对象中。|  
|**-=**|将第一个操作数的值减去第二个操作数的值；将结果存储在第一个操作数指定的对象中。|  
|**<\<=**|将第一个操作数的值按第二个操作数的值指定的位数左移；将结果存储在第一个操作数指定的对象中。|  
|**>>=**|将第一个操作数的值按第二个操作数的值指定的位数右移；将结果存储在第一个操作数指定的对象中。|  
|**&=**|获取第一个和第二个操作数的按位“与”；将结果存储在第一个操作数指定的对象中。|  
|**^=**|获取第一个和第二个操作数的按位“异或”；将结果存储在第一个操作数指定的对象中。|  
|**\|=**|获取第一个和第二个操作数的按位“与或”；将结果存储在第一个操作数指定的对象中。|
|**&&=**| （对于类类型） 的移动赋值运算符。 如果第二个操作数为右值，（而不复制它们） 将其资源移到第一个操作数。 请参阅[移动构造函数和移动赋值运算符](move-constructors-and-move-assignment-operators-cpp.md)有关详细信息。|
  
 **运算符关键字**  
  
 三个复合赋值运算符具有文本等效项。 它们是：  
  
|运算符|等效|  
|--------------|----------------|  
|**&=**|`and_eq`|  
|**\|=**|`or_eq`|  
|**^=**|`xor_eq`|  
  
 若要访问这些运算符关键字在程序中的使用两种方式： 包括头文件`iso646.h`，或使用编译[/Za](../build/reference/za-ze-disable-language-extensions.md) （禁用语言扩展） 编译器选项。  
  
## <a name="example"></a>示例  
  
```  
// expre_Assignment_Operators.cpp  
// compile with: /EHsc  
// Demonstrate assignment operators  
#include <iostream>  
using namespace std;  
int main() {  
   int a = 3, b = 6, c = 10, d = 0xAAAA, e = 0x5555;  
  
   a += b;      // a is 9  
   b %= a;      // b is 6  
   c >>= 1;      // c is 5  
   d |= e;      // Bitwise--d is 0xFFFF   
  
   cout  << "a = 3, b = 6, c = 10, d = 0xAAAA, e = 0x5555" << endl  
         << "a += b yields " << a << endl  
         << "b %= a yields " << b << endl  
         << "c >>= 1 yields " << c << endl  
         << "d |= e yields " << hex << d << endl;  
}  
```  
  
## <a name="simple-assignment"></a>简单赋值  
 简单赋值运算符 (=) 将使第二个操作数的值存储在第一个操作数指定的对象中。 如果两个对象都是算术类型，则在存储值之前，正确的操作数将转换为左侧的类型。  
  
 常量和可变类型的对象可赋给可变类型的左值或者既不是常量类型也不是可变类型的左值。  
  
 对类类型（结构、联合和类类型）的对象的赋值由名为 operator= 的函数执行。 此运算符函数值的默认行为是执行按位复制；但是，可使用重载运算符修改此行为。 (请参阅[重载运算符](../cpp/operator-overloading.md)有关详细信息。)  
  
 任何从给定基类明确派生的类的对象均可赋给基类的对象。 反之则不然，因为有一个隐式转换，它能从派生类转换到基类，但不能从基类转换到派生类。 例如：  
  
```  
// expre_SimpleAssignment.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
class ABase  
{  
public:  
    ABase() { cout << "constructing ABase\n"; }  
};  
  
class ADerived : public ABase  
{  
public:  
    ADerived() { cout << "constructing ADerived\n"; }  
};  
  
int main()  
{  
    ABase aBase;  
    ADerived aDerived;  
  
    aBase = aDerived; // OK  
    aDerived = aBase; // C2679  
}  
```  
  
 对引用类型的赋值的行为方式就像对引用所指向的对象进行赋值一样。  
  
 对于类类型对象，赋值与初始化不同。 若要演示不同赋值和初始化的工作方式，请考虑以下代码  
  
```  
UserType1 A;  
UserType2 B = A;  
```  
  
 上面的代码显示了一个初始值设定项；它调用了采用 `UserType2` 类型的参数的 `UserType1` 的构造函数。 给定以下代码  
  
```  
UserType1 A;  
UserType2 B;  
  
B = A;  
```  
  
 赋值语句  
  
```  
B = A;   
```  
  
 可能具有以下效果之一：  
  
-   将为 `UserType2` 调用函数 operator=，前提是 operator= 提供 `UserType1` 参数。  
  
-   如果存在显式转换函数 `UserType1::operator UserType2`，则调用该函数。  
  
-   调用采用 `UserType2::UserType2` 参数并复制结果的构造函数 `UserType1`，前提是存在此类构造函数。  
  
## <a name="compound-assignment"></a>复合赋值  
 复合赋值运算符，在表中所示[赋值运算符](../cpp/assignment-operators.md)，窗体中指定*e1* `op` =  *e2*，其中*e1*是一个可修改的左值不是 const 类型和*e2*是以下之一：  
  
-   算术类型  
  
-   一个指针，如果`op`是 + 或-  
  
 *E1* `op` =  *e2*窗体的行为方式如*e1* *= e1* `op` *e2*，但*e1*只计算一次。  
  
 对枚举类型的复合赋值将生成错误消息。 如果左操作数属于指针类型，则右操作数必须属于指针类型或必须是计算结果为 0 的常量表达式。 如果左操作数属于整数类型，则右操作数不能属于指针类型。  
  
## <a name="result-of-assignment-operators"></a>赋值运算符的结果  
 赋值后，赋值运算符将返回由左操作数指定的对象的值。 获得的类型是左操作数的类型。 赋值表达式的结果始终为左值。 这些运算符具有从右向左的关联性。 左操作数必须为可修改的左值。  
  
 在 ANSI C 中，赋值表达式的结果不是左值。 因此，合法的 C++ 表达式 `(a += b) += c` 在 C 中是非法的。  
  
## <a name="see-also"></a>请参阅  
 [使用二元运算符的表达式](../cpp/expressions-with-binary-operators.md)   
 [C++ 内置运算符、 优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [C 赋值运算符](../c-language/c-assignment-operators.md)