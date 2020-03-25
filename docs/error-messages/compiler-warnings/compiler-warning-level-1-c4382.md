---
title: 编译器警告（等级 1）C4382
ms.date: 11/04/2016
f1_keywords:
- C4382
helpviewer_keywords:
- C4382
ms.assetid: 34be9ad3-bae6-411a-8f80-0c8fd0d2c092
ms.openlocfilehash: 7b8dbf77defab2a711ad931057c740193908474b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186967"
---
# <a name="compiler-warning-level-1-c4382"></a>编译器警告（等级 1）C4382

> 引发 "*type*"：包含 __clrcall 析构函数或复制构造函数的类型只能在/clr： pure 模块中捕获

## <a name="remarks"></a>备注

**/Clr： pure**编译器选项在 visual studio 2015 中已弃用，在 visual studio 2017 中不受支持。

使用 **/clr** （非 **/clr： pure**）进行编译时，异常处理要求本机类型中的成员函数[__cdecl](../../cpp/cdecl.md) ，而不是[__clrcall](../../cpp/clrcall.md)。 具有使用 `__clrcall` 调用约定的成员函数的本机类型无法在使用 **/clr**编译的模块中捕获。

如果将在使用 **/clr： pure**编译的模块中捕获该异常，则可以忽略此警告。

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
