---
title: -体系结构 (ARM) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 4f1406ff-f174-487c-a126-8ab06cf447c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2a411d0c7d07fb7392baaaa4fb8a8377fcb36598
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32369859"
---
# <a name="arch-arm"></a>/arch (ARM)
为 ARM 上的代码生成指定体系结构。 另请参阅[/arch (x86)](../../build/reference/arch-x86.md)和[/arch (x64)](../../build/reference/arch-x64.md)。  
  
## <a name="syntax"></a>语法  
  
```  
/arch:[ARMv7VE|VFPv4]  
```  
  
## <a name="arguments"></a>自变量  
 **/arch: armv7ve**  
 允许使用 ARMv7VE 虚拟化扩展指令。  
  
 **/arch: vfpv4**  
 允许使用 ARM VFPv4 指令。 如果未指定此选项，则默认为 VFPv3。  
  
## <a name="remarks"></a>备注  
 `_M_ARM_FP`宏 （仅用于 ARM) 指示的 (如果有） **/arch**编译器选项已使用。 有关更多信息，请参见 [Predefined Macros](../../preprocessor/predefined-macros.md)。  
  
 当你使用[/clr](../../build/reference/clr-common-language-runtime-compilation.md)进行编译时， **/arch**对托管的函数的代码生成没有影响。 **/arch**仅影响本机函数生成的代码。  
  
### <a name="to-set-the-archarmv7ve-or-archvfpv4-compiler-option-in-visual-studio"></a>在 Visual Studio 中设置 /arch:ARMv7VE 或 /arch:VFPv4 编译器选项  
  
1.  打开**属性页**项目对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择**C/c + +** 文件夹。  
  
3.  选择**命令行**属性页。  
  
4.  在**其他选项**框中，添加`/arch:ARMv7VE`或`/arch:VFPv4`。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>。  
  
## <a name="see-also"></a>请参阅  
 [/arch （最小 CPU 体系结构）](../../build/reference/arch-minimum-cpu-architecture.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)