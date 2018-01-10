---
title: "LINK 输出 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: link
dev_langs: C++
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
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 567a87ab5cb4badd5f32423b8fb3067b21c46e9e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="link-output"></a>LINK 输出
Link 输出包括.exe 文件、 Dll、 映射文件和消息。  
  
##  <a name="_core_output_files"></a>输出文件  
 链接的默认输出文件是.exe 文件。 如果[/DLL](../../build/reference/dll-build-a-dll.md)指定选项，LINK 在生成.dll 文件。 你可以控制输出文件的名称与[输出文件的名称 （/ OUT）](../../build/reference/out-output-file-name.md)选项。  
  
 在增量模式下，链接创建一个.ilk 文件来保存更高版本增量编译的程序的状态信息。 .Ilk 文件有关的详细信息，请参阅[.ilk 文件](../../build/reference/dot-ilk-files-as-linker-input.md)。 有关增量链接的详细信息，请参阅[增量链接 (/incremental)](../../build/reference/incremental-link-incrementally.md)选项。  
  
 当 LINK 将创建包含的程序导出 (通常为 DLL) 时，它还将生成的.lib 文件，除非生成中使用了.exp 文件。 你可以控制在导入库文件名前面加[/IMPLIB](../../build/reference/implib-name-import-library.md)选项。  
  
 如果[生成映射文件 （/ 映射）](../../build/reference/map-generate-mapfile.md)指定选项，则 LINK 创建映射文件。  
  
 如果[生成调试信息 (/debug)](../../build/reference/debug-generate-debug-info.md)指定选项，则 LINK 创建包含调试信息的程序的 PDB。  
  
##  <a name="_core_other_output"></a>其他输出  
 当你键入`link`而无需任何其他命令行输入时，链接将显示一条总结了其选项的用法语句。  
  
 LINK 显示版权和版本号消息并回显命令文件输入，除非[取消显示启动版权标志 (/ NOLOGO)](../../build/reference/nologo-suppress-startup-banner-linker.md)使用选项。  
  
 你可以使用[打印进度消息 （/ 详细）](../../build/reference/verbose-print-progress-messages.md)选项以显示有关生成的其他详细信息。  
  
 链接会发出错误和警告消息的形式 LNK*nnnn*。 此错误前缀和的数字的范围也使用 LIB、 DUMPBIN 和 EDITBIN。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)