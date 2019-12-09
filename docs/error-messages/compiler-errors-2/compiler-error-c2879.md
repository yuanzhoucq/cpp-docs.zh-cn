---
title: 编译器错误 C2879
ms.date: 11/04/2016
f1_keywords:
- C2879
helpviewer_keywords:
- C2879
ms.assetid: ac92b645-2394-49de-8632-43d44e0553ed
ms.openlocfilehash: 6c7238faf94a2493894534ae5684634b65bb4342
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74736290"
---
# <a name="compiler-error-c2879"></a>编译器错误 C2879

"symbol"：只有现有命名空间才能由命名空间别名定义赋予备用名称

不能创建命名空间以外的符号的[命名空间别名](../../cpp/namespaces-cpp.md#namespace_aliases)。

下面的示例生成 C2879：

```cpp
// C2879.cpp
int main() {
   int i;
   namespace A = i;   // C2879 i is not a namespace
}
```
