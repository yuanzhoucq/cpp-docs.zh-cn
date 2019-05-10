---
title: '按位与或运算符: |'
ms.date: 06/14/2018
f1_keywords:
- bitor
- '|'
helpviewer_keywords:
- OR operator [C++], bitwise inclusive
- bitwise operators [C++], OR operator
- inclusive OR operator
- '| operator'
ms.assetid: 4c8a6a68-d828-447d-875a-aedb4ce3aa9a
ms.openlocfilehash: 848bf3b2ec61084b59ab5b1ee6807f6066a4675e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62184270"
---
# <a name="bitwise-inclusive-or-operator-"></a>按位与或运算符: |

## <a name="syntax"></a>语法

> *expression1* **|** *expression2*

## <a name="remarks"></a>备注

按位非独占 OR 运算符 (**&#124;**) 将第二个操作数的相应位进行第一个操作数的每一位进行比较。 如果其中一个位是 1，则将对应的结果位设置为 1。 否则，将对应的结果位设置为 0。

按位“与或”运算符的两个操作数必须为整型。 中涵盖的常用算术转换[标准转换](standard-conversions.md)适用于操作数。

## <a name="operator-keyword-for-124"></a>运算符关键字&#124;

**Bitor**运算符是的文本等效 **&#124;**。 有两种方法来访问**bitor**您的程序中的运算符： 包含头文件\<iso646.h >，或使用编译[/Za](../build/reference/za-ze-disable-language-extensions.md) （禁用语言扩展） 编译器选项。

## <a name="example"></a>示例

```cpp
// expre_Bitwise_Inclusive_OR_Operator.cpp
// compile with: /EHsc
// Demonstrate bitwise inclusive OR
#include <iostream>
using namespace std;

int main() {
   unsigned short a = 0x5555;      // pattern 0101 ...
   unsigned short b = 0xAAAA;      // pattern 1010 ...

   cout  << hex << ( a | b ) << endl;   // prints "ffff" pattern 1111 ...
}
```

## <a name="see-also"></a>请参阅

[C++ 内置运算符、优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C 按位运算符](../c-language/c-bitwise-operators.md)