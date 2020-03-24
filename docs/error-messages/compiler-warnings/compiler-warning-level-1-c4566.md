---
title: 编译器警告（等级 1）C4566
ms.date: 11/04/2016
f1_keywords:
- C4566
helpviewer_keywords:
- C4566
ms.assetid: 65f40730-e86f-447c-b37b-16caadcfe311
ms.openlocfilehash: 87d610980ffe9d9e5087ddaec0ecb91d813a4d60
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162253"
---
# <a name="compiler-warning-level-1-c4566"></a>编译器警告（等级 1）C4566

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
