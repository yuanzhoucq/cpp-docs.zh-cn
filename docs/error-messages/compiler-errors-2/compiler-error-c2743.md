---
title: 编译器错误 C2743
ms.date: 11/04/2016
f1_keywords:
- C2743
helpviewer_keywords:
- C2743
ms.assetid: 644cd444-21d2-471d-a176-f5f52c5a0b73
ms.openlocfilehash: d679ce0df0d43772a6c32aa8e00869ac1a4a082b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759641"
---
# <a name="compiler-error-c2743"></a>编译器错误 C2743

"type"：无法使用 __clrcall 析构函数或复制构造函数捕捉本机类型

使用 **/clr**编译的模块尝试捕获本机类型的异常，其中类型的析构函数或复制构造函数使用 `__clrcall` 调用约定。

使用 **/clr**进行编译时，异常处理要求本机类型中的成员函数[__cdecl](../../cpp/cdecl.md)而不是[__clrcall](../../cpp/clrcall.md)。 具有使用 `__clrcall` 调用约定的成员函数的本机类型无法在使用 **/clr**编译的模块中捕获。

有关详细信息，请参阅 [/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。

## <a name="example"></a>示例

下面的示例生成 C2743。

```cpp
// C2743.cpp
// compile with: /clr
public struct S {
   __clrcall ~S() {}
};

public struct T {
   ~T() {}
};

int main() {
   try {}
   catch(S) {}   // C2743
   // try the following line instead
   // catch(T) {}

   try {}
   catch(S*) {}   // OK
}
```
