---
title: 编译器错误 C3519
ms.date: 11/04/2016
f1_keywords:
- C3519
helpviewer_keywords:
- C3519
ms.assetid: ca24b2bc-7e90-4448-ae84-3fedddf9bca7
ms.openlocfilehash: e9a998e1c3a6c2fb770fb9d26d97b8a24e5554d3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432757"
---
# <a name="compiler-error-c3519"></a>编译器错误 C3519

invalid_param: embedded_idl 特性的参数无效

一个参数传递给`embedded_idl`的属性[#import](../../preprocessor/hash-import-directive-cpp.md)，但编译器无法识别的参数。

有关允许的唯一参数`embedded_idl`都`emitidl`和`no_emitidl`。

下面的示例生成 C3519:

```
// C3519.cpp
// compile with: /LD
[module(name="MyLib2")];
#import "C:\testdir\bin\importlib.tlb" embedded_idl("no_emitidcl")
// C3519
#import "C:\testdir\bin\importlib.tlb" embedded_idl("no_emitidl")
// OK
```