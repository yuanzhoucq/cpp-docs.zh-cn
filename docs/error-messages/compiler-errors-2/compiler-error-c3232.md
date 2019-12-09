---
title: 编译器错误 C3232
ms.date: 11/04/2016
f1_keywords:
- C3232
helpviewer_keywords:
- C3232
ms.assetid: 3119b3a9-0eff-4a3f-b805-e4d160af9e39
ms.openlocfilehash: e0668cb66bf8e9fa6431b6f238167d594cd00416
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750307"
---
# <a name="compiler-error-c3232"></a>编译器错误 C3232

“param”：泛型类型参数不能用于限定名中

未正确使用泛型类型参数。

以下示例生成 C3232：

```cpp
// C3232.cpp
// compile with: /clr
generic <class T>
ref class C {
   typename T::TYPE t;   // C3232
};
```
