---
title: 编译器警告（等级 1）C4288
ms.date: 11/04/2016
f1_keywords:
- C4288
helpviewer_keywords:
- C4288
ms.assetid: 6aaeb139-90cd-457a-9d37-65687042736f
ms.openlocfilehash: a732614ac5d71168ece8ada8e468afa5ba54c1f9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220075"
---
# <a name="compiler-warning-level-1-c4288"></a>编译器警告（等级 1）C4288

> 使用了非标准扩展： "var"：在 for 循环中声明的循环控制变量用在了 for 循环范围外;它与外部范围内的声明冲突

使用 [`/Ze`](../../build/reference/za-ze-disable-language-extensions.md) 和 **/zc： forscope-** 进行编译时，在 **`for`** 循环范围后使用在循环中声明[for](../../cpp/for-statement-cpp.md)的变量。 使用 c + + 语言的 Microsoft 扩展可以使此变量保持在范围内，C4288 会提醒你不会使用变量的第一个声明。

有关 [`/Zc:forScope`](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) 如何在/ze 中指定 Microsoft 扩展的信息，请参阅。 **`for`**

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
