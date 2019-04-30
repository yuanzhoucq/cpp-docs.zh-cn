---
title: 编译器错误 C2379
ms.date: 11/04/2016
f1_keywords:
- C2379
helpviewer_keywords:
- C2379
ms.assetid: 37dc3015-a4af-4341-bbf3-da6150df7e51
ms.openlocfilehash: 1b3256efb6c0ff8236ba80a9ac681780f34fa8dd
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345651"
---
# <a name="compiler-error-c2379"></a>编译器错误 C2379

正式参数编号具有不同的类型提升时

指定参数的类型不兼容，通过默认提升，与以前的声明中的类型。 这是 ANSI C 中的错误 ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) 和具有 Microsoft 扩展的警告 (**/Ze**)。

下面的示例生成 C2379:

```
// C2379.c
// compile with: /Za
void func();
void func(char);   // C2379, char promotes to int
```