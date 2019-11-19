---
title: 编译器警告 C4972
ms.date: 11/04/2016
f1_keywords:
- C4972
helpviewer_keywords:
- C4972
ms.assetid: d18e8e65-b2ef-4d75-a207-fbd0c17c9060
ms.openlocfilehash: 785d845c3dce556c4d3182ddec07a42a666154f0
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626328"
---
# <a name="compiler-warning-c4972"></a>编译器警告 C4972

直接修改取消装箱操作的结果或将其视为左值是不可验证的

取消引用值类型的句柄（也称为取消装箱），然后为其赋值，是不可验证的。

有关更多信息，请参见 [装箱](../../extensions/boxing-cpp-component-extensions.md)中定义的接口的私有 C++ 特定实现。

## <a name="example"></a>示例

下面的示例生成 C4972。

```cpp
// C4972.cpp
// compile with: /clr:safe
using namespace System;
ref struct R {
   int ^ p;   // a value type
};

int main() {
   R ^ r = gcnew R;
   *(r->p) = 10;   // C4972

   // OK
   r->p = 10;
   Console::WriteLine( r->p );
   Console::WriteLine( *(r->p) );
}
```