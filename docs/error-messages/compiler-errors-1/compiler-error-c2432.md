---
title: 编译器错误 C2432
ms.date: 11/04/2016
f1_keywords:
- C2432
helpviewer_keywords:
- C2432
ms.assetid: 0e3326e8-cab1-45a5-b48d-61edd33793e8
ms.openlocfilehash: e2983d966a6290ce19713c63feb502c8ffc74bf1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631227"
---
# <a name="compiler-error-c2432"></a>编译器错误 C2432

identifier 中的 16 位数据的非法引用

16 位寄存器用作索引或基寄存器。 编译器不支持引用 16 位数据。 16 位寄存器编译为 32 位代码时不能用作索引或基寄存器。

下面的示例生成 C2432:

```
// C2432.cpp
// processor: x86
int main() {
   _asm mov eax, DWORD PTR [bx]   // C2432
}
```