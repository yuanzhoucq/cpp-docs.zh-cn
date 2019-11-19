---
title: 编译器警告（等级1） C4566
ms.date: 11/04/2016
f1_keywords:
- C4566
helpviewer_keywords:
- C4566
ms.assetid: 65f40730-e86f-447c-b37b-16caadcfe311
ms.openlocfilehash: c6a62b399aa32ec6caf2e5a9ee6d4c5836601ba4
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965963"
---
# <a name="compiler-warning-level-1-c4566"></a>编译器警告（等级1） C4566

由通用字符名称 "char" 表示的字符不能在当前代码页中表示（页）

并非每个 Unicode 字符都可以在当前 ANSI 代码页中表示。

将窄字符串（单字节字符）转换为多字节字符，而不是宽字符串（双字节字符）。

下面的示例生成 C4566：

```cpp
// C4566.cpp
// compile with: /W1
int main() {
   char c1 = '\u03a0';   // C4566
   char c2 = '\u0642';   // C4566

   wchar_t c3 = L'\u03a0';   // OK
   wchar_t c4 = L'\u0642';   // OK
}
```