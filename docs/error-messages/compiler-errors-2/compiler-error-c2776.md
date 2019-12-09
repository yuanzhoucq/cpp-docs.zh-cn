---
title: 编译器错误 C2776
ms.date: 11/04/2016
f1_keywords:
- C2776
helpviewer_keywords:
- C2776
ms.assetid: 9d80addc-62c7-40fc-a2cc-60303abb87df
ms.openlocfilehash: 79758c88e595e6d5ebb5cd4b39a8df8fc1339752
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740060"
---
# <a name="compiler-error-c2776"></a>编译器错误 C2776

每个属性只能指定一个 "get" 方法

只能在[属性](../../cpp/property-cpp.md)扩展属性中指定一个 `get` 函数。 当指定多个 `get` 函数时，将发生此错误。

下面的示例生成 C2776：

```cpp
// C2776.cpp
struct A {
   __declspec(property(get=GetProp,get=GetPropToo))
   // try the following line instead
   // __declspec(property(get=GetProp))
      int prop;   // C2776
   int GetProp(void);
   int GetPropToo(void);
};
```
