---
title: 下标运算符 []
ms.date: 11/04/2016
f1_keywords:
- '[]'
helpviewer_keywords:
- operators [C++], subscript
- postfix operators [C++]
- '[] operator'
- subscript operator [C++], syntax
ms.assetid: 69c31494-52da-4dd0-8bbe-6ccbfd50f197
ms.openlocfilehash: a4eb878a18aa38b7047104903d10d96d66cc6720
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231086"
---
# <a name="subscript-operator-"></a>下标运算符 []

## <a name="syntax"></a>语法

```
postfix-expression [ expression ]
```

## <a name="remarks"></a>备注

后跟下标运算符 **[]** 的后缀表达式（也可以是主表达式）指定数组索引。

有关 c + +/CLI 中的托管数组的信息，请参阅[数组](../extensions/arrays-cpp-component-extensions.md)。

通常，*后缀表达式*表示的值是一个指针值（如数组标识符），而*expression*是一个整数值（包括枚举类型）。 但是，从语法上来说，只需要一个表达式是指针类型，另一个表达式是整型。 因此整数值可以位于*后缀表达式*位置，指针值可以在*表达式*或下标位置的括号中。 考虑以下代码片断：

```cpp
int nArray[5] = { 0, 1, 2, 3, 4 };
cout << nArray[2] << endl;            // prints "2"
cout << 2[nArray] << endl;            // prints "2"
```

在前面的示例中，表达式 `nArray[2]` 与 `2[nArray]` 相同。 原因是下标表达式的结果 `e1[e2]` 是由指定的：

`*((e2) + (e1))`

表达式生成的地址不是来自地址*e1*的*e2*字节。 相反，地址将进行缩放以生成数组*e2*中的下一个对象。 例如：

```cpp
double aDbl[2];
```

和的地址 `aDb[0]` `aDb[1]` 相隔8个字节，即类型的对象的大小 **`double`** 。 这种根据对象类型进行缩放的操作是由 c + + 语言自动完成的，并且在[加法运算符](../cpp/additive-operators-plus-and.md)中定义，其中讨论了指针类型的操作数的加法和减法。

下标表达式还可以有多个下标，如下所示：

*表达式*2 **[** *expression2* 2 **] [** *expression3* **]** .。。

下标表达式从左至右关联。 首先计算最左侧的下标表达式 expression1 [expression2]     。 通过添加 expression1  和 expression2  得到的地址构成一个指针表达式；然后 expression3  将添加到此指针表达式，从而构成一个新的指针表达式，依此类推，直到添加最后一个下标表达式。 在 <strong>\*</strong> 计算最后一个下标表达式之后，将应用间接寻址运算符（），除非最终指针值用于寻址数组类型。

具有多个下标的表达式引用多维数组的元素。 多维数组是其元素为数组的数组。 例如，三维数组的第一个元素是一个具有两个维度的数组。 以下示例声明并初始化字符的简单二维数组：

```cpp
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

数组的第一个元素是元素 0。 C + + 数组的范围是从*array*[0] 到*array*[*size* -1]。 但是，C++ 支持正负下标。 负下标必须在数组边界内；否则结果不可预知。 以下代码显示了正数组和负数组下标：

```cpp
#include <iostream>
using namespace std;

int main() {
    int intArray[1024];
    for (int i = 0, j = 0; i < 1024; i++)
    {
        intArray[i] = j++;
    }

    cout << intArray[512] << endl;   // 512

    cout << 257[intArray] << endl;   // 257

    int *midArray = &intArray[512];  // pointer to the middle of the array

    cout << midArray[-256] << endl;  // 256

    cout << intArray[-256] << endl;  // unpredictable, may crash
}
```

最后一行中的负下标可能产生运行时错误，因为它指向 **`int`** 内存中低于数组的源的地址256位置。 将指针 `midArray` 初始化为的中间， `intArray` 因此可能（但很危险）在其上使用正数组和负数组索引。 数组下标错误不会产生编译时错误，但它们会产生不可预知的结果。

下标运算符是可交换的。 因此，只要没有重载下标运算符（请参阅[重载运算符](../cpp/operator-overloading.md)），表达式*数组*[*index*] 和*index*[*array*] 就是等效的。 第一种形式是最常见的编码做法，但它们都有效。

## <a name="see-also"></a>另请参阅

[后缀表达式](../cpp/postfix-expressions.md)<br/>
[C++ 内置运算符、优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[数组](../cpp/arrays-cpp.md)<br/>
[一维数组](../c-language/one-dimensional-arrays.md)<br/>
[多维数组](../c-language/multidimensional-arrays-c.md)<br/>
