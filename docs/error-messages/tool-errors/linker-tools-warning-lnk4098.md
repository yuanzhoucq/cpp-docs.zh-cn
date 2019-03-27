---
title: 链接器工具警告 LNK4098
ms.date: 03/26/2019
f1_keywords:
- LNK4098
helpviewer_keywords:
- LNK4098
ms.assetid: 1f1b1408-1316-4e34-80f5-6a02f2db0ac1
ms.openlocfilehash: 66cf1a1bc75405ffc9bae8158bfc8682776a8228
ms.sourcegitcommit: 06fc71a46e3c4f6202a1c0bc604aa40611f50d36
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/27/2019
ms.locfileid: "58508723"
---
# <a name="linker-tools-warning-lnk4098"></a>链接器工具警告 LNK4098

> defaultlib '*库*冲突与其他库的使用; 请使用 /NODEFAULTLIB:*库*

想要使用不兼容的库进行链接。

> [!NOTE]
> 在运行时库现在包含可防止混合不同类型的指令。 在同一程序中，将收到此警告如果您尝试使用不同类型或调试，并在运行时库的非调试版本。 例如，如果编译一个文件以使用一种类型的运行时库和要使用另一种类型的另一个文件 （例如，零售和调试），尝试将其链接，你将收到此警告。 您应该编译所有源代码文件，以使用相同的运行时库。 有关详细信息，请参阅[/MD、 /MT、 /LD （使用运行时库）](../../build/reference/md-mt-ld-use-run-time-library.md)编译器选项。

可以使用链接器的[/VERBOSE:LIB](../../build/reference/verbose-print-progress-messages.md)切换到查找在链接器搜索的库。 例如，当可执行文件使用多线程、 非调试运行时库时，报告列表应包括 LIBCMT.lib，和不 LIBCMTD.lib、 MSVCRT.lib 或 MSVCRTD.lib。 您可以告知链接器通过忽略不正确的运行时库[/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)为每个你想要忽略的库。

下表显示了应忽略的库，你想要使用具体取决于哪个运行时库。 在命令行上使用一个 **/NODEFAULTLIB**忽略每个库的选项。 在 Visual Studio IDE 中，单独的库中的分号分隔的忽略**忽略特定默认库**属性。

| 若要使用此运行时库 | 忽略这些库 |
|-----------------------------------|----------------------------|
| 多线程 (libcmt.lib) | msvcrt.lib; libcmtd.lib; msvcrtd.lib |
| 多线程使用 DLL (msvcrt.lib) | libcmt.lib; libcmtd.lib; msvcrtd.lib |
| 调试多线程 (libcmtd.lib) | libcmt.lib; msvcrt.lib; msvcrtd.lib |
| 调试多线程使用 DLL (msvcrtd.lib) | libcmt.lib; msvcrt.lib; libcmtd.lib |

例如，如果你收到此警告，并且你想要创建的可执行文件，它使用运行时库的非调试 DLL 版本，可以使用链接器使用以下选项：

```cmd
/NODEFAULTLIB:libcmt.lib NODEFAULTLIB:libcmtd.lib /NODEFAULTLIB:msvcrtd.lib
```