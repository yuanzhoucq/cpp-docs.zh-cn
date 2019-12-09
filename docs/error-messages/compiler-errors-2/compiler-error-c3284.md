---
title: 编译器错误 C3284
ms.date: 11/04/2016
f1_keywords:
- C3284
helpviewer_keywords:
- C3284
ms.assetid: e582f316-e9db-4d27-9c70-fdfa737a9d5f
ms.openlocfilehash: 9606ff5916e4c6971ec44a9d277bb980701ed169
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757548"
---
# <a name="compiler-error-c3284"></a>编译器错误 C3284

函数“function”的泛型参数“parameter”的约束必须与函数“function”的泛型参数“paramete”的约束匹配

虚拟泛型函数所用的约束必须与基类中具有相同名称和参数集的虚拟函数的约束相同。

以下示例生成 C3284：

```cpp
// C3284.cpp
// compile with: /clr /c
// C3284 expected
public interface class IGettable {
   int Get();
};

public interface class B {
   generic<typename T>
   where T : IGettable
   virtual int mf(T t);
};

public ref class D : public B {
public:
   generic<typename T>
   // Uncomment the following line to resolve.
   // where T : IGettable
   virtual int mf(T t) {
      return 4;
   }
};
```
