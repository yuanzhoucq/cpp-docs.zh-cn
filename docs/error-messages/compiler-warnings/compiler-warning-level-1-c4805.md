---
title: 编译器警告（等级 1）C4805
ms.date: 11/04/2016
f1_keywords:
- C4805
helpviewer_keywords:
- C4805
ms.assetid: 99c7b7e2-272e-4ab5-8580-17c42e62e2ef
ms.openlocfilehash: c724af59b0654ae0f212eea038c48cb57f991aa3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175059"
---
# <a name="compiler-warning-level-1-c4805"></a>编译器警告（等级 1）C4805

“operation”: 在操作中将类型“type”与类型“type”混合不安全

对于[bool](../../cpp/bool-cpp.md)与[int](../../c-language/integer-types.md)之间的比较运算，将生成此警告。下面的示例生成 C4805：

```cpp
// C4805.cpp
// compile with: /W1
int main() {
   int i = 1;
   bool b = true;

   if (i == b) {   // C4805, comparing bool and int variables
   }
}
```
