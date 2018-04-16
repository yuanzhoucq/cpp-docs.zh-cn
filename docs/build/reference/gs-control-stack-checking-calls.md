---
title: "-Gs （控制堆栈检查调用） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /GS
dev_langs:
- C++
helpviewer_keywords:
- disabling stack probes
- GS compiler option [C++]
- /GS compiler option [C++]
- stack, stack probes
- stack probes
- -GS compiler option [C++]
- stack checking calls
ms.assetid: 40daed7c-f942-4085-b872-01e12b37729e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ff02465b4e1b1a727a2367c8d5e038f30854ecc6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="gs-control-stack-checking-calls"></a>/Gs（控制堆栈检查调用）
控制堆栈探测。  
  
## <a name="syntax"></a>语法  
  
```  
/Gs[size]  
```  
  
## <a name="arguments"></a>自变量  
 `size`  
 （可选）在启动堆栈探测之前局部变量可以占用的字节数。 如果**/Gs**选项而未指定`size`自变量，它是与指定相同**/Gs0**，  
  
## <a name="remarks"></a>备注  
 堆栈探测是编译器插入到每个函数调用中的代码序列。 堆栈探测启动时，它在内存中良性延伸存储函数的局部变量所需的空间量。  
  
 如果函数的局部变量需要的堆栈空间多于 `size` 字节，则启动它的堆栈探测。 默认情况下，当函数需要的堆栈空间多于一页时，编译器将生成启动堆栈探测的代码。 这相当于一个编译器选项： **/Gs4096**适用于 x86、 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]，和 ARM 平台。 此值使应用程序和 Windows 内存管理器可以动态增加运行时提交给程序堆栈的内存量。  
  
> [!NOTE]
>  默认值**/Gs4096**允许在运行时适当增长的 Windows 应用程序的程序堆栈。 我们建议，除非有确切的理由，否则请不要更改默认值。  
  
 某些程序（如虚拟设备驱动程序）并不需要这种默认堆栈增长机制。 在这些情况下，不需要堆栈探测，通过将 `size` 设置为大于任何函数（将需要局部变量存储）的值，可阻止编译器生成堆栈探测。 不允许有空格之间**/Gs**和`size`。  
  
 **/ Gs0**激活需要存储的本地变量的每个函数调用的堆栈探测。 这可对性能产生负面影响。  
  
 你可以通过使用启用堆栈探测打开或关闭[check_stack](../../preprocessor/check-stack.md)。 **/Gs**和`check_stack`杂注对标准 C 库例程没有影响; 它们影响仅你编译的函数。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择**C/c + +**文件夹。  
  
3.  选择**命令行**属性页。  
  
4.  在 **“附加选项”** 框中键入编译器选项。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)