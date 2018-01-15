---
title: "-TSAWARE （创建终端服务器感知应用程序） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /tsaware
- VC.Project.VCLinkerTool.TerminalServerAware
dev_langs: C++
helpviewer_keywords:
- Terminal Server
- /TSAWARE linker option
- Terminal Server, Terminal Server-aware applications
- -TSAWARE linker option
- TSAWARE linker option
ms.assetid: fe1c1846-de5b-4839-b562-93fbfe36cd29
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4c6fb783f717f730945f8d34c8fe2a03f5e1f6d0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="tsaware-create-terminal-server-aware-application"></a>/TSAWARE（创建终端服务器识别的应用程序）
```  
/TSAWARE[:NO]  
```  
  
## <a name="remarks"></a>备注  
 /TSAWARE 选项的程序映像的可选标头中的 IMAGE_OPTIONAL_HEADER DllCharacteristics 字段中设置一个标志。 当设置此标志后，终端服务器将不会向应用程序进行某些更改。  
  
 当应用程序不被终端服务器识别 （也称为旧应用程序） 时，终端服务器将进行某些修改到旧的应用程序，以使它在多用户环境中正常运行。 例如，终端服务器将创建的虚拟 Windows 文件夹中，以便每个用户获取 Windows 文件夹而不是获得系统的 Windows 目录。 这使用户访问其自己的 INI 文件。 此外，终端服务器将进行一些调整到的旧版应用程序的注册表。 这些修改会终端服务器上的旧应用程序加载变慢。  
  
 如果应用程序是终端服务器识别时，它必须既不依赖于 INI 文件也不写入**HKEY_CURRENT_USER**在安装过程中的注册表。  
  
 如果你使用 /TSAWARE 并且你的应用程序仍然使用通过 INI 文件，文件将由系统的所有用户共享。 如果这是可接受，则仍可以链接 /TSAWARE; 上的应用程序否则，你需要使用 /TSAWARE:NO。  
  
 /TSAWARE 选项为 Windows 和控制台应用程序启用 Windows 2000 及更高版本，默认情况下。 请参阅[/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md)和[/VERSION](../../build/reference/version-version-information.md)有关信息。  
  
 /TSAWARE 驱动程序、 VxDs，或 Dll 无效。  
  
 如果应用程序已链接使用 /TSAWARE，DUMPBIN [/HEADERS](../../build/reference/headers.md)将显示针对此效果的信息。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击**链接器**文件夹。  
  
3.  单击**系统**属性页。  
  
4.  修改**终端服务器**属性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TerminalServerAware%2A>。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)   
 [存储特定于用户的信息](http://msdn.microsoft.com/library/aa383452)   
 [终端服务环境中的旧应用程序](https://msdn.microsoft.com/en-us/library/aa382957.aspx)