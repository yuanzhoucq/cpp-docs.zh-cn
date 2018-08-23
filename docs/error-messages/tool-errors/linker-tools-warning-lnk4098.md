---
title: 链接器工具警告 LNK4098 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4098
dev_langs:
- C++
helpviewer_keywords:
- LNK4098
ms.assetid: 1f1b1408-1316-4e34-80f5-6a02f2db0ac1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8aadf25d968d6d457f891cab49a43591455b9d12
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301702"
---
# <a name="linker-tools-warning-lnk4098"></a>链接器工具警告 LNK4098
与 defaultlib 库冲突的其他 libs; 使用使用 /NODEFAULTLIB:library  
  
 正在尝试与不兼容的库链接。  
  
> [!NOTE]
>  运行时库现在包含指令以防止混合不同类型。 同一程序中，将收到此警告如果您尝试使用不同的类型或调试和运行时库的非调试版本。 例如，如果编译一个文件，以使用一种运行时库，另一个文件以使用另一种 （例如，单线程方式而不是多线程），并尝试将它们链接，你将收到此警告。 应编译所有源代码文件，以使用相同的运行时库。 请参阅[使用运行时库](../../build/reference/md-mt-ld-use-run-time-library.md)(**/MD**， **/MT**， **/LD**) 编译器选项，有关详细信息。  
  
 你可以使用链接器的[/VERBOSE:LIB](../../build/reference/verbose-print-progress-messages.md)开关来确定链接器搜索的库。 如果你收到 LNK4098 并想要创建的可执行文件，例如，使用单线程，非调试运行时库，请使用 **/VERBOSE:LIB**选项以了解链接器搜索的库。 链接器应打印 LIBC.lib 和不 LIBCMT.lib、 MSVCRT.lib、 LIBCD.lib、 LIBCMTD.lib 或 MSVCRTD.lib 作为所搜索的库。 你可以判断链接器忽略不正确的运行时库通过使用[/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)为每个你想要忽略的库。  
  
 下表显示应忽略的库，你想要使用具体取决于哪个运行时库。  
  
|若要使用此运行时库|忽略这些库|  
|-----------------------------------|----------------------------|  
|单线程方式 (libc.lib)|libcmt.lib、 msvcrt.lib、 libcd.lib、 libcmtd.lib、 msvcrtd.lib|  
|多线程 (libcmt.lib)|libc.lib、 msvcrt.lib、 libcd.lib、 libcmtd.lib、 msvcrtd.lib|  
|使用 DLL (msvcrt.lib) 的多线程|libc.lib、 libcmt.lib、 libcd.lib、 libcmtd.lib、 msvcrtd.lib|  
|调试单线程方式 (libcd.lib)|libc.lib、 libcmt.lib、 msvcrt.lib、 libcmtd.lib、 msvcrtd.lib|  
|调试多线程 (libcmtd.lib)|libc.lib、 libcmt.lib、 msvcrt.lib、 libcd.lib、 msvcrtd.lib|  
|调试多线程使用 DLL (msvcrtd.lib)|libc.lib、 libcmt.lib、 msvcrt.lib、 libcd.lib、 libcmtd.lib|  
  
 例如，如果你收到此警告，并且你想要创建使用的非调试单线程版本运行时库的可执行文件，你可以用链接器使用以下选项：  
  
```  
/NODEFAULTLIB:libcmt.lib /NODEFAULTLIB:msvcrt.lib /NODEFAULTLIB:libcd.lib /NODEFAULTLIB:libcmtd.lib /NODEFAULTLIB:msvcrtd.lib  
```