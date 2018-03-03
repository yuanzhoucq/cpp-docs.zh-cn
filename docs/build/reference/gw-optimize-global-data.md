---
title: "-Gw （优化全局数据） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /Gw
dev_langs:
- C++
helpviewer_keywords:
- /Gw compiler option [C++]
- -Gw compiler option [C++]
ms.assetid: 6f90f4e9-5eb8-4c47-886e-631278a5a4a9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e849ee51a231c6f0d3d696a3aaa9b1c1ac77c33c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="gw-optimize-global-data"></a>/Gw（优化全局数据）
在 COMDAT 节中打包全局数据以进行优化。  
  
## <a name="syntax"></a>语法  
  
```  
/Gw[-]  
```  
  
## <a name="remarks"></a>备注  
 **/Gw**选项使在各个 COMDAT 节中打包全局数据编译器。 默认情况下， **/Gw**处于关闭状态，必须显式启用。 若要显式禁用它，请使用**/Gw-**。 当同时**/Gw**和[/GL](../../build/reference/gl-whole-program-optimization.md)被启用，链接器将使用全程序优化来比较多个对象文件的 COMDAT 节，以排除未引用的全局数据或合并相同只读全局数据。 这样可以显著减小生成的二进制可执行文件的大小。  
  
 当你分别编译和链接时，你可以使用[/opt: ref](../../build/reference/opt-optimizations.md)链接器选项以从使用编译对象文件中未引用的全局数据的可执行文件中排除**/Gw**选项。  
  
 你还可以使用[/opt: icf](../../build/reference/opt-optimizations.md)和[/LTCG](../../build/reference/ltcg-link-time-code-generation.md)链接器选项，可以使用的相同只读全局数据跨多个对象文件编译可执行文件中合并**/Gw**选项。  
  
 有关详细信息，请参阅[简介 /Gw 编译器开关](http://blogs.msdn.com/b/vcblog/archive/2013/09/11/introducing-gw-compiler-switch.aspx)Visual c + + 团队博客上。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择**C/c + +**文件夹。  
  
3.  选择**命令行**属性页。  
  
4.  修改**其他选项**属性以包含**/Gw** ，然后选择**确定**。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)