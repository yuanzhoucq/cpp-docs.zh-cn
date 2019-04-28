---
title: 编译器错误 C2732
ms.date: 11/04/2016
f1_keywords:
- C2732
helpviewer_keywords:
- C2732
ms.assetid: 01b7ad2c-93cf-456f-a4c0-c5f2fdc7c07c
ms.openlocfilehash: 820a620b7e4414123c56433f84536393834f6fd6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208397"
---
# <a name="compiler-error-c2732"></a>编译器错误 C2732

链接规范与“function”的早期规范冲突

该函数已经使用其他链接说明符声明。

具有不同链接说明符的包含文件可能会导致此错误。

要修复此错误，请更改 `extern` 语句，以便这些链接一致。 特别是，不要对 `extern "C"` 块中的 `#include` 指令换行。

## <a name="example"></a>示例

下面的示例生成 C2732：

```
// C2732.cpp
extern void func( void );   // implicit C++ linkage
extern "C" void func( void );   // C2732
```