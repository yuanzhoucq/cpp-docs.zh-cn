---
title: "-QIfist （取消 _ftol） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /qifist
dev_langs: C++
helpviewer_keywords:
- QIfist compiler option [C++]
- -QIfist compiler option [C++]
- /QIfist compiler option [C++]
ms.assetid: 1afd32a5-f658-4b66-85f4-e0ce4cb955bd
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7377824b45027318a21f464650ecbc837a76d31c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="qifist-suppress-ftol"></a>/QIfist（取消 _ftol）
已否决。 当需要从浮点型转换为整型时，取消调用 Helper 函数 `_ftol` 。  
  
## <a name="syntax"></a>语法  
  
```  
/QIfist  
```  
  
## <a name="remarks"></a>备注  
  
> [!NOTE]
>  **/Qifist**选项仅适用于编译器面向 x86; 此编译器选项不可用面向的编译器中[!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]orARM。  
  
 除了从浮点类型转换为整数类型、`_ftol`函数会确保浮点单元 (FPU) 的舍入模式是向零方向 （截断），通过设置控制字的 10 和 11 位。 这可保证： 从浮点类型转换为整数类型发生 （数的小数部分将被丢弃） 与 ANSI C 标准所述。 使用时**/QIfist**，此保证不再适用。 如 Intel 参考手册中所述，舍入模式将为四个之一：  
  
-   舍入为最接近 （如果等距的偶数）  
  
-   向负无穷方向舍入  
  
-   向正无穷方向舍入  
  
-   向零方向舍入  
  
 你可以使用[_control87、 _controlfp、 \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md) C 运行时函数来修改 FPU 的舍入行为。 舍入模式 FPU 默认值为"舍入为最接近的。" 使用**/QIfist**可以改善性能的应用程序，但并不是没有风险。 您应该全面测试你的代码的部分，舍入模式，与依赖代码生成之前对敏感**/QIfist**在生产环境中。  
  
 [/arch (x86)](../../build/reference/arch-x86.md)和**/QIfist**不能使用同一编译。  
  
> [!NOTE]
>  **/Qifist**是不实际上由默认因为舍入位数也会影响到浮点浮点点舍入 （时会出现此情况在每次计算后），因此，当你设置 （向零方向） 的 C 样式舍入的标志时，浮点计算可能会不同。 **/Qifist**如果截断的浮点数的小数部分的预期行为取决于你的代码不应使用。 如果您不确定，不要使用**/QIfist**。  
  
 **/QIfist**选项已弃用启动 Visual Studio 2005 中。 编译器具有极大地提高了 float int 转换速度。 不推荐使用的编译器选项的列表，请参阅**已弃用并删除的编译器选项**中[按类别列出的编译器选项](../../build/reference/compiler-options-listed-by-category.md)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击 **“C/C++”** 文件夹。  
  
3.  点击“命令行”  属性页。  
  
4.  在 **“附加选项”** 框中键入编译器选项。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>请参阅  
 [/Q 选项 （低级别操作）](../../build/reference/q-options-low-level-operations.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)