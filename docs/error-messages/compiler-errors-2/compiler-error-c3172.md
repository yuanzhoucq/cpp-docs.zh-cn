---
title: 编译器错误 C3172
ms.date: 11/04/2016
f1_keywords:
- C3172
helpviewer_keywords:
- C3172
ms.assetid: 1834e2fd-6036-4c33-aff2-b51bc7c99441
ms.openlocfilehash: 1da2676d660d23e3fb71b56263779b1f1edacbf9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761733"
---
# <a name="compiler-error-c3172"></a>编译器错误 C3172

"module_name"：不能在项目中指定不同的 idl_module 特性

在编译中的两个文件中找到了具有相同名称但不同 `dllname` 或 `version` 参数[idl_module](../../windows/idl-module.md)特性。 每个编译只能指定一个唯一的 `idl_module` 属性。

可以在多个源代码文件中指定相同的 `idl_module` 属性。

例如，如果找到以下 `idl_module` 属性：

```cpp
// C3172.cpp
[module(name="MyMod")];
[ idl_module(name="x", dllname="file.dll", version="1.1") ];
int main() {}
```

然后，

```cpp
// C3172b.cpp
// compile with: C3172.cpp
// C3172 expected
[ idl_module(name="x", dllname="file.dll", version="1.0") ];
```

编译器将生成 C3172 （请注意不同版本的值）。
