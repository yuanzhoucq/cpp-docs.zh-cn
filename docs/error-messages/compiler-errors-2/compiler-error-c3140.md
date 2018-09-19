---
title: 编译器错误 C3140 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3140
dev_langs:
- C++
helpviewer_keywords:
- C3140
ms.assetid: 122f8943-fac3-4db8-a3a8-2c5d19233de6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a40cec364af10f4b61c19b9a28646279a8efca43
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46111729"
---
# <a name="compiler-error-c3140"></a>编译器错误 C3140

不能在同一编译单元中具有多个 module 特性

[模块](../../windows/module-cpp.md)属性只能定义一次每个项目。

下面的示例生成 C3140:

```
// C3140.cpp
// compile with: /c
[emitidl];
[module(name = "MyLibrary")];
[module(name = "MyLibrary2")];   // C3140
```