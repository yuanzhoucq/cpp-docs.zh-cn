---
title: 编译器警告 （等级 1） C4288 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4288
dev_langs:
- C++
helpviewer_keywords:
- C4288
ms.assetid: 6aaeb139-90cd-457a-9d37-65687042736f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b8b9e82f8cb24c4635fb64c3ac0a1c82e301c086
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056478"
---
# <a name="compiler-warning-level-1-c4288"></a>编译器警告（等级 1）C4288

使用了非标准扩展: var： 在 for 循环中声明的循环控制变量用外部 for 循环范围中;它与外部作用域中的声明冲突

使用编译时[/Ze](../../build/reference/za-ze-disable-language-extensions.md)和 **/zc: forscope-** 中, 声明的变量**有关**之后使用循环[为](../../cpp/for-statement-cpp.md)-循环作用域。 C + + 语言的 Microsoft 扩展允许此变量，以保持在范围内，并且 C4288 提醒您未使用该变量的第一个声明。

请参阅[/zc: forscope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)有关如何指定中的 Microsoft 扩展的信息**为**使用 /Ze 循环。

下面的示例生成 C4288:

```
// C4288.cpp
// compile with: /W1 /c /Zc:forScope-
int main() {
   int i = 0;    // not used in this program
   for (int i = 0 ; ; ) ;
   i++;   // C4288 using for-loop declaration of i
}
```