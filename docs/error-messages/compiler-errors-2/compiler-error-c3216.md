---
title: 编译器错误 C3216
ms.date: 11/04/2016
f1_keywords:
- C3216
helpviewer_keywords:
- C3216
ms.assetid: bbab1efe-8779-4489-8bb0-b11e45f5cbe5
ms.openlocfilehash: 6b4f51dc0e27381ef64fc6cd1e4e279736a725aa
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751256"
---
# <a name="compiler-error-c3216"></a>编译器错误 C3216

约束必须是泛型参数，而不是“type”

约束格式不正确。

下面的示例生成 C3216：

```cpp
// C3216.cpp
// compile with: /clr
interface struct A {};

generic <class T>
where F : A   // C3216
// Try the following line instead:
// where T : A    // C3216
ref class C {};
```

下面的代码示例演示了可能的解决方法：

```cpp
// C3216b.cpp
// compile with: /clr /c
interface struct A {};

generic <class T>
where T : A
ref class C {};
```
