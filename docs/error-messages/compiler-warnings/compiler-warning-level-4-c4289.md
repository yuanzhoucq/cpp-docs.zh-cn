---
title: 编译器警告（等级 4）C4289
ms.date: 11/04/2016
f1_keywords:
- C4289
helpviewer_keywords:
- C4289
ms.assetid: 0dbd2863-4cde-4e16-894b-104a2d5fa724
ms.openlocfilehash: 3a997af466ddfdaaf4631afeb53d917ce0338c3b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488801"
---
# <a name="compiler-warning-level-4-c4289"></a>编译器警告（等级 4）C4289

使用了非标准扩展 :“var”: 在 for 循环中声明的循环控制变量用在了 for 循环范围外

使用编译时[/Ze](../../build/reference/za-ze-disable-language-extensions.md)和 **/zc: forscope-** 中, 声明的变量[有关](../../cpp/for-statement-cpp.md)之后使用循环**为**-循环作用域。

请参阅[/zc: forscope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)有关如何指定中的标准行为的信息**有关**循环也 **/Ze**。

默认情况下，此警告处于关闭状态。 请参阅 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 了解详细信息。

下面的示例生成 C4289:

```
// C4289.cpp
// compile with: /W4 /Zc:forScope-
#pragma warning(default:4289)
int main() {
   for (int i = 0 ; ; )   // C4289
      break;
   i++;
}
```