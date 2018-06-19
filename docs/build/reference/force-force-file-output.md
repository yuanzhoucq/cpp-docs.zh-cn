---
title: -FORCE （强制文件输出） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.ForceLink
- /force
dev_langs:
- C++
helpviewer_keywords:
- FORCE linker option
- file output in linker
- /FORCE linker option
- -FORCE linker option
ms.assetid: b1e9a218-a5eb-4e60-a4a4-65b4be15e5da
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d1daa27ce48590d4a122eafde9f63f7142271610
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373695"
---
# <a name="force-force-file-output"></a>/FORCE（强制文件输出）
```  
/FORCE:[MULTIPLE|UNRESOLVED]  
```  
  
## <a name="remarks"></a>备注  
 /FORCE 选项通知链接器来创建有效的.exe 文件或 DLL 即使符号引用但未定义或多次定义。  
  
 /FORCE 选项可以采用可选的参数：  
  
-   使用 /FORCE:MULTIPLE 链接查找符号的多个定义创建的输出文件。  
  
-   使用 /FORCE： 未解析是否链接查找未定义的符号创建输出文件。 / 强制： 无法解析未解析入口点符号是否忽略。  
  
 / 不带任何参数 FORCE 意味着这两个多个，并且未解析。  
  
 使用此选项创建的文件可能未按预期运行。 链接器不会在指定 /FORCE 选项时以增量方式将链接。  
  
 如果使用编译模块 **/clr**， **/强制**将不会创建映像。  
  
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