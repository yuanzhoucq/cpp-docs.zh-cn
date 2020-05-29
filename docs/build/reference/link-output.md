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
ms.openlocfilehash: 253f88ed50b9f064edf976277a4618e4f101ec7e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331790"
---
# <a name="link-output"></a>LINK 输出

链接输出包括 .exe 文件、DLL、地图文件和消息。

## <a name="output-files"></a><a name="_core_output_files"></a>输出文件

LINK 的默认输出文件是 .exe 文件。 如果指定[了 /DLL](dll-build-a-dll.md)选项，LINK 将生成 .dll 文件。 您可以使用[输出文件名 （/OUT）](out-output-file-name.md)选项控制输出文件名。

在增量模式下，LINK 创建一个 .ilk 文件，用于保存程序以后增量生成的状态信息。 有关 .ilk 文件的详细信息，请参阅[.ilk 文件](dot-ilk-files-as-linker-input.md)。 有关增量链接的详细信息，请参阅[链接增量链接（/增量）](incremental-link-incrementally.md)选项。

当 LINK 创建包含导出的程序（通常是 DLL）时，它还会生成 .lib 文件，除非生成中使用了 .exp 文件。 您可以使用[/IMPLIB](implib-name-import-library.md)选项控制导入库文件名。

如果指定了["生成地图文件（/MAP）"](map-generate-mapfile.md)选项，LINK 将创建一个地图文件。

如果指定了[生成调试信息 （/DEBUG）](debug-generate-debug-info.md)选项，LINK 将创建一个 PDB 以包含该程序的调试信息。

## <a name="other-output"></a><a name="_core_other_output"></a>其他输出

当您在没有任何`link`任何其他命令行输入的情况下键入时，LINK 将显示一个用法语句，该语句汇总其选项。

LINK 显示版权和版本消息并回显命令文件输入，除非使用["抑制启动横幅 （/NOLOGO）"](nologo-suppress-startup-banner-linker.md)选项。

您可以使用["打印进度消息（/VERBOSE）"](verbose-print-progress-messages.md)选项来显示有关生成的其他详细信息。

LINK 在 LNK*nnnn*窗体中发出错误和警告消息。 LIB、DUMPBIN 和 EDITBIN 也使用此错误前缀和数字范围。

## <a name="see-also"></a>另请参阅

[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
