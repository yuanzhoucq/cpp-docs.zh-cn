---
title: 编译器警告 （等级 1） C4382 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4382
dev_langs:
- C++
helpviewer_keywords:
- C4382
ms.assetid: 34be9ad3-bae6-411a-8f80-0c8fd0d2c092
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 29afe066fb86d0dd99216a63c057046ec76de55b
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704316"
---
# <a name="compiler-warning-level-1-c4382"></a>编译器警告（等级 1）C4382

> 引发*类型*： 具有 __clrcall 析构函数或复制构造函数的类型仅可捕获在 /clr: pure 模块

## <a name="remarks"></a>备注

**/Clr: pure**编译器选项是在 Visual Studio 2015 中已过时，并在 Visual Studio 2017 中不支持。

如果使用编译的 **/clr** (不 **/clr: pure**)，异常处理预计要的本机类型的成员函数[__cdecl](../../cpp/cdecl.md)而不[__clrcall](../../cpp/clrcall.md). 与成员函数使用的本机类型`__clrcall`调用约定不能使用编译的模块中捕获 **/clr**。

如果使用编译的模块中，将捕获到异常 **/clr: pure**，则可以忽略此警告。

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