---
title: -WINMD （生成 Windows 元数据） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadata
dev_langs:
- C++
ms.assetid: bcfb4901-411e-4c9e-9f78-23028b6e5fcc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0d3e628713c8228675db3b34e70d670c88152462
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376174"
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