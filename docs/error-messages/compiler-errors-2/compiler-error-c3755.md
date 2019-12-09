---
title: 编译器错误 C3755
ms.date: 11/04/2016
f1_keywords:
- C3755
helpviewer_keywords:
- C3755
ms.assetid: 9317b55e-a52e-4b87-b915-5a208d6eda38
ms.openlocfilehash: 0150693ae84b45dc62c11cfdc59369eb25a819cd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757275"
---
# <a name="compiler-error-c3755"></a>编译器错误 C3755

"delegate"：不能定义委托

[委托（C++组件扩展）](../../extensions/delegate-cpp-component-extensions.md)可以声明，但不能定义。

## <a name="example"></a>示例

下面的示例生成 C3755。

```cpp
// C3755.cpp
// compile with: /clr /c
delegate void MyDel() {};   // C3755
```

## <a name="example"></a>示例

如果尝试创建委托模板，也可能会发生 C3755。 下面的示例生成 C3755。

```cpp
// C3755_b.cpp
// compile with: /clr /c
ref struct R {
   template<class T>
   delegate void D(int) {}   // C3755
};
```
