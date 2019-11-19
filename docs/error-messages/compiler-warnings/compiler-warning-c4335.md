---
title: 编译器警告 C4335
ms.date: 11/04/2016
f1_keywords:
- C4335
helpviewer_keywords:
- C4335
ms.assetid: e66467ad-a10b-4438-8c7c-e8e8d11d39bb
ms.openlocfilehash: ccb00118d0c6895eee84976bb01472ea2f98353d
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627126"
---
# <a name="compiler-warning-c4335"></a>编译器警告 C4335

检测到 Mac 文件格式：请将源文件转换为 DOS 格式或 UNIX 格式

源文件第一行的行终止字符为 Macintosh 样式（' \r '），而不是 UNIX （' \n '）或 DOS （' \r\n '）。

此警告总是作为错误发出。  有关如何禁用此警告的信息，请参阅[警告](../../preprocessor/warning.md)杂注。  此外，此警告只会针对每个编译单位发出一次。 因此，如果有多个 `#include` 指令指定了 Macintosh 格式的文件，则将只颁发 C4335 一次。

以 Macintosh 格式生成文件的一种方法是使用 Visual Studio 中的 "**高级保存选项**" （位于 "**文件**" 菜单上）。

## <a name="example"></a>示例

下面的示例生成 C4335。

```cpp
// C4335 expected
#include "c4335.h"   // assume both include files are in Macintosh format
#include "c4335_2.h"
```
