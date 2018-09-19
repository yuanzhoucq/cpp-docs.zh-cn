---
title: 编译器错误 C3172 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3172
dev_langs:
- C++
helpviewer_keywords:
- C3172
ms.assetid: 1834e2fd-6036-4c33-aff2-b51bc7c99441
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 25c3b1fd9132c6b170fdf74b1619a35d83959f90
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117629"
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