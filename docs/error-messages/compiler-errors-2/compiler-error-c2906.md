---
title: 编译器错误 C2906
ms.date: 11/04/2016
f1_keywords:
- C2906
helpviewer_keywords:
- C2906
ms.assetid: 30f652f1-6af6-4a2f-a69e-a1a4876cc8c6
ms.openlocfilehash: 621b31cf362c1dcc740390cf9e405b7da3f05da8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62378513"
---
# <a name="compiler-error-c2906"></a>编译器错误 C2906

specialization： 显式专用化需要 template<>

有关模板的显式专用化，必须使用新语法。

下面的示例生成 C2906:

```
// C2906.cpp
// compile with: /c
template<class T> class X{};   // primary template
class X<int> { }   // C2906
template<> class X<int> { };   // new syntax
```