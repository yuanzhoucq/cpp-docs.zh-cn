---
title: 如何： 使用 winmdidl.exe 和 midlrt.exe 通过窗口元数据创建.h 文件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 4be8ba11-c223-44ad-9256-7e1edae9a7bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f93570d18373a2e5ab4c698a9a85d4412129dd17
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39650604"
---
# <a name="how-to-use-winmdidlexe-and-midlrtexe-to-create-h-files-from-windows-metadata"></a>如何：使用 winmdidl.exe 和 midlrt.exe 通过窗口元数据创建 .h 文件
Winmdidl.exe 和 midlrt.exe 可在本机 C++ 代码与 Windows 运行时组件之间实现 COM 级别交互。 Winmdidl.exe 采用包含 Windows 运行时组件元数据的 .winmd 文件作为输入，并输出 IDL 文件。 Midlrt.exe 将该 IDL 文件转换为 C++ 代码可以使用的头文件。 这两个工具都在命令行上运行。  
  
 可在两个主要方案中使用这些工具：  
  
-   创建自定义 IDL 和头文件，以便使用 Windows 运行时模板库 (WRL) 编写的 C++ 应用可以使用自定义 Windows 运行时组件。  
  
-   为 Windows 运行时组件中用户定义的事件类型生成代理和存根 (Stub) 文件。 有关详细信息，请参阅[自定义事件和 Windows 运行时组件中的事件访问器](/uwp/winrt-components/custom-events-and-event-accessors-in-windows-runtime-components)。  
  
 只有分析自定义 .winmd 文件才需要这些工具。 已为你生成用于 Windows 操作系统组件的 .idl 和 .h 文件。 默认情况下[!INCLUDE[win81](../misc/includes/win81_md.md)]，这些文件位于 \Program 文件 (x86) \Windows Kits\8.1\Include\winrt\\。  
  
## <a name="location-of-the-tools"></a>工具的位置  
 默认情况下[!INCLUDE[win81](../misc/includes/win81_md.md)]，winmdidl.exe 和 midlrt.exe 位于 C:\Program Files (x86) \Windows Kits\8.1\\。 \bin\x86\ 和 \bin\x64\ 文件夹中也提供了这些工具的相应版本。  
  
## <a name="winmdidl-command-line-arguments"></a>Winmdidl 命令行自变量  
  
```  
Winmdidl.exe [/nologo] [/supressversioncheck] [/time] [/outdir:dir] [/banner:file] [/utf8] Winmdfile  
```  
  
 `/nologo`  
 禁止控制台显示 winmdidl 版权消息和版本号。  
  
 `/supressversioncheck`  
 未使用。  
  
 `/time`  
 在控制台输出中显示总执行时间。  
  
 /outdir:\<dir >  
 指定输出目录。 如果路径包含空格，请使用引号。 默认输出目录是*\<驱动器 >*: \Users\\*\<用户名 >* \AppData\Local\VirtualStore\Program 文件 (x86) \Microsoft VisualStudio 12.0\\。  
  
 `/banner:<file>`  
 指定一个文件，其中包含要在生成的 .idl 文件顶部追加到默认版权消息和 winmdidl 版本号前面的自定义文本。 如果路径包含空格，请使用引号。  
  
 `/utf8`  
 使文件格式化为 UTF-8。  
  
 `Winmdfile`  
 要分析的 .winmd 文件的名称。 如果路径包含空格，请使用引号。  
  
## <a name="midlrt-command-line-arguments"></a>Midlrt 命令行自变量  
 请参阅[MIDLRT 和 Windows 运行时组件](http://msdn.microsoft.com/library/windows/desktop/hh869900\(v=vs.85\).aspx)。  
  
## <a name="examples"></a>示例  
 下面的示例演示 Visual Studio x86 命令提示符处的 winmdidl 命令。 它指定一个输出目录，以及一个包含要添加到生成的 .idl 文件的特殊横幅文本的文件。  
  
 `C:\Program Files (x86)\Microsoft Visual Studio 12.0>winmdidl /nologo /outdir:c:\users\giraffe\documents\ /banner:c:\users\giraffe\documents\banner.txt "C:\Users\giraffe\Documents\Visual Studio 2013\Projects\Test_for_winmdidl\Debug\Test_for_winmdidl\test_for_winmdidl.winmd"`  
  
 下一个示例演示 winmdidl 发出的指示操作已成功的控制台显示。  
  
 **生成 c:\users\giraffe\documents\\\Test_for_winmdidl.idl**  
  
 接下来，midlrt 在生成的 IDL 文件上运行。 请注意， **/metadata_dir**参数指定.idl 文件的名称。 \WinMetadata\ 的路径是必需的 — 它是 windows.winmd 的位置。  
  
 `C:\Program Files (x86)\Microsoft Visual Studio 12.0> midlrt "c:\users\mblome\documents\test_for_winmdidl.idl" /metadata_dir "C:\Windows\System32\WinMetadata"`  
  
## <a name="remarks"></a>备注  
 Winmdidl 操作的输出文件的名称与输入文件相同，但是具有 .idl 文件扩展名。  
  
 如果你在开发将从 WRL 访问的 Windows 运行时组件，则可以指定 winmdidl.exe 和 midlrt.exe 作为生成后步骤运行，以便在每次生成时都生成 .idl 和 .h 文件。 有关示例，请参阅[在 Windows 运行时组件中引发事件](/uwp/winrt-components/raising-events-in-windows-runtime-components)。