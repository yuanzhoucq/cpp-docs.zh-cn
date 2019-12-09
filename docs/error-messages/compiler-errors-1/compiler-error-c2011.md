---
title: 编译器错误 C2011
ms.date: 11/04/2016
f1_keywords:
- C2011
helpviewer_keywords:
- C2011
ms.assetid: 992c9d51-e850-4d53-b86b-02e73b38249c
ms.openlocfilehash: dc13829a267deea1f412eb2d8f86057f01dc0e1c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752413"
---
# <a name="compiler-error-c2011"></a>编译器错误 C2011

“identifier”：“type”类型重定义

标识符已定义为 `type`。 检查标识符的重定义。

如果不止一次将头文件或类型库导入同一个文件，则也有可能生成 C2011。 若要防止多个包含在标头文件中定义的类型，请在头文件中使用 include 临界或 `#pragma`[一次](../../preprocessor/once.md)指令。

如果需要查找重定义的类型的初始声明，可以使用[/p](../../build/reference/p-preprocess-to-a-file.md)编译器标志来生成传递到编译器的预处理输出。 你可以使用文本搜索工具在输出文件中查找重定义的标识符的实例。

下面的示例生成了 C2011 并演示了修复此错误的一种方法：

```cpp
// C2011.cpp
// compile with: /c
struct S;
union S;   // C2011
union S2;   // OK
```
