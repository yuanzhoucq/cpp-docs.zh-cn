---
title: 编译器警告（等级 1）C4566
ms.date: 11/04/2016
f1_keywords:
- C4566
helpviewer_keywords:
- C4566
ms.assetid: 65f40730-e86f-447c-b37b-16caadcfe311
ms.openlocfilehash: c864feb2478e9f99ad6e4c0087dcef72b55de601
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460263"
---
# <a name="compiler-warning-level-1-c4566"></a>编译器警告（等级 1）C4566

表示通用字符名称 'char' 字符不能出现在当前代码页 （页）

不是每个 Unicode 字符可表示当前的 ANSI 代码页中。

窄字符串 （单字节字符） 转换为多字节字符，而不是宽字符串 （双字节字符）。

下面的示例生成 C4566:

```
// C4566.cpp
// compile with: /W1
int main() {
   char c1 = '\u03a0';   // C4566
   char c2 = '\u0642';   // C4566

   wchar_t c3 = L'\u03a0';   // OK
   wchar_t c4 = L'\u0642';   // OK
}
```