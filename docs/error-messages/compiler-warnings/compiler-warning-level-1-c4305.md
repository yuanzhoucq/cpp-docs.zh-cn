---
title: 编译器警告（等级 1）C4305
ms.date: 01/17/2018
f1_keywords:
- C4305
helpviewer_keywords:
- C4305
ms.openlocfilehash: 567442bc48487e4f7d1f905f871d15f913646e87
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233283"
---
# <a name="compiler-warning-level-1-c4305"></a>编译器警告（等级 1）C4305

> "*context*"：从 "*type1*" 到 "*type2*" 的截断

## <a name="remarks"></a>备注

如果将值转换为较小类型的初始化或构造函数参数，则会发出此警告，导致信息丢失。

## <a name="example"></a>示例

此示例显示了你可能会看到此警告的两种方式：

```cpp
// C4305.cpp
// Compile by using: cl /EHsc /W4 C4305.cpp

struct item
{
    item(float) {}
};

int main()
{
    float f = 2.71828;          // C4305 'initializing'
    item i(3.14159);            // C4305 'argument'
    return static_cast<int>(f);
}
```

若要解决此问题，请使用正确类型的值进行初始化，或使用显式强制转换为正确的类型。 例如，使用文本（例如 **`float`** 2.71828 f）而不是 **`double`** （浮点文本的默认类型）来初始化 **`float`** 变量，或传递给采用参数的构造函数 **`float`** 。
