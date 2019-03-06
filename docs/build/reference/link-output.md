---
title: LINK 输出
ms.date: 11/04/2016
f1_keywords:
- link
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
ms.openlocfilehash: c147a900d81465565ccbe73baf11570beb353554
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416119"
---
# <a name="link-output"></a>LINK 输出

Link 输出包括.exe 文件、 Dll、 映射文件和消息。

##  <a name="_core_output_files"></a> 输出文件

链接的默认输出文件是.exe 文件。 如果[/DLL](../../build/reference/dll-build-a-dll.md)指定选项，LINK 在生成.dll 文件。 您可以控制输出文件的名称与[输出文件的名称 (/out)](../../build/reference/out-output-file-name.md)选项。

在增量模式下，链接创建一个.ilk 文件来保存程序的更高版本的增量生成的状态信息。 有关.ilk 文件的详细信息，请参阅[.ilk 文件](../../build/reference/dot-ilk-files-as-linker-input.md)。 有关增量链接的详细信息，请参阅[增量链接 (/incremental)](../../build/reference/incremental-link-incrementally.md)选项。

当链接创建包含的程序将导出 (通常为 DLL) 时，它还将生成的.lib 文件，除非在生成中使用了.exp 文件。 您可以控制在导入库文件名[/IMPLIB](../../build/reference/implib-name-import-library.md)选项。

如果[生成映射文件 (/map)](../../build/reference/map-generate-mapfile.md)指定选项，链接创建映射文件。

如果[生成调试信息 (/debug)](../../build/reference/debug-generate-debug-info.md)指定选项，链接创建要包含的程序的调试信息的 PDB。

##  <a name="_core_other_output"></a> 其他输出

当您键入`link`而无需任何其他命令行输入时，链接将显示一条用法语句总结了其自己的选项。

链接显示版权和版本的消息，并回显命令文件输入，除非[取消显示启动版权标志 (/ NOLOGO)](../../build/reference/nologo-suppress-startup-banner-linker.md)使用选项。

可以使用[打印进度消息 (/verbose)](../../build/reference/verbose-print-progress-messages.md)选项以显示有关生成的其他详细信息。

链接会发出错误和警告消息中窗体 LNK*nnnn*。 由 LIB、 DUMPBIN 和 EDITBIN 还使用此错误前缀和的数字范围。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)
