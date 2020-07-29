---
title: 赋值运算符
description: C + + 标准语言赋值运算符语法和用法。
ms.date: 07/24/2020
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
helpviewer_keywords:
- operators [C++], assignment
- assignment operators [C++], C++
- '&= operator'
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
ms.openlocfilehash: 91346d06c6fab4f3cd83c5318c88e738daf8d249
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229215"
---
# <a name="assignment-operators"></a>赋值运算符

## <a name="syntax"></a>语法

*表达式**赋值运算符**表达式*

*assignment-operator*: one of<br/>
&emsp;**`=`**&emsp;**`*=`**&emsp;**`/=`**&emsp;**`%=`**&emsp;**`+=`**&emsp;**`-=`**&emsp;**`<<=`**&emsp;**`>>=`**&emsp;**`&=`**&emsp;**`^=`**&emsp;**`|=`**

## <a name="remarks"></a>备注

赋值运算符将值存储在由左操作数指定的对象中。 有两种类型的赋值运算：

- *简单赋值*，其中第二个操作数的值存储在第一个操作数指定的对象中。

- *复合赋值*：在存储结果之前执行算术、移位或位运算。

下表中的所有赋值运算符 **`=`** 都是复合赋值运算符。

### <a name="assignment-operators-table"></a>赋值运算符表

| 操作员 | 含义 |
|--|--|
| **`=`** | 将第二个操作数的值存储在由第一个操作数指定的对象中（简单赋值）。 |
| **`*=`** | 将第一个操作数的值与第二个操作数的值相乘；将结果存储在第一个操作数指定的对象中。 |
| **`/=`** | 将第一个操作数的值与第二个操作数的值相除；将结果存储在第一个操作数指定的对象中。 |
| **`%=`** | 对第二个操作数的值所指定的第一个操作数进行取模；将结果存储在第一个操作数指定的对象中。 |
| **`+=`** | 将第二个操作数的值与第一个操作数的值相加；将结果存储在第一个操作数指定的对象中。 |
| **`-=`** | 将第一个操作数的值减去第二个操作数的值；将结果存储在第一个操作数指定的对象中。 |
| **`<<=`** | 将第一个操作数的值按第二个操作数的值指定的位数左移；将结果存储在第一个操作数指定的对象中。 |
| **`>>=`** | 将第一个操作数的值按第二个操作数的值指定的位数右移；将结果存储在第一个操作数指定的对象中。 |
| **`&=`** | 获取第一个和第二个操作数的按位“与”；将结果存储在第一个操作数指定的对象中。 |
| **`^=`** | 获取第一个和第二个操作数的按位“异或”；将结果存储在第一个操作数指定的对象中。 |
| **`|=`** | 获取第一个和第二个操作数的按位“与或”；将结果存储在第一个操作数指定的对象中。 |

### <a name="operator-keywords"></a>运算符关键字

其中三个复合赋值运算符具有等效关键字。 它们分别是：

| 操作员 | 等效 |
|--|--|
| **`&=`** | **`and_eq`** |
| **`|=`** | **`or_eq`** |
| **`^=`** | **`xor_eq`** |

C + + 将这些运算符关键字指定为复合赋值运算符的替代拼写。 在 C 中，在标头中以宏形式提供备用拼写 \<iso646.h> 。 在 c + + 中，替换拼写是关键字;\<iso646.h>不推荐使用或 c + + 等效项 \<ciso646> 。 在 Microsoft c + + 中， [`/permissive-`](../build/reference/permissive-standards-conformance.md) [`/Za`](../build/reference/za-ze-disable-language-extensions.md) 需要或编译器选项来启用备用拼写。

## <a name="example"></a>示例

```cpp
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

简单赋值运算符（ **`=`** ）会导致第二个操作数的值存储在第一个操作数指定的对象中。 如果两个对象都是算术类型，则在存储值之前将右操作数转换为左侧的类型。

**`const`** 和类型的对象 **`volatile`** 可以分配给只是或不是或的类型的左值 **`volatile`** **`const`** **`volatile`** 。

对类类型的对象（ **`struct`** 、 **`union`** 和类型）的赋值 **`class`** 由名为的函数执行 `operator=` 。 此运算符函数值的默认行为是执行按位复制；但是，可使用重载运算符修改此行为。 有关详细信息，请参阅[运算符重载](../cpp/operator-overloading.md)。 类类型还可以具有*复制赋值*运算符和*移动赋值*运算符。 有关详细信息，请参阅[复制构造函数和复制赋值运算符](copy-constructors-and-copy-assignment-operators-cpp.md)和[移动构造函数和移动赋值运算符](move-constructors-and-move-assignment-operators-cpp.md)。

任何从给定基类明确派生的类的对象均可赋给基类的对象。 反之亦然，因为存在从派生类到基类的隐式转换，而不是从基类到派生类的隐式转换。 例如：

```cpp
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

```cpp
UserType1 A;
UserType2 B = A;
```

上面的代码显示了一个初始值设定项；它调用了采用 `UserType2` 类型的自变量的 `UserType1` 的构造函数。 给定以下代码

```cpp
UserType1 A;
UserType2 B;

B = A;
```

赋值语句

```cpp
B = A;
```

可能具有以下效果之一：

- 为调用函数 `operator=` `UserType2` ，同时提供 `operator=` `UserType1` 参数。

- 如果存在显式转换函数 `UserType1::operator UserType2`，则调用该函数。

- 调用采用 `UserType2::UserType2` 参数并复制结果的构造函数 `UserType1`，前提是存在此类构造函数。

## <a name="compound-assignment"></a>复合赋值

复合赋值运算符在[赋值运算符表](#assignment-operators-table)中显示。 这些运算符的形式为*e1* *op* =  *e2*，其中*e1*是不可修改的 **`const`** 左值， *e2*为：

- 算术类型

- 如果*op*为或，则为指针 **`+`****`-`**

*E1* *op* =  *e2*窗体表现为*e1* **`=`** *e1* *op* *e2*，但*e1*只计算一次。

对枚举类型的复合赋值将生成错误消息。 如果左操作数为指针类型，则右操作数必须是指针类型，或者必须是计算结果为0的常量表达式。 如果左操作数为整数类型，则右操作数不能是指针类型。

## <a name="result-of-assignment-operators"></a>赋值运算符的结果

赋值后，赋值运算符将返回由左操作数指定的对象的值。 获得的类型是左操作数的类型。 赋值表达式的结果始终为左值。 这些运算符具有从右向左的关联性。 左操作数必须为可修改的左值。

在 ANSI C 中，赋值表达式的结果不是左值。 这意味着 `(a += b) += c` C 中不允许使用合法的 c + + 表达式。

## <a name="see-also"></a>另请参阅

[使用二元运算符的表达式](../cpp/expressions-with-binary-operators.md)<br/>
[C + + 内置运算符、优先级和结合性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C 赋值运算符](../c-language/c-assignment-operators.md)
