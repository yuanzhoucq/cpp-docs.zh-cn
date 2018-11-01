---
title: 编译器错误 C3749
ms.date: 11/04/2016
f1_keywords:
- C3749
helpviewer_keywords:
- C3749
ms.assetid: 3d26b468-4757-41b8-b5a2-78022a5295fb
ms.openlocfilehash: 7535f82a392f3d54b265ada2bd40a8d433838f4b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596505"
---
# <a name="compiler-error-c3749"></a>编译器错误 C3749

attribute： 不能在函数内使用的自定义属性

不能在函数内使用的自定义属性。 自定义属性的详细信息，请参阅主题[属性](../../windows/attributes/attribute.md)。

## <a name="example"></a>示例

下面的示例生成 C3749:

```
// C3749a.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::All)]
public ref struct ABC : public Attribute {
   ABC() {}
};

void f1() { [ABC]; };  // C3749
```
