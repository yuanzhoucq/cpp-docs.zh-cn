---
title: 链接器工具错误 LNK2011
ms.date: 11/04/2016
f1_keywords:
- LNK2011
helpviewer_keywords:
- LNK2011
ms.assetid: 04991ef5-49d5-46c7-8eee-a9d1d3fc541e
ms.openlocfilehash: e08f068099af68375523eae0f0cc4d63960f3261
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194806"
---
# <a name="linker-tools-error-lnk2011"></a>链接器工具错误 LNK2011

未链接预编译对象;映像可能无法运行

如果使用预编译头，则 LINK 要求必须在中链接使用预编译头创建的所有对象文件。 如果你有一个用于生成预编译标头以用于其他源文件的源文件，则你现在必须包含与预编译标头一起创建的对象文件。

例如，如果编译名为 STUB 的文件来创建与其他源文件一起使用的预编译头，则必须使用存根链接，否则将收到此错误。 在下面的命令行中，第一行用于创建预编译标头（通用 .pch），该标头与 PROG1 和 PROG2 的第二行和第三行使用。 文件存根只包含 `#include` 行（与 PROG1 和 PROG2 中相同的 `#include` 行），并且仅用于生成预编译头。 在最后一行中，存根必须链接到，以避免 LNK2011。

```
cl /c /Yccommon.h stub.cpp
cl /c /Yucommon.h prog1.cpp
cl /c /Yucommon.h prog2.cpp
link /out:prog.exe stub.obj prog1.obj prog2.obj
```
