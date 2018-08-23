---
title: -QIfist （取消 _ftol） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /qifist
dev_langs:
- C++
helpviewer_keywords:
- QIfist compiler option [C++]
- -QIfist compiler option [C++]
- /QIfist compiler option [C++]
ms.assetid: 1afd32a5-f658-4b66-85f4-e0ce4cb955bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b693f78b6fbd9a11dbe98ec2eacc3d781ffd7ebf
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2018
ms.locfileid: "42572812"
---
# <a name="qifist-suppress-ftol"></a>/QIfist（取消 _ftol）
已否决。 当需要从浮点型转换为整型时，取消调用 Helper 函数 `_ftol` 。  
  
## <a name="syntax"></a>语法  
  
```  
/QIfist  
```  
  
## <a name="remarks"></a>备注  
  
> [!NOTE]
>  **/Qifist**选项仅适用于编译器面向 x86; 此编译器选项不是在面向 x64 编译器中可用 orARM。  
  
 从浮点类型转换为整型类型，除了`_ftol`函数确保浮点单元 (FPU) 的舍入模式为向零方向 （截断），通过设置的控制字位 10 和 11 位。 这可确保从浮点类型转换为整型类型发生所描述的 ANSI C 标准 （数字的小数部分将被丢弃）。 使用时 **/QIfist**，这一保证不再适用。 舍入模式将一个四个 Intel 参考手册中所述：  
  
-   舍入为最接近 （如果等距为偶数）  
  
-   向负无穷方向舍入  
  
-   向正无穷大方向舍入  
  
-   向零舍入  
  
 可以使用[_control87、 _controlfp， \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md) C 运行时函数来修改 FPU 的舍入行为。 舍入模式 FPU 默认值为"舍入为最接近。" 使用 **/QIfist**可以提高性能的应用程序，但并不是没有风险。 您应该全面测试你的代码对之前使用依赖于代码生成舍入模式不敏感的部分 **/QIfist**在生产环境中。  
  
 [/arch (x86)](../../build/reference/arch-x86.md)并 **/QIfist**不能使用同一编译。  
  
> [!NOTE]
>  **/Qifist**是不有效默认情况下由于舍入位数也会影响浮点到浮动点舍入 （这发生在每次计算后），因此，当设置为 C 样式 （接近零） 舍入的标志，浮点计算可能会不同。 **/Qifist**不应在你的代码依赖于截断的浮点数的小数部分的预期行为。 如果您不确定，请不要使用 **/QIfist**。  
  
 **/QIfist**选项已弃用 Visual Studio 2005 中启动。 编译器对进行了重大改进在 float int 转换速度。 有关不推荐使用的编译器选项的列表，请参阅**已弃用并删除的编译器选项**中[按类别列出的编译器选项](../../build/reference/compiler-options-listed-by-category.md)。  
  
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