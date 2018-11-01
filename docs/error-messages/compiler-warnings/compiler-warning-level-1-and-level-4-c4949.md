---
title: 编译器警告（等级 1 和等级 4）C4949
ms.date: 11/04/2016
f1_keywords:
- C4949
helpviewer_keywords:
- C4949
ms.assetid: 34f45a05-c115-49cb-9f67-0bd4f0735d9b
ms.openlocfilehash: 8050edbd7a653776d046bc7b4155fd43094d9a5d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50515920"
---
# <a name="compiler-warning-level-1-and-level-4-c4949"></a>编译器警告（等级 1 和等级 4）C4949

杂注 managed 和 unmanaged 是仅当使用编译时，才有意义 / clr [: 选项]

编译器将忽略[托管](../../preprocessor/managed-unmanaged.md)和非托管杂注，如果不使用编译的源代码[/clr](../../build/reference/clr-common-language-runtime-compilation.md)。 此警告为信息性。

下面的示例生成 C4949:

```
// C4949.cpp
// compile with: /LD /W1
#pragma managed   // C4949
```

当**非托管的 #pragma**使用不带 **/clr**，C4949 是第 4 级警告。

下面的示例生成 C4949:

```
// C4949b.cpp
// compile with: /LD /W4
#pragma unmanaged   // C4949
```