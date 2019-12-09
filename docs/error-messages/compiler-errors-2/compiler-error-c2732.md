---
title: 编译器错误 C2732
ms.date: 11/04/2016
f1_keywords:
- C2732
helpviewer_keywords:
- C2732
ms.assetid: 01b7ad2c-93cf-456f-a4c0-c5f2fdc7c07c
ms.openlocfilehash: 61bac8c1b5c9e029cc5833f458669b490fed8c91
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755793"
---
# <a name="compiler-error-c2732"></a>编译器错误 C2732

链接规范与“function”的早期规范冲突

该函数已经使用其他链接说明符声明。

具有不同链接说明符的包含文件可能会导致此错误。

要修复此错误，请更改 `extern` 语句，以便这些链接一致。 特别是，不要对 `extern "C"` 块中的 `#include` 指令换行。

## <a name="example"></a>示例

下面的示例生成 C2732：

```cpp
// C2732.cpp
extern void func( void );   // implicit C++ linkage
extern "C" void func( void );   // C2732
```
