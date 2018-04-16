---
title: "-FU (命名强制 #using 文件) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.ForcedUsingFiles
- /FU
- VC.Project.VCNMakeTool.ForcedUsingAssemblies
dev_langs:
- C++
helpviewer_keywords:
- -FU compiler option [C++]
- FU compiler option [C++]
- /FU compiler option [C++]
ms.assetid: 698f8603-457f-435a-baff-5ac9243d6ca1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 17b62859aaf0c9dc6b3313fbb726602b5b83a82c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="fu-name-forced-using-file"></a>/FU（命名强制 #using 文件）
你可以使用作为传递的源文件名的替代方法的编译器选项[#using 指令](../../preprocessor/hash-using-directive-cpp.md)源代码中。  
  
## <a name="syntax"></a>语法  
  
```  
/FU file  
```  
  
## <a name="arguments"></a>自变量  
 `file`  
 指定要在此编译中引用的元数据文件。  
  
## <a name="remarks"></a>备注  
 /FU 开关只采用一个文件名。 若要指定多个文件，请对每个文件使用 /FU。  
  
 如果你使用[!INCLUDE[cppcli](../../build/reference/includes/cppcli_md.md)]并引用元数据来使用[友元程序集](../../dotnet/friend-assemblies-cpp.md)功能，不能使用**/FU**。 您必须将 `#using` 与 `[as friend]` 特性一起使用，才能在代码中引用元数据。 [!INCLUDE[cppwrt](../../build/reference/includes/cppwrt_md.md)] ([!INCLUDE[cppwrt_short](../../build/reference/includes/cppwrt_short_md.md)]) 中不支持友元程序集。  
  
 有关如何创建一个程序集或模块为公共语言运行时 (CLR) 的信息，请参阅[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。 有关如何生成[!INCLUDE[cppwrt_short](../../build/reference/includes/cppwrt_short_md.md)]，请参阅[生成应用程序和库](../../cppcx/building-apps-and-libraries-c-cx.md)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择**C/c + +**文件夹。  
  
3.  选择**高级**属性页。  
  
4.  修改**强制 #using**属性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForcedUsingFiles%2A>。  
  
## <a name="see-also"></a>请参阅  
 [输出文件 (/ F) 选项](../../build/reference/output-file-f-options.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)