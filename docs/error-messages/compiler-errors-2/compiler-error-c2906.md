---
title: 编译器错误 C2906
ms.date: 11/04/2016
f1_keywords:
- C2906
helpviewer_keywords:
- C2906
ms.assetid: 30f652f1-6af6-4a2f-a69e-a1a4876cc8c6
ms.openlocfilehash: bf21c4f14948d56fe781226e5aaf1b479059cb55
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748692"
---
# <a name="compiler-error-c2906"></a>编译器错误 C2906

"专用化"：显式专用化需要 "template < >"

必须使用新语法来显式专用化模板。

下面的示例生成 C2906：

```cpp
// C2906.cpp
// compile with: /c
template<class T> class X{};   // primary template
class X<int> { }   // C2906
template<> class X<int> { };   // new syntax
```
