---
title: 编译器错误 C3519
ms.date: 11/04/2016
f1_keywords:
- C3519
helpviewer_keywords:
- C3519
ms.assetid: ca24b2bc-7e90-4448-ae84-3fedddf9bca7
ms.openlocfilehash: 7e56ff814b1a2dd6ec3cb41db2cbcc21d7dcf2d9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750164"
---
# <a name="compiler-error-c3519"></a>编译器错误 C3519

"invalid_param"： embedded_idl 特性的参数无效

参数被传递到[#import](../../preprocessor/hash-import-directive-cpp.md)的 `embedded_idl` 属性，但编译器不能识别参数。

`embedded_idl` 允许的唯一参数 `emitidl` 和 `no_emitidl`。

下面的示例生成 C3519：

```cpp
// C3519.cpp
// compile with: /LD
[module(name="MyLib2")];
#import "C:\testdir\bin\importlib.tlb" embedded_idl("no_emitidcl")
// C3519
#import "C:\testdir\bin\importlib.tlb" embedded_idl("no_emitidl")
// OK
```
