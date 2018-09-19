---
title: 编译器错误 C3354 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3354
dev_langs:
- C++
helpviewer_keywords:
- C3354
ms.assetid: 185de401-231e-4999-a149-172ee4c69d84
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 40f86702be19259bed7899cdbc5106346d6c6594
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058531"
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
