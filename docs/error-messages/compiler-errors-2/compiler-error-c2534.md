---
title: 编译器错误 C2534
ms.date: 11/04/2016
f1_keywords:
- C2534
helpviewer_keywords:
- C2534
ms.assetid: 481f9f54-5b51-4aa0-8eea-218f10807705
ms.openlocfilehash: 202e3bbe2238b4cc2a5233ac4e093717d623f099
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87207896"
---
# <a name="compiler-error-c2534"></a>编译器错误 C2534

"identifier"：构造函数无法返回值

构造函数不能返回值，也不能具有返回类型（甚至是 **`void`** 返回类型）。

通过 **`return`** 从构造函数定义中删除语句，可以解决此错误。

下面的示例生成 C2534：

```cpp
// C2534.cpp
class A {
public:
   int i;
   A() { return i; }   // C2534
};
```
