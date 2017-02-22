---
title: "/TSAWARE（创建终端服务器识别的应用程序） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/tsaware"
  - "VC.Project.VCLinkerTool.TerminalServerAware"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/TSAWARE 链接器选项"
  - "终端服务器"
  - "终端服务器, 终端服务器识别应用程序"
  - "TSAWARE 链接器选项"
  - "-TSAWARE 链接器选项"
ms.assetid: fe1c1846-de5b-4839-b562-93fbfe36cd29
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# /TSAWARE（创建终端服务器识别的应用程序）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/TSAWARE[:NO]  
```  
  
## 备注  
 \/TSAWARE 选项在程序映像的可选标头中的 IMAGE\_OPTIONAL\_HEADER DllCharacteristics 字段内设置一个标记。  如果设置此标记，则终端服务器将无法对应用程序进行某些更改。  
  
 当应用程序不被终端服务器识别时（即所谓的旧版应用程序），终端服务器将对旧版应用程序进行某些修改，使其能在多用户环境中正常工作。  例如，终端服务器将创建虚拟 Windows 文件夹，这样每个用户得到的都是 Windows 文件夹而不是系统的 Windows 目录。  这使用户可以访问他们自己的 INI 文件。  另外，终端服务器对旧版应用程序的注册表进行某些调整。  这些修改减慢了旧版应用程序在终端服务器上的加载。  
  
 如果应用程序可由终端服务器识别，则在安装过程中它必须既不依赖于 INI 文件也不向 **HKEY\_CURRENT\_USER** 注册表写入。  
  
 如果使用 \/TSAWARE 并且应用程序仍使用 INI 文件，则这些文件将被系统的所有用户共享。  如果这是可接受的，则仍然可以将应用程序与 \/TSAWARE 链接；否则需要使用 \/TSAWARE:NO。  
  
 默认情况下，对于 Windows 2000 及更高版本、Windows 和控制台应用程序，\/TSAWARE 选项是启用的。  有关信息请参见 [\/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) 和 [\/VERSION](../../build/reference/version-version-information.md)。  
  
 \/TSAWARE 对于驱动程序、VxD 或 DLL 无效。  
  
 如果应用程序是与 \/TSAWARE 链接的，则 DUMPBIN [\/HEADERS](../../build/reference/headers.md) 将为此目的显示信息。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击“系统”属性页。  
  
4.  修改“终端服务器”属性。  
  
### 以编程方式设置此链接器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TerminalServerAware%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)   
 [Storing User\-Specific Information](http://msdn.microsoft.com/library/aa383452)   
 [Legacy Applications in a Terminal Services Environment](https://msdn.microsoft.com/en-us/library/aa382957.aspx)