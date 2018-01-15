---
title: "版本 （版本信息） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.Version
- /version
dev_langs: C++
helpviewer_keywords:
- -VERSION linker option
- Version Information linker option
- version numbers, specifying in .exe
- /VERSION linker option
- VERSION linker option
ms.assetid: b86d0e86-dca6-4316-aee2-d863ccb9f223
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: aeb8d2845c5e8daa931e354b149fc1c35b37fbd7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="version-version-information"></a>/VERSION（版本信息）
```  
/VERSION:major[.minor]  
```  
  
## <a name="remarks"></a>备注  
 其中：  
  
 *主要*和*次要*  
 所需的.exe 或.dll 文件的标头中的版本号。  
  
## <a name="remarks"></a>备注  
 /VERSION 选项通知链接器将版本号.exe 或.dll 文件的标头中。 使用 DUMPBIN [/HEADERS](../../build/reference/headers.md)才能看到该映像版本字段的可选的标头值，以查看 /VERSION 的效果。  
  
 *主要*和*次要*自变量为十进制数字 0 到 65535 的范围。 默认值为 0.0 版。  
  
 使用 /VERSION 指定的信息不影响您在文件资源管理器中查看应用程序属性时为应用程序显示的版本信息。 该版本信息来自资源文件，用于生成应用程序。 请参阅[版本信息编辑器](../../windows/version-information-editor.md)有关详细信息。  
  
 要插入的版本号的另一个方法是使用[版本](../../build/reference/version-c-cpp.md)模块定义语句。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击**链接器**文件夹。  
  
3.  单击**常规**属性页。  
  
4.  修改**版本**属性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Version%2A>。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)