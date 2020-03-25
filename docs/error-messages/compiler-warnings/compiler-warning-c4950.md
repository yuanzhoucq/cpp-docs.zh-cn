---
title: 编译器警告 C4950
ms.date: 11/04/2016
f1_keywords:
- C4950
helpviewer_keywords:
- C4950
ms.assetid: 50226a5c-c664-4d09-ac59-e9e874ca244f
ms.openlocfilehash: 52c4de94dfe087b4dcf407295e556c9350b2cb8b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164984"
---
# <a name="compiler-warning-c4950"></a>编译器警告 C4950

“type_or_member”：标记为过时

使用 <xref:System.ObsoleteAttribute> 特性将成员或类型标记为过时。

始终发出 C4950 错误。 您可以通过使用[warning](../../preprocessor/warning.md) pragma 指令或[/wd](../../build/reference/compiler-option-warning-level.md)编译器选项来关闭此警告。

## <a name="example"></a>示例

下面的示例生成 C4950：

```cpp
// C4950.cpp
// compile with: /clr
using namespace System;

// Any reference to Func3 should generate an error with message
[System::ObsoleteAttribute("Will be removed in next version", true)]
Int32 Func3(Int32 a, Int32 b) {
   return (a + b);
}

int main() {
   Int32 MyInt3 = ::Func3(2, 2);   // C4950
}
```
