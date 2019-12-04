---
title: 编译器错误 C2930
ms.date: 11/04/2016
f1_keywords:
- C2930
helpviewer_keywords:
- C2930
ms.assetid: f07eecd1-e5d1-4518-bd89-b1fd2a003a17
ms.openlocfilehash: b30e614236298cf9a07cbc29e028039903f9748f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760975"
---
# <a name="compiler-error-c2930"></a>编译器错误 C2930

“class”：type-class-id 被重新定义为 “enum identifier” 的枚举器

不能将泛型或模板类用作枚举的成员。

如果大括号匹配不正确，则可能导致此错误。

以下示例生成 C2930：

```cpp
// C2930.cpp
// compile with: /c
template<class T>
class x{};
enum SomeEnum { x };   // C2930

class y{};
enum SomeEnum { y };
```

使用泛型时，也可能发生 C2930：

```cpp
// C2930c.cpp
// compile with: /clr /c
generic<class T>
ref struct GC {};
enum SomeEnum { GC };   // C2930

ref struct GC2 {};
enum SomeEnum2 { GC2 };
```
