---
title: "如何：使用 winmdidl.exe 和 midlrt.exe 通过窗口元数据创建 .h 文件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: 4be8ba11-c223-44ad-9256-7e1edae9a7bc
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 winmdidl.exe 和 midlrt.exe 通过窗口元数据创建 .h 文件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Winmdidl.exe 和 midlrt.exe 可在本机 C\+\+ 代码与 Windows 运行时组件之间实现 COM 级别交互。  Winmdidl.exe 采用包含 Windows 运行时组件元数据的 .winmd 文件作为输入，并输出 IDL 文件。  Midlrt.exe 将该 IDL 文件转换为 C\+\+ 代码可以使用的头文件。  这两个工具都在命令行上运行。  
  
 可在两个主要方案中使用这些工具：  
  
-   创建自定义 IDL 和头文件，以便使用 Windows 运行时模板库 \(WRL\) 编写的 C\+\+ 应用可以使用自定义 Windows 运行时组件。  
  
-   为 Windows 运行时组件中用户定义的事件类型生成代理和存根 \(Stub\) 文件。  有关详细信息，请参阅[在 Windows 运行时组件中引发事件](../Topic/Raising%20Events%20in%20Windows%20Runtime%20Components.md)。  
  
 只有分析自定义 .winmd 文件才需要这些工具。  已为你生成用于 Windows 操作系统组件的 .idl 和 .h 文件。  默认情况下，在 [!INCLUDE[win81](../misc/includes/win81_md.md)] 中，它们位于 \\Program Files \(x86\)\\Windows Kits\\8.1\\Include\\winrt\\。  
  
## 工具的位置  
 默认情况下，在 [!INCLUDE[win81](../misc/includes/win81_md.md)] 中，winmdidl.exe 和 midlrt.exe 位于 C:\\Program Files \(x86\)\\Windows Kits\\8.1\\。  \\bin\\x86\\ 和 \\bin\\x64\\ 文件夹中也提供了这些工具的相应版本。  
  
## Winmdidl 命令行参数  
  
```  
  
Winmdidl.exe [/nologo] [/supressversioncheck] [/time] [/outdir:dir] [/banner:file] [/utf8] Winmdfile  
  
```  
  
 `/nologo`  
 禁止控制台显示 winmdidl 版权消息和版本号。  
  
 `/supressversioncheck`  
 未使用。  
  
 `/time`  
 在控制台输出中显示总执行时间。  
  
 \/outdir:\<dir\>  
 指定输出目录。  如果路径包含空格，请使用引号。  默认输出目录是 *\<驱动器\>*:\\Users\\*\<用户名\>*\\AppData\\Local\\VirtualStore\\Program Files \(x86\)\\Microsoft Visual Studio 12.0\\。  
  
 `/banner:<file>`  
 指定一个文件，其中包含要在生成的 .idl 文件顶部追加到默认版权消息和 winmdidl 版本号前面的自定义文本。  如果路径包含空格，请使用引号。  
  
 `/utf8`  
 使文件格式化为 UTF\-8。  
  
 `Winmdfile`  
 要分析的 .winmd 文件的名称。  如果路径包含空格，请使用引号。  
  
## Midlrt 命令行参数  
 请参阅 [MIDLRT 和 Windows 运行时组件](http://msdn.microsoft.com/library/windows/desktop/hh869900\(v=vs.85\).aspx)。  
  
## 示例  
 下面的示例演示 Visual Studio x86 命令提示符处的 winmdidl 命令。  它指定一个输出目录，以及一个包含要添加到生成的 .idl 文件的特殊横幅文本的文件。  
  
 **C:\\Program Files \(x86\)\\Microsoft Visual Studio 12.0\>winmdidl \/nologo \/outdir:c:\\users\\giraffe\\documents\\ \/banner:c:\\users\\giraffe\\documents\\banner.txt "C:\\Users\\giraffe\\Documents\\Visual Studio 2013\\Projects\\Test\_for\_winmdidl\\Debug\\Test\_for\_winmdidl\\test\_for\_winmdidl.winmd"**  
  
 下一个示例演示 winmdidl 发出的指示操作已成功的控制台显示。  
  
 **Generating c:\\users\\giraffe\\documents\\\\Test\_for\_winmdidl.idl**  
  
 接下来，midlrt 在生成的 IDL 文件上运行。  请注意，**metadata\_dir** 参数在 .idl 文件的名称后指定。  \\WinMetadata\\ 的路径是必需的 — 它是 windows.winmd 的位置。  
  
 **C:\\Program Files \(x86\)\\Microsoft Visual Studio 12.0\> midlrt "c:\\users\\mblome\\documents\\test\_for\_winmdidl.idl" \/metadata\_dir "C:\\Windows\\System32\\WinMetadata"**  
  
## 备注  
 Winmdidl 操作的输出文件的名称与输入文件相同，但是具有 .idl 文件扩展名。  
  
 如果你在开发将从 WRL 访问的 Windows 运行时组件，则可以指定 winmdidl.exe 和 midlrt.exe 作为生成后步骤运行，以便在每次生成时都生成 .idl 和 .h 文件。  有关示例，请参阅[在 Windows 运行时组件中引发事件](../Topic/Raising%20Events%20in%20Windows%20Runtime%20Components.md)。