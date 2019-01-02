---
title: alignof 和 alignas (C++)
ms.date: 11/04/2016
ms.assetid: 1d18aa8a-9621-4fb5-86e5-4cc86d5187f4
ms.openlocfilehash: 825df25494497e13d29212f7f951be8247b6f136
ms.sourcegitcommit: 185b8ee6dd4e10045df730c5b957b9729813da2d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2018
ms.locfileid: "53411918"
---
# <a name="alignof-and-alignas-c"></a>alignof 和 alignas (C++)

**Alignas**类型说明符是可移植的 c + + 标准方法来指定自定义的变量和用户定义类型的对齐方式。 **Alignof**运算符也是一种标准可移植方法来获取指定的类型或变量的对齐方式。

## <a name="example"></a>示例

可以使用**alignas**类、 结构或联合，或单个成员上。 当多个**alignas**遇到说明符时，编译器将选择最严格的一个 （即具有最大值）。

```cpp
// alignas_alignof.cpp
// compile with: cl /EHsc alignas_alignof.cpp
#include <iostream>

struct alignas(16) Bar
{
    int i;       // 4 bytes
    int n;      // 4 bytes
    alignas(4) char arr[3];
    short s;          // 2 bytes
};

int main()
{
    std::cout << alignof(Bar) << std::endl; // output: 16
}
```

## <a name="see-also"></a>请参阅

[对齐方式](../cpp/alignment-cpp-declarations.md)
