---
title: "存根 （MS-DOS 存根 （stub） 文件名） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /stub
- VC.Project.VCLinkerTool.DosStub
dev_langs:
- C++
helpviewer_keywords:
- Win32 [C++], attaching MS-DOS stub program
- STUB linker option
- MS-DOS stub file name linker option
- /STUB linker option
- Windows API [C++], attaching MS-DOS stub program
- -STUB linker option
ms.assetid: 65221ffe-4f9a-4a14-ac69-3cfb79b40b5f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2bb7d1b9f56e7cea5d476d5ece6bdfab50fbe7a9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="stub-ms-dos-stub-file-name"></a>/STUB（MS-DOS 存根 (stub) 文件名）
```  
/STUB:filename  
```  
  
## <a name="remarks"></a>备注  
 其中：  
  
 *filename*  
 MS-DOS 应用程序。  
  
## <a name="remarks"></a>备注  
 /STUB 选项将 MS-DOS 存根程序附加到 Win32 程序。  
  
 如果在 MS-DOS 中执行文件，调用存根 （stub） 程序。 它通常显示适当的消息;但是，任何有效的 MS-DOS 应用程序可以是存根 （stub） 程序。  
  
 指定*filename*存根 （stub） 程序命令行上冒号 （:） 之后。 链接器检查*filename*并发出错误消息，如果文件不是可执行文件。 该程序必须是.exe 文件;.com 文件是无效的存根 （stub） 程序。  
  
 如果未使用此选项，则链接器将附加默认的存根 （stub） 程序颁发以下消息：  
  
```  
This program cannot be run in MS-DOS mode.  
```  
  
 生成虚拟设备驱动程序时, *filename*允许用户指定文件的名称包含 IMAGE_DOS_HEADER 结构结构 （在 WINNT 中定义。H) 可以用于 VXD，而不是默认标头中。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击**链接器**文件夹。  
  
3.  点击“命令行”  属性页。  
  
4.  该选项键入**其他选项**框。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)