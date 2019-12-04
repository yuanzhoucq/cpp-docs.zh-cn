---
title: 编译器错误 C2951
ms.date: 11/04/2016
f1_keywords:
- C2951
helpviewer_keywords:
- C2951
ms.assetid: c6f95aa2-c894-425b-a51c-d40d70c8daa1
ms.openlocfilehash: fdb837f8e9a9b769d470b70b962ce63d144161e1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755975"
---
# <a name="compiler-error-c2951"></a>编译器错误 C2951

类型声明只能在全局、命名空间或类范围内使用

不能将泛型或模板类声明到全局或命名空间范围之外。 如果在包含文件中进行泛型或模板声明，请确保包含文件位于全局范围。

下面的示例生成 C2951：

```cpp
// C2951.cpp
template <class T>
class A {};

int main() {
   template <class T>   // C2951
   class B {};
}
```

使用泛型时也可能发生 C2951：

```cpp
// C2951b.cpp
// compile with: /clr /c

// OK
generic <class T>
ref class GC { };

int main() {
   generic <class T> ref class GC2 {};   // C2951
}
```
