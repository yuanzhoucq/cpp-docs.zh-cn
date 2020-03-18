---
title: 已弃用杂注
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.deprecated
helpviewer_keywords:
- deprecated pragma
- pragmas, deprecated
ms.assetid: 9c046f12-7875-499a-8d5d-12f8642fed2d
ms.openlocfilehash: 5694c5175ff23952c601884243b428a842278b7d
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446477"
---
# <a name="deprecated-pragma"></a>已弃用杂注

**弃用**的杂注使你可以指示函数、类型或任何其他标识符在未来版本中可能不再受支持，也不应再使用。

> [!NOTE]
> 有关 c + + 14 `[[deprecated]]` 特性的信息，以及有关何时使用该特性而不是 Microsoft `__declspec(deprecated)` 修饰符或不**推荐**使用的杂注的指导，请参阅[中C++的特性](../cpp/attributes.md)。

## <a name="syntax"></a>语法

> **#pragma 弃用（** *identifier1* [ **，** *identifier2* ...] **）**

## <a name="remarks"></a>备注

当编译器遇到不**推荐使用**的杂注所指定的标识符时，它会发出编译器警告[C4995](../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md)。

可以否决宏名称。 将宏名称包含在引号内，否则宏将展开。

由于**弃用**的杂注适用于所有匹配标识符，并且不考虑签名，因此它不是弃用特定版本重载函数的最佳选项。 引入到作用域中的任何匹配的函数名称都会触发警告。

建议尽可能使用 c + + 14 `[[deprecated]]` 属性，而不是已**弃用**的杂注。 在许多情况下，与不**推荐使用**的杂注相比，Microsoft 特定的[__declspec （不推荐使用）](../cpp/deprecated-cpp.md)声明修饰符也是更好的选择。 `[[deprecated]]` 属性和 `__declspec(deprecated)` 修饰符允许您为特定形式的重载函数指定弃用状态。 仅在对属性或修饰符适用于特定重载函数的引用上显示诊断警告。

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