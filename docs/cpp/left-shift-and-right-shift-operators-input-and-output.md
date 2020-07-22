---
title: 左移和右移运算符（ &gt; &gt; 和 &lt; &lt; ）
ms.date: 08/13/2018
f1_keywords:
- <<
- '>>'
helpviewer_keywords:
- << operator [C++], with specific objects
- left shift operators [C++]
- right shift operators [C++]
- bitwise-shift operators [C++]
- '>> operator'
- shift operators [C++]
- operators [C++], shift
ms.assetid: 25fa0cbb-5fdd-4657-8745-b35f7d8f1606
ms.openlocfilehash: 7cde299d305219f2bd0e53a9f19c2ca35a8c7b69
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404765"
---
# <a name="left-shift-and-right-shift-operators-gtgt-and-ltlt"></a>左移和右移运算符（ &gt; &gt; 和 &lt; &lt; ）

按位移位运算符是右移位运算符（ **&gt;&gt;** ），它将*shift 表达式*的位移动到右侧，将左移位运算符（）移动到左边的移位运算符（ **&lt;&lt;** ）。 *shift-expression* <sup>1</sup>

## <a name="syntax"></a>语法

> *移位表达式* `<<`*加法表达式*\
> *shift-expression* `>>` *additive-expression*

## <a name="remarks"></a>备注

> [!IMPORTANT]
> 以下说明和示例在 Windows 上适用于 x86 和 x64 体系结构。 对于 ARM 设备，左移运算符和右移位运算符的实现在很大程度上是不同的。 有关详细信息，请参阅[HELLO ARM](https://devblogs.microsoft.com/cppblog/hello-arm-exploring-undefined-unspecified-and-implementation-defined-behavior-in-c/)博客文章的 "移位运算符" 部分。

## <a name="left-shifts"></a>左移

左移运算符使*shift 表达式*中的位向左移动由*加法表达式*指定的位置数。 因移位运算而空出的位上将用零填充。 左移是逻辑移动（从末端移掉的位将被舍弃，包括符号位）。 有关位移位种类的详细信息，请参阅[按位移位](https://en.wikipedia.org/wiki/Bitwise_shift)。

以下示例将显示使用无符号数字的左移运算。 该示例通过将值表示为 bitset 来显示对位的操作。 有关详细信息，请参阅[位组类](../standard-library/bitset-class.md)。

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    unsigned short short1 = 4;
    bitset<16> bitset1{short1};   // the bitset representation of 4
    cout << bitset1 << endl;  // 0b00000000'00000100

    unsigned short short2 = short1 << 1;     // 4 left-shifted by 1 = 8
    bitset<16> bitset2{short2};
    cout << bitset2 << endl;  // 0b00000000'00001000

    unsigned short short3 = short1 << 2;     // 4 left-shifted by 2 = 16
    bitset<16> bitset3{short3};
    cout << bitset3 << endl;  // 0b00000000'00010000
}
```

如果你左移有符号的数字，以至于符号位受影响，则结果是不确定的。 下面的示例演示了将1位左移到符号位位置时所发生的情况。

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    short short1 = 16384;
    bitset<16> bitset1(short1);
    cout << bitset1 << endl;  // 0b01000000'00000000

    short short3 = short1 << 1;
    bitset<16> bitset3(short3);  // 16384 left-shifted by 1 = -32768
    cout << bitset3 << endl;  // 0b10000000'00000000

    short short4 = short1 << 14;
    bitset<16> bitset4(short4);  // 4 left-shifted by 14 = 0
    cout << bitset4 << endl;  // 0b00000000'00000000
}
```

## <a name="right-shifts"></a>右移

右移运算符使*移位表达式*中的位模式向右移位（由*加法表达式*指定的位置数）。 对于无符号数字，因移位运算而空出的位上将用零填充。 对于有符号数字，符号位用于填充空出的位。 也就是说，如果数字为正，则使用 0；如果数字为负，则使用 1。

> [!IMPORTANT]
> 符号为负的数字右移的结果依实现而定。 尽管 Microsoft c + + 编译器使用符号位来填充空出的位位置，但并不保证其他实现也这样做。

以下示例显示使用无符号数字的右移运算：

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    unsigned short short11 = 1024;
    bitset<16> bitset11{short11};
    cout << bitset11 << endl;     // 0b00000100'00000000

    unsigned short short12 = short11 >> 1;  // 512
    bitset<16> bitset12{short12};
    cout << bitset12 << endl;     // 0b00000010'00000000

    unsigned short short13 = short11 >> 10;  // 1
    bitset<16> bitset13{short13};
    cout << bitset13 << endl;     // 0b00000000'00000001

    unsigned short short14 = short11 >> 11;  // 0
    bitset<16> bitset14{short14};
    cout << bitset14 << endl;     // 0b00000000'00000000
}
```

下一示例显示使用符号为正的数字的右移运算。

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    short short1 = 1024;
    bitset<16> bitset1(short1);
    cout << bitset1 << endl;     // 0b00000100'00000000

    short short2 = short1 >> 1;  // 512
    bitset<16> bitset2(short2);
    cout << bitset2 << endl;     // 0b00000010'00000000

    short short3 = short1 >> 11;  // 0
    bitset<16> bitset3(short3);
    cout << bitset3 << endl;     // 0b00000000'00000000
}
```

