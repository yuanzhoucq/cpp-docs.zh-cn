---
title: 编译器警告 （等级 1） C4162 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4162
dev_langs:
- C++
helpviewer_keywords:
- C4162
ms.assetid: 21ae3c92-501d-4689-ad7d-13753cb65eff
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a36fa6a63443bf2272df7ce6125fd77afedf100f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46027175"
---
# <a name="compiler-warning-level-1-c4162"></a>编译器警告 （等级 1） C4162

identifier： 没有找到带 C 链接函数

具有 C 链接的函数声明，但找不到。

若要解决此警告，编译.c 文件中 （调用 C 编译器）。  如果必须调用 c + + 编译器，请将 extern"C"的函数声明之前。

下面的示例生成 C4162

```
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

```
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