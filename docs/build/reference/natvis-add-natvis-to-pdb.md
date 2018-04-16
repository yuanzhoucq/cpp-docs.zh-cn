---
title: -NATVIS （将添加到 PDB 的 Natvis） |Microsoft 文档
ms.date: 08/10/2017
ms.tgt_pltfrm: ''
ms.technology:
- cpp-tools
ms.topic: article
f1_keywords:
- /natvis
- VC.Project.VCLinkerTool.ImportLIbrary
dev_langs:
- C++
helpviewer_keywords:
- NATVIS linker option
- /NATVIS linker option
- -NATVIS linker option
- Add Natvis file to PDB
ms.assetid: 8747fc0c-701a-4796-bb4d-818ab4465cca
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 20715b48413a705aa2338e7e37538171e4141cad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="natvis-add-natvis-to-pdb"></a>/ NATVIS （将添加到 PDB 的 Natvis）
  
> / NATVIS:*filename*  
  
## <a name="parameters"></a>参数  
  
*filename*  
要添加到 PDB 文件的 Natvis 文件。 它在到 PDB 的 Natvis 文件中嵌入的调试器可视化效果。  
  
## <a name="remarks"></a>备注  
  
/NATVIS 选项嵌入 Natvis 文件中定义的调试器可视化效果*filename*到由 LINK 生成的 PDB 文件。 这使调试器能够显示独立于.natvis 文件的可视化效果。 多个 /NATVIS 选项可用于在生成的 PDB 文件中嵌入多个 Natvis 文件。  
  
PDB 文件不通过使用创建时，LINK 忽略 /NATVIS [/调试](../../build/reference/debug-generate-debug-info.md)选项。 有关创建和使用.natvis 文件的信息，请参阅[在 Visual Studio 调试器中创建本机对象的自定义视图](/visualstudio/debugger/create-custom-views-of-native-objects)。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择**命令行**中的属性页**链接器**文件夹。  
  
3.  添加到 /NATVIS 选项**其他选项**文本框。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
-   此选项没有编程等效。  
  
## <a name="see-also"></a>请参阅  
  
[在 Visual Studio 调试器中创建本机对象的自定义视图](/visualstudio/debugger/create-custom-views-of-native-objects)  
[设置链接器选项](../../build/reference/setting-linker-options.md)  
[链接器选项](../../build/reference/linker-options.md)