下一示例显示使用符号为负的整数的右移运算。

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    short neg1 = -16;
    bitset<16> bn1(neg1);
    cout << bn1 << endl;  // 0b11111111'11110000

    short neg2 = neg1 >> 1; // -8
    bitset<16> bn2(neg2);
    cout << bn2 << endl;  // 0b11111111'11111000

    short neg3 = neg1 >> 2; // -4
    bitset<16> bn3(neg3);
    cout << bn3 << endl;  // 0b11111111'11111100

    short neg4 = neg1 >> 4; // -1
    bitset<16> bn4(neg4);
    cout << bn4 << endl;  // 0b11111111'11111111

    short neg5 = neg1 >> 5; // -1
    bitset<16> bn5(neg5);
    cout << bn5 << endl;  // 0b11111111'11111111
}
```

## <a name="shifts-and-promotions"></a>移位和提升

移位运算符两侧的表达式必须是整数类型。 根据[标准转换](standard-conversions.md)中所述的规则执行整型提升。 结果的类型与提升的*移位表达式*的类型相同。

在下面的示例中， **char**类型的变量被提升为**int**。

```cpp
#include <iostream>
#include <typeinfo>

using namespace std;

int main() {
    char char1 = 'a';

    auto promoted1 = char1 << 1;   // 194
    cout << typeid(promoted1).name() << endl;  // int

    auto promoted2 = char1 << 10;  // 99328
    cout << typeid(promoted2).name() << endl;  // int
}
```

## <a name="additional-details"></a>其他详细信息

如果*加法表达式*为负，或者*加法表达式*大于或等于（提升）*移位表达式*中的位数，则移位运算的结果是不确定的。 如果*加法表达式*为0，则不执行移位运算。

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    unsigned int int1 = 4;
    bitset<32> b1{int1};
    cout << b1 << endl;    // 0b00000000'00000000'00000000'00000100

    unsigned int int2 = int1 << -3;  // C4293: '<<' : shift count negative or too big, undefined behavior
    unsigned int int3 = int1 >> -3;  // C4293: '>>' : shift count negative or too big, undefined behavior
    unsigned int int4 = int1 << 32;  // C4293: '<<' : shift count negative or too big, undefined behavior
    unsigned int int5 = int1 >> 32;  // C4293: '>>' : shift count negative or too big, undefined behavior
    unsigned int int6 = int1 << 0;
    bitset<32> b6{int6};
    cout << b6 << endl;    // 0b00000000'00000000'00000000'00000100 (no change)
}
```

## <a name="footnotes"></a>脚注

<sup>1</sup>以下是 c + + 11 ISO 规范（INCITS/ISO/IEC 14882-2011 [2012]）、5.8.2 和5.8.3 部分中的移位运算符的说明。

`E1 << E2` 的值是 `E1` 向左移动 `E2` 位的结果，空出的位用零填充。 如果 `E1` 有一个无符号类型，则结果的值为**E1 × 2**<sup>**E2**</sup>，减少的模数比结果类型中可表示的最大值多一个。 否则，如果 `E1` 具有有符号的类型和非负值，并且**E1 × 2**<sup>**E2**</sup>可在结果类型的相应无符号类型中表示，则该值转换为结果类型就是生成的值; 否则，该行为是不确定的。

`E1 >> E2` 的值是 `E1` 向右移动 `E2` 位的结果。 如果 `E1` 具有无符号类型或 `E1` 具有有符号类型和非负值，则结果的值为**E1/2**<sup>**E2**</sup>的商的整数部分。 如果 `E1` 属于有符号类型且为负值，则结果值由实现决定。

## <a name="see-also"></a>另请参阅

[带有二元运算符的表达式](../cpp/expressions-with-binary-operators.md)<br/>
[C++ 内置运算符、优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
