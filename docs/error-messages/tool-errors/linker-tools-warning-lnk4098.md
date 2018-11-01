---
title: 链接器工具警告 LNK4098
ms.date: 11/04/2016
f1_keywords:
- LNK4098
helpviewer_keywords:
- LNK4098
ms.assetid: 1f1b1408-1316-4e34-80f5-6a02f2db0ac1
ms.openlocfilehash: 088124fcce7cafad3fab3280ae0b3ae0d893283e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468713"
---
# <a name="linker-tools-warning-lnk4098"></a>链接器工具警告 LNK4098

使用其他库; 的 defaultlib library 冲突使用 /nodefaultlib: library

正在尝试使用不兼容的库进行链接。

> [!NOTE]
>  在运行时库现在包含可防止混合不同类型的指令。 在同一程序中，将收到此警告如果您尝试使用不同类型或调试，并在运行时库的非调试版本。 例如，如果编译一个文件以使用一种运行时库，另一个文件以使用另一种 （例如，单线程还是多线程），并尝试将其链接，你将收到此警告。 您应该编译所有源代码文件，以使用相同的运行时库。 请参阅[使用运行时库](../../build/reference/md-mt-ld-use-run-time-library.md)(**/MD**， **/MT**， **/LD**) 编译器选项的详细信息。

可以使用链接器的[/VERBOSE:LIB](../../build/reference/verbose-print-progress-messages.md)开关，用于确定链接器搜索的库。 如果你收到 LNK4098 且想要创建可执行文件，例如，使用单线程、 非调试运行时库，请使用 **/VERBOSE:LIB**查找链接器搜索的库选项。 链接器应打印 LIBC.lib 和不 LIBCMT.lib、 MSVCRT.lib、 LIBCD.lib、 LIBCMTD.lib 或 MSVCRTD.lib 作为所搜索的库。 您可以告知链接器通过忽略不正确的运行时库[/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)为每个你想要忽略的库。

下表显示了应忽略的库，你想要使用具体取决于哪个运行时库。

|若要使用此运行时库|忽略这些库|
|-----------------------------------|----------------------------|
|单线程 (libc.lib)|libcmt.lib、 msvcrt.lib、 libcd.lib、 libcmtd.lib、 msvcrtd.lib|
|多线程 (libcmt.lib)|libc.lib、 msvcrt.lib、 libcd.lib、 libcmtd.lib、 msvcrtd.lib|
|多线程使用 DLL (msvcrt.lib)|libc.lib、 libcmt.lib、 libcd.lib、 libcmtd.lib、 msvcrtd.lib|
|调试单线程 (libcd.lib)|libc.lib、 libcmt.lib、 msvcrt.lib、 libcmtd.lib、 msvcrtd.lib|
|调试多线程 (libcmtd.lib)|libc.lib、 libcmt.lib、 msvcrt.lib、 libcd.lib、 msvcrtd.lib|
|调试多线程使用 DLL (msvcrtd.lib)|libc.lib、 libcmt.lib、 msvcrt.lib、 libcd.lib、 libcmtd.lib|

例如，如果收到此警告，并且你想要创建使用非调试、 单线程版本运行时库的可执行文件，您可以用链接器使用以下选项：

```
/NODEFAULTLIB:libcmt.lib /NODEFAULTLIB:msvcrt.lib /NODEFAULTLIB:libcd.lib /NODEFAULTLIB:libcmtd.lib /NODEFAULTLIB:msvcrtd.lib
```