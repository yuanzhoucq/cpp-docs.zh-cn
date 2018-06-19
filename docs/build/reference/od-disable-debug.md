---
title: -Od （禁用 （调试）） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /od
dev_langs:
- C++
helpviewer_keywords:
- no optimizations
- fast compiling
- /Od compiler option [C++]
- disable optimizations
- Od compiler option [C++]
- -Od compiler option [C++]
- disable (debug) compiler option [C++]
ms.assetid: b1ac31b7-e086-4eeb-be5e-488f7513f5f5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47e287a9991f8192f16ec2f93e4068dc797ff72a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376255"
---
# <a name="od-disable-debug"></a>/Od（禁用（调试））
关闭程序中的所有优化并加快编译。  
  
## <a name="syntax"></a>语法  
  
```  
/Od  
```  
  
## <a name="remarks"></a>备注  
 默认值为此选项。 因为 **/Od**取消代码移动，它简化了在调试过程。 有关调试的编译器选项的详细信息，请参阅[/Z7、 /Zi、 /ZI （调试信息格式）](../../build/reference/z7-zi-zi-debug-information-format.md)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击 **“C/C++”** 文件夹。  
  
3.  单击**优化**属性页。  
  
4.  修改**优化**属性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>。  
  
## <a name="see-also"></a>请参阅  
 [/O 选项 （优化代码）](../../build/reference/o-options-optimize-code.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [/Z7、/Zi、/ZI（调试信息格式）](../../build/reference/z7-zi-zi-debug-information-format.md)