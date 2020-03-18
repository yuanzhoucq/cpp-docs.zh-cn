---
title: LINK 输出
ms.date: 11/04/2016
helpviewer_keywords:
- mapfiles [C++]
- ILK files
- output files [C++], linker
- files [C++], LINK
- .ilk files
- LINK tool [C++], output
- import libraries [C++], creating
- executable files [C++], as linker output
- mapfiles [C++], LINK output
- linker [C++], output files
- DLLs [C++], as linker output
- LINK tool [C++], mapfile
ms.assetid: a98b557c-1947-447a-be1f-616fb45a9580
ms.openlocfilehash: 8323723f2049d3db469e874c91b99f4cfb561c72
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439323"
---
# <a name="link-output"></a>LINK 输出

链接输出包含 .exe 文件、Dll、映射文件和消息。

##  <a name="_core_output_files"></a>输出文件

LINK 的默认输出文件为 .exe 文件。 如果指定了[/DLL](dll-build-a-dll.md)选项，则 LINK 生成 .dll 文件。 可以用[输出文件名（/out）](out-output-file-name.md)选项控制输出文件的名称。

在增量模式下，LINK 创建 .ilk 文件以保存程序的后续增量生成的状态信息。 有关 .ilk 文件的详细信息，请参阅[.Ilk 文件](dot-ilk-files-as-linker-input.md)。 有关增量链接的详细信息，请参阅[增量式链接（/INCREMENTAL）](incremental-link-incrementally.md)选项。

当 LINK 创建包含导出的程序（通常为 DLL）时，它还会生成 .lib 文件，除非在生成中使用了 .exp 文件。 可以通过[/IMPLIB](implib-name-import-library.md)选项控制导入库的文件名。

如果指定了 "[生成映射映射（/MAP）](map-generate-mapfile.md) " 选项，则 LINK 将创建映射。

如果指定了 "[生成调试信息（/debug）](debug-generate-debug-info.md) " 选项，则 LINK 将创建一个 PDB 来包含程序的调试信息。

##  <a name="_core_other_output"></a>其他输出

在不使用任何其他命令行输入的情况下键入 `link` 时，LINK 将显示汇总其选项的使用情况语句。

LINK 显示版权和版本消息，并回显命令文件输入，除非使用 "[取消显示启动版权标志" （/nologo）](nologo-suppress-startup-banner-linker.md)选项。

您可以使用 "[打印进度消息（/verbose）](verbose-print-progress-messages.md) " 选项显示有关生成的其他详细信息。

以 .LNK*nnnn*的形式链接问题错误和警告消息。 LIB、DUMPBIN 和 EDITBIN 也使用此错误前缀和数字范围。

## <a name="see-also"></a>另请参阅

[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
