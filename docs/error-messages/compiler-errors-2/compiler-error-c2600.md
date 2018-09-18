---
title: 编译器错误 C2600 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2600
dev_langs:
- C++
helpviewer_keywords:
- C2600
ms.assetid: cce11943-ea01-4bee-a7b0-b67d24ec6493
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c1846cefa78c8df13e8ca3c1a7fbc142ba2bf6ad
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022079"
---
# <a name="compiler-error-c2600"></a>编译器错误 C2600

function： 不能定义编译器生成的特殊成员函数 （必须在类中首先声明）

在为类定义成员函数（如构造函数或析构函数）之前，必须在类中声明它们。 如果没有在类中声明，则编译器会生成默认的构造函数和析构函数（称为特殊成员函数）。 但是，如果在类中定义这些函数中没有匹配声明的函数，则编译器将检测到冲突。

若要修复此错误，请在类声明中，声明你在类声明以外定义的每个成员函数。

以下示例生成 C2600：

```
// C2600.cpp
// compile with: /c
class C {};
C::~C() {}   // C2600

class D {
   D::~D();
};

D::~D() {}
```