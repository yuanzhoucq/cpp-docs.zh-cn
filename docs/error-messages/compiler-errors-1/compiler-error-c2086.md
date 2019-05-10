---
title: 编译器错误 C2086
ms.date: 11/04/2016
f1_keywords:
- C2086
helpviewer_keywords:
- C2086
ms.assetid: 4329bf72-90c8-444c-8524-4ef75e6b2139
ms.openlocfilehash: 094a794627b886abc7db5ba4d74c6fe97ff82461
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62216121"
---
# <a name="compiler-error-c2086"></a>编译器错误 C2086

identifier： 重定义

后续的声明与前一个或一次以上，定义标识符。

C2086 也可以是引用的 C# 程序集的增量生成的结果。 重新生成要解决此错误的 C# 程序集。

下面的示例生成 C2086:

```
// C2086.cpp
main() {
  int a;
  int a;   // C2086 not an error in ANSI C
}
```