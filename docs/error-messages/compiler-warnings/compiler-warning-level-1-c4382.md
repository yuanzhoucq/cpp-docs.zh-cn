---
title: 编译器警告（等级 1）C4382
ms.date: 11/04/2016
f1_keywords:
- C4382
helpviewer_keywords:
- C4382
ms.assetid: 34be9ad3-bae6-411a-8f80-0c8fd0d2c092
ms.openlocfilehash: cca2f8cc13cc8317bac3736e142ef58e126ed994
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50629211"
---
# <a name="compiler-warning-level-1-c4382"></a>编译器警告（等级 1）C4382

> 引发 '*类型*： 带有 __clrcall 析构函数或复制构造函数的类型仅可捕获在 /clr: pure 模块

## <a name="remarks"></a>备注

**/Clr: pure**编译器选项在 Visual Studio 2015 中弃用并在 Visual Studio 2017 中不受支持。

编译时使用 **/clr** (不 **/clr: pure**)，异常处理需要的本机类型的成员函数[__cdecl](../../cpp/cdecl.md) ，而不[__clrcall](../../cpp/clrcall.md). 与使用的成员函数的本机类型`__clrcall`调用约定不能使用编译的模块中捕获 **/clr**。

如果将编译的模块中捕获的异常 **/clr: pure**，可以忽略此警告。

有关详细信息，请参阅 [/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。

## <a name="example"></a>示例

下面的示例生成 C4382。

```cpp
// C4382.cpp
// compile with: /clr /W1 /c
struct S {
   __clrcall ~S() {}
};

struct T {
   ~T() {}
};

int main() {
   S s;
   throw s;   // C4382

   S * ps = &s;
   throw ps;   // OK

   T t;
   throw t;   // OK
}
```