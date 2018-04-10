---
title: -hotpatch （创建可热修补的映像） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- /hotpatch
- VC.Project.VCCLCompilerTool.CreateHotpatchableImage
dev_langs:
- C++
helpviewer_keywords:
- hot patching
- -hotpatch compiler option [C++]
- /hotpatch compiler option [C++]
- hotpatching
ms.assetid: aad539b6-c053-4c78-8682-853d98327798
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ad7ab4e6450d33923b728f20c8a35185edd2b05e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="hotpatch-create-hotpatchable-image"></a>/hotpatch（创建可热修补的映像）
准备映像以进行热修补。  
  
## <a name="syntax"></a>语法  
  
```  
/hotpatch  
```  
  
## <a name="remarks"></a>备注  
 当**/hotpatch**使用在编译时，编译器可确保每个函数的第一个指令为至少两个字节，这是进行热修补所要求。  
  
 若要完成的准备工作，在使用后使映像可热修补， **/hotpatch**进行编译时，必须使用[/FUNCTIONPADMIN （创建可热修补的映像）](../../build/reference/functionpadmin-create-hotpatchable-image.md)链接。 在编译和链接映像使用的 cl.exe，一次调用**/hotpatch**意味着**/functionpadmin**。  
  
 由于指令始终两个字节或更大 ARM 体系结构，而是因为 x64 编译总是被视为如同**/hotpatch**已指定，无需指定**/hotpatch**时为这些目标; 编译但是，你必须仍使用链接**/functionpadmin**若要为其创建可热修补的映像。 **/Hotpatch**编译器选项仅影响 x86 编译。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择**C/c + +**文件夹。  
  
3.  选择**命令行**属性页。  
  
4.  添加到编译器选项**其他选项**框。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="guidance"></a>指导  
 有关更新管理的详细信息，请参阅"安全指南适用于更新管理"在[http://www.microsoft.com/technet/security/guidance/PatchManagement.mspx](http://www.microsoft.com/technet/security/guidance/PatchManagement.mspx)。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)