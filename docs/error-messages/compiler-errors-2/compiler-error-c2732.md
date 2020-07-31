---
title: 编译器错误 C2732
ms.date: 11/04/2016
f1_keywords:
- C2732
helpviewer_keywords:
- C2732
ms.assetid: 01b7ad2c-93cf-456f-a4c0-c5f2fdc7c07c
ms.openlocfilehash: 78be424040c7315271d0880c6678584f698b5be8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218177"
---
# <a name="compiler-error-c2732"></a>编译器错误 C2732

链接规范与“function”的早期规范冲突

该函数已经使用其他链接说明符声明。

具有不同链接说明符的包含文件可能会导致此错误。

若要修复此错误，请更改 **`extern`** 语句，使链接一致。 特别是，不要对 `extern "C"` 块中的 `#include` 指令换行。

## <a name="example"></a>示例

下面的示例生成 C2732：

```cpp
// C2732.cpp
extern void func( void );   // implicit C++ linkage
extern "C" void func( void );   // C2732
```
