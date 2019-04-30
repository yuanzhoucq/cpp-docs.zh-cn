---
title: 编译器警告（等级 1）C4311
ms.date: 11/04/2016
f1_keywords:
- C4311
helpviewer_keywords:
- C4311
ms.assetid: ddc579d0-d051-47bc-915d-71ffb32323c9
ms.openlocfilehash: 5f9b8ce710879913fdad1be5c0f22f8e3f4ed9d7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408324"
---
# <a name="compiler-warning-level-1-c4311"></a>编译器警告（等级 1）C4311

“variable”: 从“type”到“type”的指针截断

此警告检测 64 位指针截断问题。 例如，如果为 64 位体系结构编译代码，则当指针被分配给 `int`（32 位）时，指针（64 位）的值将被截断。 有关详细信息，请参阅[使用指针的规则](/windows/desktop/WinProg64/rules-for-using-pointers)。

有关警告 C4311 的常见原因的其他信息，请参阅[常见编译器错误](/windows/desktop/WinProg64/common-compiler-errors)。

为 64 位目标编译后，下列代码示例会生成 C4311，然后演示如何修复此问题：

```
// C4311.cpp
// compile by using: cl /W1 C4311.cpp
int main() {
   void* p = &p;
   unsigned int i = (unsigned int) p;   // C4311 for 64-bit targets
   unsigned long long j = (unsigned long long) p;   // OK
}
```