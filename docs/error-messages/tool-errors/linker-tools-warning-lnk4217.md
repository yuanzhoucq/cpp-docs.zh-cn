---
title: 链接器工具警告 LNK4217 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4217
dev_langs:
- C++
helpviewer_keywords:
- LNK4217
ms.assetid: 280dc03e-5933-4e8d-bb8c-891fbe788738
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3c650eddd8078419f63df48cc91705d2e86eb5c8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067970"
---
# <a name="linker-tools-warning-lnk4217"></a>链接器工具警告 LNK4217

本地定义的符号 symbol 函数 function 中导入

[__declspec （dllimport)](../../cpp/dllexport-dllimport.md)即使本地定义了符号指定符号。 删除`__declspec`修饰符来解决此警告。

`symbol` 是映像中定义的符号名称。 `function` 是正在导入符号的函数。

通过使用选项进行编译时不会出现此警告[/clr](../../build/reference/clr-common-language-runtime-compilation.md)。

如果您尝试将两个模块链接在一起，而是应编译的第一个模块的导入库的第二个模块时，也可能发生 LNK4217。

```
// LNK4217.cpp
// compile with: /LD
#include "windows.h"
__declspec(dllexport) void func(unsigned short*) {}
```

然后，

```
// LNK4217b.cpp
// compile with: /c
#include "windows.h"
__declspec(dllexport) void func(unsigned short*) {}
```

尝试链接这两个模块将导致 LNK4217，编译第二个示例的第一个示例，若要解决的导入库。