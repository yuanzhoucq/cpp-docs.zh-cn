---
title: 编译器错误 C3699
ms.date: 11/04/2016
f1_keywords:
- C3699
helpviewer_keywords:
- C3699
ms.assetid: 47c29afc-ab8b-4238-adfe-788dd6e00b3b
ms.openlocfilehash: ec902266550e591623894823e6336bd2436bfbd5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758029"
---
# <a name="compiler-error-c3699"></a>编译器错误 C3699

"operator"：不能在类型 "type" 上使用此间接寻址

尝试使用 `type`上不允许的间接寻址。

## <a name="example"></a>示例

下面的示例生成 C3699。

```cpp
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

普通属性不能具有引用类型。 有关更多信息，请参见 [property](../../extensions/property-cpp-component-extensions.md) 。 下面的示例生成 C3699。

```cpp
// C3699_b.cpp
// compile with: /clr /c
ref struct C {
   property System::String % x;   // C3699
   property System::String ^ y;   // OK
};
```

## <a name="example"></a>示例

"指向指针的指针" 语法的等效项是跟踪引用的句柄。 下面的示例生成 C3699。

```cpp
// C3699_c.cpp
// compile with: /clr /c
using namespace System;
void Test(String ^^ i);   // C3699
void Test2(String ^% i);
```
