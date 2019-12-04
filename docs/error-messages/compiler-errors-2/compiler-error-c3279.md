---
title: 编译器错误 C3279
ms.date: 11/04/2016
f1_keywords:
- C3279
helpviewer_keywords:
- C3279
ms.assetid: 639afc20-984c-4a95-be35-8bf9409f02d5
ms.openlocfilehash: 3025dbf7c6bf4701218c2d9a956cae26d7180848
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757600"
---
# <a name="compiler-error-c3279"></a>编译器错误 C3279

不允许对在 cli 命名空间中声明的类模板进行部分专用化、显式专用化和显式实例化

`cli` 命名空间由 Microsoft 定义并包含伪模板。 Microsoft C++编译器不允许对此命名空间中的类模板进行用户定义的部分和显式专用化，以及类模板的显式实例化。

以下示例生成 C3279：

```cpp
// C3279.cpp
// compile with: /clr
namespace cli {
   template <> ref class array<int> {};   // C3279
   template <typename T> ref class array<T, 2> {};   // C3279
}
```
