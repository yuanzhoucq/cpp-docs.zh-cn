---
title: 编译器警告（等级1） C4162
ms.date: 11/04/2016
f1_keywords:
- C4162
helpviewer_keywords:
- C4162
ms.assetid: 21ae3c92-501d-4689-ad7d-13753cb65eff
ms.openlocfilehash: 68e3a752f2aa039f4a2aba24d6433dc9fe2372f6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200052"
---
# <a name="compiler-warning-level-1-c4162"></a>编译器警告（等级1） C4162

"identifier"：未找到带 C 链接的函数

已声明带 C 链接的函数，但找不到该函数。

若要解决此警告，请在 .c 文件中编译（调用 C 编译器）。  如果必须调用C++编译器，请在函数声明之前放置 Extern "C"。

下面的示例生成 C4162

```cpp
// C4162.cpp
// compile with: /c /W1
unsigned char _bittest(long* a, long b);
#pragma intrinsic (_bittest)   // C4162

int main() {
   bool bit;
   long num = 78002;
   bit = _bittest(&num, 5);
}
```

可能的解决方法：

```cpp
// C4162b.cpp
// compile with: /c
extern "C"
unsigned char _bittest(long* a, long b);
#pragma intrinsic (_bittest)

int main() {
   bool bit;
   long num = 78002;
   bit = _bittest(&num, 5);
}
```
