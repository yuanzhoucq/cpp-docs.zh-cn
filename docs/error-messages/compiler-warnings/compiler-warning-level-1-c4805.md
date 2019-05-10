---
title: 编译器警告（等级 1）C4805
ms.date: 11/04/2016
f1_keywords:
- C4805
helpviewer_keywords:
- C4805
ms.assetid: 99c7b7e2-272e-4ab5-8580-17c42e62e2ef
ms.openlocfilehash: 3bbce2529b208b764fa28bad1d67e1bbb38ec127
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406348"
---
# <a name="compiler-warning-level-1-c4805"></a>编译器警告（等级 1）C4805

“operation”: 在操作中将类型“type”与类型“type”混合不安全

对于 [bool](../../cpp/bool-cpp.md) 与 [int](../../c-language/integer-types.md)之间的比较操作，会生成此警告。下面的示例生成 C4805：

```
// C4805.cpp
// compile with: /W1
int main() {
   int i = 1;
   bool b = true;

   if (i == b) {   // C4805, comparing bool and int variables
   }
}
```