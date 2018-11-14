---
title: 赋值运算符
ms.date: 03/05/2018
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
ms.openlocfilehash: 44211e43a0449c8a50ff03cac31eeed1fcc49a28
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2018
ms.locfileid: "51328469"
---
# <a name="assignment-operators"></a>赋值运算符

## <a name="syntax"></a>语法

*表达式**赋值运算符**表达式*

*赋值运算符*： 之一<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>=&nbsp;&nbsp;&nbsp;*=&nbsp;&nbsp;&nbsp;/=&nbsp;&nbsp;&nbsp;%=&nbsp;&nbsp;&nbsp;+=&nbsp;&nbsp;&nbsp;-=&nbsp;&nbsp;&nbsp;\<\<=&nbsp;&nbsp;&nbsp;>>=&nbsp;&nbsp;&nbsp;&=&nbsp;&nbsp;&nbsp;^=&nbsp;&nbsp;&nbsp;\|=</strong>

## <a name="remarks"></a>备注

赋值运算符将值存储在左操作数指定的对象中。 有两种类型的赋值操作：

1. *简单赋值*，在这第二个操作数的值存储在第一个操作数指定的对象。

1. *复合赋值*，算术、 移位或位运算执行再存储结果。

下表中除 = 运算符之外的所有其他赋值运算符都是复合赋值运算符。

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

**运算符关键字**

三个复合赋值运算符具有文本等效项。 它们是：

|运算符|等效|
|--------------|----------------|
|**&=**|`and_eq`|
|**\|=**|`or_eq`|
|**^=**|`xor_eq`|

有两种方法来访问这些应用程序中的运算符关键字： 包括头文件`iso646.h`，或使用编译[/Za](../build/reference/za-ze-disable-language-extensions.md) （禁用语言扩展） 编译器选项。

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

简单赋值运算符 (**=**) 会导致要存储在第一个操作数指定的对象中的第二个操作数的值。 如果两个对象都是算术类型，则在存储值之前，正确的操作数将转换为左侧的类型。

对象**const**并**易失性**类型可以分配到左值的类型仅包含**易失性**，或者是否既不**const**也不**易失性**。

对象的类类型 （结构、 联合和类类型） 的赋值由名为的函数执行`operator=`。 此运算符函数值的默认行为是执行按位复制；但是，可使用重载运算符修改此行为。 请参阅[运算符重载](../cpp/operator-overloading.md)有关详细信息。 此外，类类型可以具有*复制赋值*并*移动赋值*运算符。 有关详细信息，请参阅[复制构造函数和复制赋值运算符](copy-constructors-and-copy-assignment-operators-cpp.md)并[移动构造函数和移动赋值运算符](move-constructors-and-move-assignment-operators-cpp.md)。

任何从给定基类明确派生的类的对象均可赋给基类的对象。 反之则不然，因为有一个隐式转换，它能从派生类转换到基类，但不能从基类转换到派生类。 例如：

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

- 调用函数`operator=`有关`UserType2`提供`operator=`随提供`UserType1`参数。

- 如果存在显式转换函数 `UserType1::operator UserType2`，则调用该函数。

- 调用采用 `UserType2::UserType2` 自变量并复制结果的构造函数 `UserType1`，前提是存在此类构造函数。

## <a name="compound-assignment"></a>复合赋值

复合赋值运算符，在表中所示[赋值运算符](#assignment-operators)，在窗体中指定*e1* *op*= *e2*，其中*e1*是可修改左值不是**const**类型和*e2*是以下之一：

- 算术类型

- 一个指针，如果*op*是**+** 或 **-**

*E1* *op*= *e2*形式表现为*e1* **=** *e1* *op* *e2*，但*e1*只计算一次。

对枚举类型的复合赋值将生成错误消息。 如果左操作数属于指针类型，则右操作数必须属于指针类型或必须是计算结果为 0 的常量表达式。 如果左操作数属于整数类型，则右操作数不能属于指针类型。

## <a name="result-of-assignment-operators"></a>赋值运算符的结果

赋值后，赋值运算符将返回由左操作数指定的对象的值。 获得的类型是左操作数的类型。 赋值表达式的结果始终为左值。 这些运算符具有从右向左的关联性。 左操作数必须为可修改的左值。

在 ANSI C 中，赋值表达式的结果不是左值。 因此，合法的 C++ 表达式 `(a += b) += c` 在 C 中是非法的。

## <a name="see-also"></a>请参阅

[使用二元运算符的表达式](../cpp/expressions-with-binary-operators.md)<br/>
[C++ 内置运算符、优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C 赋值运算符](../c-language/c-assignment-operators.md)
