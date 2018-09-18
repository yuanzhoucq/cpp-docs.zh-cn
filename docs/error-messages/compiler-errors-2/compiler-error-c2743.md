---
title: 编译器错误 C2743 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2743
dev_langs:
- C++
helpviewer_keywords:
- C2743
ms.assetid: 644cd444-21d2-471d-a176-f5f52c5a0b73
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4217a1e7a8475362c654ac34b6a345846341ec35
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056479"
---
# <a name="compiler-error-c2743"></a>编译器错误 C2743

type： 无法捕获具有 __clrcall 析构函数或复制构造函数的本机类型

使用编译的模块 **/clr**尝试捕获异常的本机类型和其中的类型的析构函数或复制构造函数使用`__clrcall`调用约定。

编译时使用 **/clr**，异常处理需要的本机类型的成员函数[__cdecl](../../cpp/cdecl.md)而不[__clrcall](../../cpp/clrcall.md)。 与使用的成员函数的本机类型`__clrcall`调用约定不能使用编译的模块中捕获 **/clr**。

有关详细信息，请参阅 [/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。

## <a name="example"></a>示例

下面的示例生成 C2743。

```
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