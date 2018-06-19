---
title: -homeparams （将寄存器参数复制到堆栈） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /homeparams
dev_langs:
- C++
helpviewer_keywords:
- /homeparams compiler option [C++]
- -homeparams compiler option [C++]
ms.assetid: 51067de4-24f7-436b-b8d9-bc867a7d53aa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ffc9b37ebdcbb380186c7840f5ebd956708a2dc
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374393"
---
# <a name="homeparams-copy-register-parameters-to-stack"></a>/homeparams（将寄存器参数复制到堆栈）
强制将传入寄存器的参数写入其在函数入口的堆栈上的位置。  
  
## <a name="syntax"></a>语法  
  
```  
/homeparams  
```  
  
## <a name="remarks"></a>备注  
 此编译器选项仅适用于 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 编译器（本机编译和跨平台编译）。  
  
 当在传递参数[!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]编译，则调用约定会要求堆栈空间要求的参数，即使对于在寄存器中传递的参数。 有关详细信息，请参阅[参数传递](../../build/parameter-passing.md)。 但是，默认情况下，在发布版本中，将寄存器参数将不将写入到堆栈中的参数已提供的空间。 这使得难以调试的程序优化 （发布） 版本。  
  
 对于发布版本中，使用 **/homeparams**以确保你可以调试你的应用程序。 **/homeparams**未意味着性能降低，因为它的确需要周期以加载到堆栈将寄存器参数。  
  
 在调试版本中，堆栈始终填充在寄存器中传递的参数。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击 **“C/C++”** 文件夹。  
  
3.  点击“命令行”  属性页。  
  
4.  在 **“附加选项”** 框中键入编译器选项。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)