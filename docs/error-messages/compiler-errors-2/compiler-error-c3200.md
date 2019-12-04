---
title: 编译器错误 C3200
ms.date: 11/04/2016
f1_keywords:
- C3200
helpviewer_keywords:
- C3200
ms.assetid: 44bb5e77-f0ec-421c-a732-b9ee7c0a3529
ms.openlocfilehash: 7f6b514231bcda18404e891e0acbe457c8f95146
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738773"
---
# <a name="compiler-error-c3200"></a>编译器错误 C3200

"template"：模板参数 "parameter" 的模板参数无效，应为类模板

向类模板传递的参数无效。 类模板需要模板作为参数。 在下面的示例中，调用 `Y<int, int> aY` 将生成 C3200。 第一个参数必须是一个模板，如 `Y<X, int> aY`。

```cpp
// C3200.cpp
template<typename T>
class X
{
};

template<template<typename U> class T1, typename T2>
class Y
{
};

int main()
{
   Y<int, int> y;   // C3200
}
```
