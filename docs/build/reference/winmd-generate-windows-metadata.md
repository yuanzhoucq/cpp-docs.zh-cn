---
title: "-WINMD （生成 Windows 元数据） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadata
dev_langs:
- C++
ms.assetid: bcfb4901-411e-4c9e-9f78-23028b6e5fcc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7517ec459677659067e80930ee48caccf84d52f3
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="winmd-generate-windows-metadata"></a>/WINMD（生成 Windows 元数据）
启用 Windows 运行时元数据 (.winmd) 文件的生成。  
  
```  
/WINMD[:{NO|ONLY}]  
```  
  
## <a name="remarks"></a>备注  
 /WINMD  
 通用 Windows 平台应用程序默认设置。 链接器生成二进制可执行文件和 .winmd 元数据文件。  
  
 /WINMD:NO  
 链接器仅生成二进制可执行文件，但不生成 .winmd 文件。  
  
 /WINMD:ONLY  
 链接器仅生成 .winmd 文件，但不生成二进制可执行文件。  
  
 默认情况下，输出文件名的形式是 `binaryname`.winmd。 若要指定不同的文件名，请使用[/WINMDFILE](../../build/reference/winmdfile-specify-winmd-file.md)选项。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择**链接器**文件夹。  
  
3.  选择**Windows 元数据**属性页。  
  
4.  在**生成 Windows 元数据**下拉列表框中，选择所需的选项。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)