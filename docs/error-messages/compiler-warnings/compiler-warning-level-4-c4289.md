---
title: 编译器警告（等级 4）C4289
ms.date: 11/04/2016
f1_keywords:
- C4289
helpviewer_keywords:
- C4289
ms.assetid: 0dbd2863-4cde-4e16-894b-104a2d5fa724
ms.openlocfilehash: cc1a22065be6d5f7f49d6c32f6bc9b6479399e29
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541971"
---
# <a name="compiler-warning-level-4-c4289"></a>编译器警告（等级 4）C4289

使用了非标准扩展 :“var”: 在 for 循环中声明的循环控制变量用在了 for 循环范围外

使用[/ze](../../build/reference/za-ze-disable-language-extensions.md)和 **/zc： forScope** **进行编译**时，在 for 循环后使用在[for 循环中](../../cpp/for-statement-cpp.md)声明的变量。

有关如何在**for**循环中用 **/ze**指定标准行为的信息，请参阅[/zc： forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) 。

默认情况下，此警告处于关闭状态。 请参阅 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 了解详细信息。

下面的示例生成 C4289：

```cpp
// C4289.cpp
// compile with: /W4 /Zc:forScope-
#pragma warning(default:4289)
int main() {
   for (int i = 0 ; ; )   // C4289
      break;
   i++;
}
```