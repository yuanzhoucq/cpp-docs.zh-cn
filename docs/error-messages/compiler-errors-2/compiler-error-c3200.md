---
title: 编译器错误 C3200
ms.date: 11/04/2016
f1_keywords:
- C3200
helpviewer_keywords:
- C3200
ms.assetid: 44bb5e77-f0ec-421c-a732-b9ee7c0a3529
ms.openlocfilehash: 7eb0c00f4f4c5c59766bf305acfef89e12a6cfb1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505061"
---
# <a name="compiler-error-c3200"></a>编译器错误 C3200

模板： 模板参数 parameter 的无效的模板参数应为类模板

传递到类模板的参数无效。 类模板需要一个参数作为模板。 在以下示例中，调用`Y<int, int> aY`将生成 C3200。 第一个参数必须是一个模板，如`Y<X, int> aY`。

```
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