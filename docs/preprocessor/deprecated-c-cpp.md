---
title: 已弃用 (C/C++)
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.deprecated
- deprecated_CPP
helpviewer_keywords:
- deprecated pragma
- pragmas, deprecated
ms.assetid: 9c046f12-7875-499a-8d5d-12f8642fed2d
ms.openlocfilehash: 262b23e6e4813a5e22bc3f4e7c9a18efb9988a7c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389289"
---
# <a name="deprecated-cc"></a>已弃用 (C/C++)

**弃用**杂注，可以指示，一个函数、 类型或任何其他标识符可能不再支持在以后发布或不再使用。

> [!NOTE]
> 有关 C + + 14`[[deprecated]]`属性，并指导用户何时使用该属性与 Microsoft declspec 或杂注，请参阅[C++标准属性](../cpp/attributes.md)属性。

## <a name="syntax"></a>语法

```
#pragma deprecated( identifier1 [,identifier2, ...] )
```

## <a name="remarks"></a>备注

当编译器遇到指定的标识符**弃用**杂注，它会发出编译器警告[C4995](../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md)。

可以否决宏名称。 将宏名称包含在引号内，否则宏将展开。

因为**弃用**杂注，适用于所有匹配的标识符，而不考虑使用签名，它不是即将弃用的特定版本的重载函数的最佳选项。 引入到范围的任何匹配的函数名称将触发警告。

我们建议你使用 C + + 14`[[deprecated]]`属性，如果可能，而不是**弃用**杂注。 Microsoft 专用[__declspec （deprecated)](../cpp/deprecated-cpp.md)声明修饰符也是更好的选择在许多情况下比**弃用**杂注。 `[[deprecated]]`属性和`__declspec(deprecated)`修饰符，可以指定不推荐使用的重载函数的特殊形式的状态。 诊断警告仅出现在对特定重载函数的引用属性还是适用于修饰符。

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

## <a name="see-also"></a>请参阅

[Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)