---
title: "-Oi （生成内部函数） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableIntrinsicFunctions
- /oi
- VC.Project.VCCLWCECompilerTool.EnableIntrinsicFunctions
dev_langs: C++
helpviewer_keywords:
- Oi compiler option [C++]
- intrinsic functions, generate
- /Oi compiler option [C++]
- -Oi compiler option [C++]
- generate intrinsic functions compiler option [C++]
ms.assetid: fa4a3bf6-0ed8-481b-91c0-add7636132b4
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a2dbbac624f02b60c35f9840da94d677b13c7f40
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="oi-generate-intrinsic-functions"></a>/Oi（生成内部函数）
替换某些函数调用替换内部函数或其他特殊形式的函数，可帮助你的应用程序的运行速度。  
  
## <a name="syntax"></a>语法  
  
```  
/Oi[-]  
```  
  
## <a name="remarks"></a>备注  
 使用内部函数的程序很速度更快，因为它们没有函数调用的开销，但是由于创建的其他代码可能比较大。  
  
 请参阅[内部](../../preprocessor/intrinsic.md)有关在其函数具有内部形式的详细信息。  
  
 **/Oi**是仅请求到编译器的一些函数调用替换内部函数; 编译器可能调用该函数 （和不的函数调用替换内部函数） 如果它将导致更好的性能。  
  
 **x86 特定**  
  
 内部函数的浮点函数不执行任何特殊检查输入值和因此工作在有限范围内的输入，并具有不同的异常处理和具有相同名称的库例程边界条件。 使用真正的内部形式意味着丢失和丢失的 IEEE 异常处理，`_matherr`和`errno`功能; 后者意味着丢失的 ANSI 一致性。 但是，这些内部形式可以显著加快浮点密集型程序，并且对于很多程序，一致性问题都很少的实际值。  
  
 你可以使用[Za](../../build/reference/za-ze-disable-language-extensions.md)编译器选项来重写真正内部浮点选项的生成。 在此情况下，函数将生成为库例程，后者将自变量直接传递到浮点芯片，而不是将自变量推送到程序堆栈。  
  
 **结束 x86 特定**  
  
 你还使用[内部](../../preprocessor/intrinsic.md)创建内部函数，或[函数 （C/c + +）](../../preprocessor/function-c-cpp.md)来显式强制实现函数调用。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击 **“C/C++”** 文件夹。  
  
3.  单击**优化**属性页。  
  
4.  修改**启用内部函数**属性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableIntrinsicFunctions%2A>。  
  
## <a name="see-also"></a>另请参阅  
 [/O 选项 （优化代码）](../../build/reference/o-options-optimize-code.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [编译器内部函数](../../intrinsics/compiler-intrinsics.md)