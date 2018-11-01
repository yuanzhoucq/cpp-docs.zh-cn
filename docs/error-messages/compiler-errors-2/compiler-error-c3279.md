---
title: 编译器错误 C3279
ms.date: 11/04/2016
f1_keywords:
- C3279
helpviewer_keywords:
- C3279
ms.assetid: 639afc20-984c-4a95-be35-8bf9409f02d5
ms.openlocfilehash: 5f39510ee9ec0e717d675aa8b396405bc33b4ea1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445001"
---
# <a name="compiler-error-c3279"></a>编译器错误 C3279

不允许对在 cli 命名空间中声明的类模板进行部分专用化、显式专用化和显式实例化

`cli` 命名空间由 Microsoft 定义并包含伪模板。 Visual C++ 编译器不允许对此命名空间中的类模板进行用户定义专用化、部分专用化、显式专用化和显式实例化。

以下示例生成 C3279：

```
// C3279.cpp
// compile with: /clr
namespace cli {
   template <> ref class array<int> {};   // C3279
   template <typename T> ref class array<T, 2> {};   // C3279
}
```