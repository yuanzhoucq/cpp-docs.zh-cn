---
title: 编译器警告 C4950
ms.date: 11/04/2016
f1_keywords:
- C4950
helpviewer_keywords:
- C4950
ms.assetid: 50226a5c-c664-4d09-ac59-e9e874ca244f
ms.openlocfilehash: 784179af68ff55ba70c61255c88688105ecb1738
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494544"
---
# <a name="compiler-warning-c4950"></a>编译器警告 C4950

“type_or_member”：标记为过时

将成员或类型标记为过时与<xref:System.ObsoleteAttribute>属性。

始终发出 C4950 错误。 可以通过使用来关闭此警告[警告](../../preprocessor/warning.md)杂注指令或[/wd](../../build/reference/compiler-option-warning-level.md)编译器选项。

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