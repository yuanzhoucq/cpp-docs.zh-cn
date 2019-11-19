---
title: 编译器警告（等级1和等级4） C4949
ms.date: 11/04/2016
f1_keywords:
- C4949
helpviewer_keywords:
- C4949
ms.assetid: 34f45a05-c115-49cb-9f67-0bd4f0735d9b
ms.openlocfilehash: f2876813131271ebb2561f8ea7435bb96dc2ce17
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627416"
---
# <a name="compiler-warning-level-1-and-level-4-c4949"></a>编译器警告（等级1和等级4） C4949

仅当用 "/clr [： option]" 编译时，pragma "managed" 和 "非托管" 才有意义

如果源代码未用[/clr](../../build/reference/clr-common-language-runtime-compilation.md)编译，编译器将忽略[托管](../../preprocessor/managed-unmanaged.md)和非托管杂注。 此警告为信息性。

下面的示例生成 C4949：

```cpp
// C4949.cpp
// compile with: /LD /W1
#pragma managed   // C4949
```

如果在没有 **/clr**的情况下使用 **#pragma 非托管**，则 C4949 为级别4警告。

下面的示例生成 C4949：

```cpp
// C4949b.cpp
// compile with: /LD /W4
#pragma unmanaged   // C4949
```