---
title: 编译器错误 C3737
ms.date: 11/04/2016
f1_keywords:
- C3737
helpviewer_keywords:
- C3737
ms.assetid: ca2aeb23-2491-4ccb-8838-884abf7065c8
ms.openlocfilehash: 25dbb8897db45cbddaaf7f0530bcb2a8653b03cf
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752790"
---
# <a name="compiler-error-c3737"></a>编译器错误 C3737

"delegate"：委托不能有显式调用约定

不能为 `delegate`指定[调用约定](../../cpp/calling-conventions.md)。

## <a name="example"></a>示例

下面的示例生成 C3737：

```cpp
// C3737a.cpp
// compile with: /clr
delegate void __stdcall MyFunc();   // C3737
// Try the following line instead.
// delegate void MyFunc();

int main() {
}
```
