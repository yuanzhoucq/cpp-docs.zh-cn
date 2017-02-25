---
title: "/STUB（MS-DOS 存根 (stub) 文件名） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/stub"
  - "VC.Project.VCLinkerTool.DosStub"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/STUB 链接器选项"
  - "MS-DOS stub 文件名链接器选项"
  - "STUB 链接器选项"
  - "-STUB 链接器选项"
  - "Win32 [C++], 附加 MS-DOS stub 程序"
  - "Windows API [C++], 附加 MS-DOS stub 程序"
ms.assetid: 65221ffe-4f9a-4a14-ac69-3cfb79b40b5f
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# /STUB（MS-DOS 存根 (stub) 文件名）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/STUB:filename  
```  
  
## 备注  
 其中：  
  
 *filename*  
 MS\-DOS 应用程序。  
  
## 备注  
 \/STUB 选项将 MS\-DOS 存根\(Stub\)程序附加到 Win32 程序。  
  
 如果在 MS\-DOS 中执行文件，则将调用存根 \(stub\) 程序。  它通常显示适当的消息；然而，任何有效的 MS\-DOS 应用程序都可以是存根 \(stub\) 程序。  
  
 在命令行上冒号 \(:\) 之后，为存根 \(stub\) 程序指定 *filename*。  如果文件不是可执行文件，则链接器检查 *filename* 并发出错误信息。  程序必须是 .exe 文件；.com 文件对于存根 \(stub\) 程序无效。  
  
 如果不使用该选项，则链接器附加发出以下消息的默认存根 \(stub\) 程序：  
  
```  
This program cannot be run in MS-DOS mode.  
```  
  
 当生成虚拟设备驱动程序时，*filename* 使用户得以指定文件名，该文件名包含要用于 VXD 中而不是默认头的 IMAGE\_DOS\_HEADER 结构（在 WINNT.H 中定义）。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击**“命令行”**属性页。  
  
4.  将该选项键入**“附加选项”**框中。  
  
### 以编程方式设置此链接器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)