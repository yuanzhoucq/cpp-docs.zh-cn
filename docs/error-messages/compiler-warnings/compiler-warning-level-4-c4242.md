---
title: 编译器警告（等级 4）C4242
ms.date: 11/04/2016
f1_keywords:
- C4242
helpviewer_keywords:
- C4242
ms.assetid: 8df742e1-fbf1-42f3-8e93-c0e1c222dc7e
ms.openlocfilehash: 3123a414dc7a169d2a472dad96d659a9e56c9020
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541749"
---
# <a name="compiler-warning-level-4-c4242"></a>编译器警告（等级 4）C4242

"identifier"：从 "type1" 转换到 "type2"，可能丢失数据

类型不同。 类型转换可能会导致数据丢失。 编译器进行类型转换。

默认情况下，此警告处于关闭状态。 请参阅 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 了解详细信息。

有关 C4242 的其他信息，请参阅[常见编译器错误](/windows/win32/WinProg64/common-compiler-errors)。

下面的示例生成 C4242：

```cpp
// C4242.cpp
// compile with: /W4
#pragma warning(4:4242)
int func() {
   return 0;
}

int main() {
   char a;
   a = func();   // C4242, return type and variable type do not match
}
```