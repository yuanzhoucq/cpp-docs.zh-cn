---
title: "-WINMDFILE (指定 winmd 文件) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadataFile
dev_langs:
- C++
ms.assetid: 062b41b3-14d6-432c-a361-fdb66e918931
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 153e5c0bd42b6fdba59e309483f25f09b86fe9fa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="winmdfile-specify-winmd-file"></a>/WINMDFILE（指定 winmd 文件）
指定生成的 Windows 运行时元数据 (.winmd) 输出文件的文件名称[/WINMD](../../build/reference/winmd-generate-windows-metadata.md)链接器选项。  
  
```  
/WINMDFILE:filename  
```  
  
## <a name="remarks"></a>备注  
 使用 `filename` 中指定的值重写默认的 .winmd 文件名 (`binaryname`.winmd)。 请注意不要将".winmd"追加到`filename`。  如果多个值列出上**/WINMDFILE**命令行中，最后一个优先。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择**链接器**文件夹。  
  
3.  选择**Windows 元数据**属性页。  
  
4.  在**Windows 元数据文件**框中，输入文件位置。  
  
## <a name="see-also"></a>请参阅  
 [/WINMD （生成 Windows 元数据）](../../build/reference/winmd-generate-windows-metadata.md)   
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)