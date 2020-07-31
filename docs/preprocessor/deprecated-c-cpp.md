---
title: 已弃用杂注
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.deprecated
helpviewer_keywords:
- deprecated pragma
- pragmas, deprecated
ms.assetid: 9c046f12-7875-499a-8d5d-12f8642fed2d
ms.openlocfilehash: 52d9deb4ad68dacc99fab9d12bc9eb21bc0d360e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231606"
---
# <a name="deprecated-pragma"></a>已弃用杂注

使用 **`deprecated`** 杂注，可以指示在未来版本中可能不再支持某个函数、类型或任何其他标识符，也不应再使用它。

> [!NOTE]
> 有关 c + + 14 属性的信息 `[[deprecated]]` ，以及有关何时使用该属性而不是 Microsoft `__declspec(deprecated)` 修饰符或 **`deprecated`** 杂注的指导，请参阅[c + + 中的特性](../cpp/attributes.md)。

## <a name="syntax"></a>语法

> **#pragma 弃用（** *identifier1* [ **，** *identifier2* ...] **）**

## <a name="remarks"></a>备注

当编译器遇到杂注指定的标识符时 **`deprecated`** ，它会发出编译器警告[C4995](../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md)。

可以否决宏名称。 将宏名称包含在引号内，否则宏将展开。

因为 **`deprecated`** 杂注适用于所有匹配标识符，并且不考虑签名，所以它不是弃用特定版本重载函数的最佳选项。 引入到作用域中的任何匹配的函数名称都会触发警告。

建议尽可能使用 c + + 14 `[[deprecated]]` 属性，而不是 **`deprecated`** 杂注。 在许多情况下，与杂注不同，Microsoft 特定的[__declspec （不推荐使用）](../cpp/deprecated-cpp.md)声明修饰符也是更好的选择 **`deprecated`** 。 `[[deprecated]]`特性和 `__declspec(deprecated)` 修饰符允许您为特定窗体的重载函数指定弃用状态。 仅在对属性或修饰符适用于特定重载函数的引用上显示诊断警告。

## <a name="example"></a>示例

```cpp
// pragma_directive_deprecated.cpp
// compile with: /W3
#include <stdio.h>
void func1(void) {
}

void func2(void) {
}

int main() {
   func1();
   func2();
   #pragma deprecated(func1, func2)
   func1();   // C4995
   func2();   // C4995
}
```

以下示例说明如何否决类：

```cpp
// pragma_directive_deprecated2.cpp
// compile with: /W3
#pragma deprecated(X)
class X {  // C4995
public:
   void f(){}
};

int main() {
   X x;   // C4995
}
```

## <a name="see-also"></a>另请参阅

[Pragma 指令和 __pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
