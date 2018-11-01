---
title: 编译器错误 C2879
ms.date: 11/04/2016
f1_keywords:
- C2879
helpviewer_keywords:
- C2879
ms.assetid: ac92b645-2394-49de-8632-43d44e0553ed
ms.openlocfilehash: 9ac8f5e5edb1a6ed7314c5b5d125fcc9bfbe67de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677950"
---
# <a name="compiler-error-c2879"></a>编译器错误 C2879

symbol： 只有现有命名空间可以由命名空间别名定义提供的替代名称

无法创建[命名空间别名](../../cpp/namespaces-cpp.md#namespace_aliases)以外的其他命名空间符号。

下面的示例生成 C2879:

```
// C2879.cpp
int main() {
   int i;
   namespace A = i;   // C2879 i is not a namespace
}
```