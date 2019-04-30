---
title: 编译器错误 C3354
ms.date: 11/04/2016
f1_keywords:
- C3354
helpviewer_keywords:
- C3354
ms.assetid: 185de401-231e-4999-a149-172ee4c69d84
ms.openlocfilehash: 1ff2967f602722c99b58b679324bd4f50575f109
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402601"
---
# <a name="compiler-error-c3354"></a>编译器错误 C3354

“%$I”：该函数用于创建不能有返回类型“type”的委托

以下类型作为 `delegate`的返回类型无效：

- 指向函数的指针

- 指向成员的指针

- 指向成员函数的指针

- 对函数的引用

- 对成员函数的引用

以下示例生成 C3354：

```
// C3354_2.cpp
// compile with: /clr /c
using namespace System;
typedef void ( *VoidPfn )();

delegate VoidPfn func(); // C3354
// try the following line instead
// delegate  void func();
```
