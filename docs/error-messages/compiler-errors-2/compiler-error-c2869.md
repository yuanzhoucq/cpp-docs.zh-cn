---
title: 编译器错误 C2869
ms.date: 11/04/2016
f1_keywords:
- C2869
helpviewer_keywords:
- C2869
ms.assetid: 6e30c001-47f3-4101-b9f1-cc542c9fffae
ms.openlocfilehash: c543a0a4afc0d24205e5afd57cf6ca0732f3edf4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755039"
---
# <a name="compiler-error-c2869"></a>编译器错误 C2869

"name"：已被定义为命名空间

不能重复使用已用作命名空间的名称。

下面的示例生成 C2869：

```cpp
// C2869.cpp
// compile with: /c
namespace A { int i; };

class A {};   // C2869, A is already used
```
