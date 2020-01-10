---
title: 编译器错误 C2231
ms.date: 11/04/2016
f1_keywords:
- C2231
helpviewer_keywords:
- C2231
ms.assetid: 677c5c66-d30f-4c3b-bbb9-760858d56477
ms.openlocfilehash: 50230b3a9b609d281cddf996783287c270f844d5
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301816"
---
# <a name="compiler-error-c2231"></a>编译器错误 C2231

"."：左操作数指向 "class-key"，使用 "->"

成员选择操作（.）左侧的操作数是指针，而不是类、结构或联合。

下面的示例生成 C2231:

```c
// C2231.c
struct S {
   int member;
} s, *ps = &s;
int main() {
   ps.member = 0;   // C2231

   // OK
   ps->member = 0;   // crash
   s.member = 0;
}
```
