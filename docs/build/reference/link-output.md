---
title: "LINK 输出 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "link"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".ilk 文件"
  - "DLL [C++], 作为链接器输出"
  - "可执行文件 [C++], 作为链接器输出"
  - "文件 [C++], LINK"
  - "ILK 文件"
  - "导入库 [C++], 创建"
  - "LINK 工具 [C++], 映射文件"
  - "LINK 工具 [C++], 输出"
  - "链接器 [C++], 输出文件"
  - "映射文件 [C++]"
  - "映射文件 [C++], LINK 输出"
  - "输出文件 [C++], 链接器"
ms.assetid: a98b557c-1947-447a-be1f-616fb45a9580
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# LINK 输出
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Link 输出包括 .exe 文件、DLL、映射文件和消息。  
  
##  <a name="_core_output_files"></a> 输出文件  
 LINK 的默认输出文件是 .exe 文件。  如果指定了 [\/DLL](../../build/reference/dll-build-a-dll.md) 选项，则 LINK 生成 .dll 文件。  可以用[输出文件名称 \(\/OUT\)](../../build/reference/out-output-file-name.md) 选项控制输出文件名。  
  
 在增量模式中，LINK 创建一个 .ilk 文件来保存程序后来的增量编译状态信息。  有关 .ilk 文件的详细信息，请参见 [.ilk 文件](../../build/reference/dot-ilk-files-as-linker-input.md)。  有关增量链接的更多信息，请参见[渐进式链接 \(\/INCREMENTAL\)](../../build/reference/incremental-link-incrementally.md) 选项。  
  
 当 LINK 创建包含导出（通常是 DLL）的程序时，如果在生成中没有使用 .exp 文件，它还将生成 .lib 文件。  可以用 [\/IMPLIB](../../build/reference/implib-name-import-library.md) 选项控制导入库文件名。  
  
 如果指定了[生成映射文件 \(\/MAP\)](../../build/reference/map-generate-mapfile.md) 选项，则 LINK 创建映射文件。  
  
 如果指定了[生成调试信息 \(\/DEBUG\)](../../build/reference/debug-generate-debug-info.md) 选项，则 LINK 创建 PDB 以包含程序的调试信息。  
  
##  <a name="_core_other_output"></a> 其他输出  
 当键入 `link` 时不带任何其他命令行输入，LINK 将显示总结其选项的用法语句。  
  
 如果没有使用[取消显示启动版权标志 \(\/NOLOGO\)](../../build/reference/nologo-suppress-startup-banner-linker.md) 选项，则 LINK 显示版权和版本消息，并回显命令文件输入。  
  
 可以使用[显示进度消息 \(\/VERBOSE\)](../../build/reference/verbose-print-progress-messages.md) 选项显示有关生成的附加详细信息。  
  
 LINK 以 LNK*nnnn* 的格式发出错误信息和警告消息。  LIB、DUMPBIN 和 EDITBIN 也使用该错误前缀和数字范围。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)