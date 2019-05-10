---
title: 编译器错误 C3519
ms.date: 11/04/2016
f1_keywords:
- C3519
helpviewer_keywords:
- C3519
ms.assetid: ca24b2bc-7e90-4448-ae84-3fedddf9bca7
ms.openlocfilehash: e9a998e1c3a6c2fb770fb9d26d97b8a24e5554d3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360029"
---
# <a name="compiler-error-c3519"></a>编译器错误 C3519

'invalid_param' : invalid parameter to embedded_idl attribute

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