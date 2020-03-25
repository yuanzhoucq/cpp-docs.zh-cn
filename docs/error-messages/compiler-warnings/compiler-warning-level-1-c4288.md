---
title: 编译器警告（等级 1）C4288
ms.date: 11/04/2016
f1_keywords:
- C4288
helpviewer_keywords:
- C4288
ms.assetid: 6aaeb139-90cd-457a-9d37-65687042736f
ms.openlocfilehash: e706a448f4264eceedbb4fa8932c0fc30e88d532
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175735"
---
# <a name="compiler-warning-level-1-c4288"></a>编译器警告（等级 1）C4288

使用了非标准扩展： "var"：在 for 循环中声明的循环控制变量用在了 for 循环范围外;它与外部范围内的声明冲突

使用[/ze](../../build/reference/za-ze-disable-language-extensions.md)和 **/zc： forscope**[进行编译](../../cpp/for-statement-cpp.md)时，在 for 循环后使用在**for 循环中**声明的变量。 使用 Microsoft 对语言的C++扩展，此变量将保留在范围内，并且 C4288 会提醒你未使用该变量的第一个声明。

有关如何在**for**循环中为/Ze 指定 Microsoft 扩展的信息，请参阅[/zc： forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) 。

下面的示例生成 C4288：

```cpp
// C4288.cpp
// compile with: /W1 /c /Zc:forScope-
int main() {
   int i = 0;    // not used in this program
   for (int i = 0 ; ; ) ;
   i++;   // C4288 using for-loop declaration of i
}
```
