---
title: 编译器错误 C2430
ms.date: 11/04/2016
f1_keywords:
- C2430
helpviewer_keywords:
- C2430
ms.assetid: 07c20f76-63e1-4d22-b2a9-98b0d45c5cac
ms.openlocfilehash: f82eb4914ec36aa513822964f551a05fbb77aa97
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744571"
---
# <a name="compiler-error-c2430"></a>编译器错误 C2430

"identifier" 中有多个索引寄存器

缩放多个寄存器。 编译器支持扩展索引，但只能缩放一个寄存器。

## <a name="example"></a>示例

下面的示例生成 C2430。

```cpp
// C2430.cpp
// processor: x86
int main() {
   _asm mov eax, [ebx*2+ecx*4] // C2430
}
```
