---
title: "-PGD （按配置文件优化指定数据库） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.ProfileGuidedDatabase
dev_langs:
- C++
helpviewer_keywords:
- -PGD linker option
- /PGD linker option
ms.assetid: 9f312498-493b-461f-886f-92652257e443
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cb61395d9f3b8c98e17e3683a7c3897b9315d78b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="pgd-specify-database-for-profile-guided-optimizations"></a>/PGD（为按配置文件优化指定数据库）
/PGD:`filename`  
  
## <a name="remarks"></a>备注  
 其中：  
  
 `filename`  
 指定将用于保存有关正在运行的程序的信息的.pgd 文件的名称。  
  
## <a name="remarks"></a>备注  
 使用时[/ltcg: pginstrument](../../build/reference/ltcg-link-time-code-generation.md)，/PGD 用于指定非默认名称或使用.pgd 文件的位置。 如果未指定 /PGD，.pgd 文件名称将与输出文件 （.exe 或.dll） 名称相同，并且将在从中调用该链接的同一目录中创建。  
  
 在使用 /ltcg: pgoptimize，使用 /PGD 来指定要用于创建优化的映像的.pgd 文件的名称。  
  
 有关详细信息，请参阅[按配置优化](../../build/reference/profile-guided-optimizations.md)。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  展开**配置属性**节点。  
  
3.  展开**链接器**节点。  
  
4.  选择**优化**属性页。  
  
5.  修改**按配置优化数据库**属性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
1.  请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProfileGuidedDatabase%2A>。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)