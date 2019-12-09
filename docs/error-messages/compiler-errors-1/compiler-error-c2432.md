---
title: 编译器错误 C2432
ms.date: 11/04/2016
f1_keywords:
- C2432
helpviewer_keywords:
- C2432
ms.assetid: 0e3326e8-cab1-45a5-b48d-61edd33793e8
ms.openlocfilehash: d4234626bc246d6da87be68b03d44562dd5990ff
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744506"
---
# <a name="compiler-error-c2432"></a>编译器错误 C2432

"identifier" 中对16位数据的非法引用

16位寄存器用作索引或基寄存器。 编译器不支持引用16位数据。 编译32位代码时，16位寄存器不能用作索引或基寄存器。

下面的示例生成 C2432：

```cpp
// C2432.cpp
// processor: x86
int main() {
   _asm mov eax, DWORD PTR [bx]   // C2432
}
```
