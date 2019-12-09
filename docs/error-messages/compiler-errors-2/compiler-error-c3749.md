---
title: 编译器错误 C3749
ms.date: 11/04/2016
f1_keywords:
- C3749
helpviewer_keywords:
- C3749
ms.assetid: 3d26b468-4757-41b8-b5a2-78022a5295fb
ms.openlocfilehash: 75138bf8b090b7770d5bee918790efc095d76627
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761837"
---
# <a name="compiler-error-c3749"></a>编译器错误 C3749

"attribute"：自定义特性不能在函数内部使用

自定义特性不能在函数内部使用。 有关自定义特性的详细信息，请参阅主题[特性](../../windows/attributes/attribute.md)。

## <a name="example"></a>示例

下面的示例生成 C3749：

```cpp
// C3749a.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::All)]
public ref struct ABC : public Attribute {
   ABC() {}
};

void f1() { [ABC]; };  // C3749
```
