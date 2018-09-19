---
title: 编译器错误 C2477 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2477
dev_langs:
- C++
helpviewer_keywords:
- C2477
ms.assetid: 60bc324b-6605-4833-8099-a291efc712e7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4a3e8a9f76526ecc170b30436ff395d54f8d5395
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46020157"
---
# <a name="compiler-error-c2477"></a>编译器错误 C2477

member： 不能通过派生类中初始化静态数据成员

一种模板类的静态数据成员未正确初始化。 这是为了符合 ISO c + + 标准的版本早于 Visual Studio.NET 2003年的 Visual c + + 编译器进行了重大更改。

下面的示例生成 C2477:

```
// C2477.cpp
// compile with: /Za /c
template <class T>
struct S {
   static int n;
};

struct X {};
struct A: S<X> {};

int A::n = 0;   // C2477

template<>
int S<X>::n = 0;
```