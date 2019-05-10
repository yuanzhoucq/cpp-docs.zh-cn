---
title: 编译器错误 C3699
ms.date: 11/04/2016
f1_keywords:
- C3699
helpviewer_keywords:
- C3699
ms.assetid: 47c29afc-ab8b-4238-adfe-788dd6e00b3b
ms.openlocfilehash: 93058d34ca9a17ab175a55a7bc7b953d369e65c5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324761"
---
# <a name="compiler-error-c3699"></a>编译器错误 C3699

operator： 不能在类型 type 上使用此中间环节

尝试使用不允许的间接寻址`type`。

## <a name="example"></a>示例

下面的示例生成 C3699。

```
// C3699.cpp
// compile with: /clr /c
using namespace System;
int main() {
   String * s;   // C3699
   // try the following line instead
   // String ^ s2;
}
```

## <a name="example"></a>示例

Trivial 属性不能具有引用类型。 有关更多信息，请参见 [property](../../extensions/property-cpp-component-extensions.md) 。 下面的示例生成 C3699。

```
// C3699_b.cpp
// compile with: /clr /c
ref struct C {
   property System::String % x;   // C3699
   property System::String ^ y;   // OK
};
```

## <a name="example"></a>示例

"指向指针的指针"语法的等效项是跟踪引用的句柄。 下面的示例生成 C3699。

```
// C3699_c.cpp
// compile with: /clr /c
using namespace System;
void Test(String ^^ i);   // C3699
void Test2(String ^% i);
```