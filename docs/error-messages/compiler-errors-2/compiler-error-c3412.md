---
title: 编译器错误 C3412
ms.date: 11/04/2016
f1_keywords:
- C3412
helpviewer_keywords:
- C3412
ms.assetid: aa4dd43b-54ce-4cda-85c1-1a77dd6e34fa
ms.openlocfilehash: ad241b656464746333760cfcbc134c91e49bf44e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761411"
---
# <a name="compiler-error-c3412"></a>编译器错误 C3412

"template"：无法在当前范围内专用化模板

模板不能在类范围内专用化，只能在全局或命名空间范围内使用。

## <a name="example"></a>示例

下面的示例生成 C3412。

```cpp
// C3412.cpp
template <class T>
struct S {
   template <>
   struct S<int> {};   // C3412 in a class
};
```

## <a name="example"></a>示例

下面的示例演示了可能的解决方法。

```cpp
// C3412b.cpp
// compile with: /c
template <class T>
struct S {};

template <>
struct S<int> {};
```
