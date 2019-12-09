---
title: 编译器错误 C3883
ms.date: 11/04/2016
f1_keywords:
- C3883
helpviewer_keywords:
- C3883
ms.assetid: cdd1c1f4-f268-4469-9c62-d52303114b0c
ms.openlocfilehash: 9dbb0328aa1810d55f2d974aed822992b53101b5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74736654"
---
# <a name="compiler-error-c3883"></a>编译器错误 C3883

"var"： initonly 静态数据成员必须已初始化

使用[initonly](../../dotnet/initonly-cpp-cli.md)标记的变量未正确初始化。

下面的示例生成 C3883：

```cpp
// C3883.cpp
// compile with: /clr
ref struct Y1 {
   initonly
   static int staticConst1;   // C3883
};
```

以下示例演示了可能的解决方法：

```cpp
// C3883b.cpp
// compile with: /clr /c
ref struct Y1 {
   initonly
   static int staticConst2 = 0;
};
```

下面的示例演示如何在静态构造函数中初始化：

```cpp
// C3883c.cpp
// compile with: /clr /LD
ref struct Y1 {
   initonly
   static int staticConst1;

   static Y1() {
      staticConst1 = 0;
   }
};
```
