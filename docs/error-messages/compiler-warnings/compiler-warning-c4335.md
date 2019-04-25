---
title: 编译器警告 C4335
ms.date: 11/04/2016
f1_keywords:
- C4335
helpviewer_keywords:
- C4335
ms.assetid: e66467ad-a10b-4438-8c7c-e8e8d11d39bb
ms.openlocfilehash: 43c2f5d9092cdbad14e429349bd7d04e236b75e4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62151846"
---
# <a name="compiler-warning-c4335"></a>编译器警告 C4335

检测到 Mac 文件格式： 请将源文件转换为 DOS 或 UNIX 格式

源文件的第一行的行终止字符是 Macintosh 样式 ('\r') 而不是 UNIX ('\n') 或 DOS ('\r\n')。

作为错误发出始终发出此警告。  请参阅[警告](../../preprocessor/warning.md)了解如何禁用此警告的杂注。  此外，将发出此警告仅一次每个编译单位。 因此，如果有多个`#include`Macintosh 格式指定文件的指令，C4335 将才会发出一次。

适用于目标系统中生成文件的一种方法是使用**高级保存选项**(在**文件**菜单) 在 Visual Studio 中。

## <a name="example"></a>示例

下面的示例生成 C4335。

```
// C4335 expected
#include "c4335.h"   // assume both include files are in Macintosh format
#include "c4335_2.h"
```