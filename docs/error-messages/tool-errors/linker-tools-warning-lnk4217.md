---
title: 链接器工具警告 LNK4217
ms.date: 04/15/2019
f1_keywords:
- LNK4217
helpviewer_keywords:
- LNK4217
ms.assetid: 280dc03e-5933-4e8d-bb8c-891fbe788738
ms.openlocfilehash: f1ea3cd0a8770571ae5c55d29a901c134311550f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410221"
---
# <a name="linker-tools-warning-lnk4217"></a>链接器工具警告 LNK4217

> 符号*符号*中定义*filename_1.obj*导入*filename_2.obj*in function*函数*

[__declspec （dllimport)](../../cpp/dllexport-dllimport.md)即使在相同的映像中的对象文件中定义了符号指定符号。 删除`__declspec(dllimport)`修饰符来解决此警告。

## <a name="remarks"></a>备注

*符号*是映像中定义的符号名称。 *函数*是导入符号的函数。

通过使用编译时不会出现此警告[/clr](../../build/reference/clr-common-language-runtime-compilation.md)选项。

如果您尝试将两个模块链接在一起，而是应编译的第一个模块的导入库的第二个模块时，也可能发生 LNK4217。

```cpp
// LNK4217.cpp
// compile with: /LD
#include "windows.h"
__declspec(dllexport) void func(unsigned short*) {}
```

然后，

```cpp
// LNK4217b.cpp
// compile with: /c
#include "windows.h"
__declspec(dllexport) void func(unsigned short*) {}
```

尝试链接这两个模块将导致 LNK4217。 编译第二个示例的第一个示例，若要解决的导入库。

## <a name="see-also"></a>请参阅

[链接器工具警告 LNK4049](linker-tools-warning-lnk4049.md) \
[链接器工具警告 LNK4286](linker-tools-warning-lnk4286.md) \
[dllexport、dllimport](../../cpp/dllexport-dllimport.md)