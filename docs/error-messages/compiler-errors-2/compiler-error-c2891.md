---
title: 编译器错误 C2891
ms.date: 11/04/2016
f1_keywords:
- C2891
helpviewer_keywords:
- C2891
ms.assetid: e12cfb2d-df45-4b0d-b155-c51d17e812fa
ms.openlocfilehash: d9a1cdafdf7d3a2843aee4a20f71c7e6a4693150
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366363"
---
# <a name="compiler-error-c2891"></a>编译器错误 C2891

parameter： 不能采用一个模板参数的地址

不能采用一个模板参数的地址，除非它是左值。 类型参数不是左值，因为它们没有任何地址。 非类型化值都不是左值的模板参数列表中还没有一个地址。 这是代码的因为作为模板参数传递的值是代码的编译器生成的复制的模板自变量导致编译器错误 C2891 示例。

```
template <int i> int* f() { return &i; }
```

都是左值，例如，引用类型的模板参数可以具有其采用地址。

```
template <int& r> int* f() { return &r; }
```

若要更正此错误，不会模板参数的地址除非它是左值。