---
title: 编译器错误 C3172
ms.date: 11/04/2016
f1_keywords:
- C3172
helpviewer_keywords:
- C3172
ms.assetid: 1834e2fd-6036-4c33-aff2-b51bc7c99441
ms.openlocfilehash: 5c9c1561b63c740b9f7f5d85b2bf3e04de2542c0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62175181"
---
# <a name="compiler-error-c3172"></a>编译器错误 C3172

模块名： 不能在项目中指定不同的 idl_module 特性

[idl_module](../../windows/idl-module.md)属性具有相同名称但不同`dllname`或`version`在两个编译中的文件中找到的参数。 只有一个唯一`idl_module`属性可以指定每次编译。

相同`idl_module`属性可以指定多个源代码文件中。

例如，如果以下`idl_module`找属性：

```
// C3172.cpp
[module(name="MyMod")];
[ idl_module(name="x", dllname="file.dll", version="1.1") ];
int main() {}
```

然后，

```
// C3172b.cpp
// compile with: C3172.cpp
// C3172 expected
[ idl_module(name="x", dllname="file.dll", version="1.0") ];
```

编译器将生成 C3172 （请注意不同的版本值）。