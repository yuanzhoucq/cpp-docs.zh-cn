---
title: -GR （启用运行时类型信息） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /gr
- VC.Project.VCCLWCECompilerTool.RuntimeTypeInfo
- VC.Project.VCCLCompilerTool.RuntimeTypeInfo
dev_langs:
- C++
helpviewer_keywords:
- -Gr compiler option [C++]
- Gr compiler option [C++]
- RTTI compiler option
- /Gr compiler option [C++]
- enable run-time type information compiler option [C++]
ms.assetid: d1f9f850-dcec-49fd-96ef-e72d01148906
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 79e91f11fa6397d2ba8279998726249182c541d4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374969"
---
# <a name="gr-enable-run-time-type-information"></a>/GR（启用运行时类型信息）
添加代码以在运行时检查对象类型。  
  
## <a name="syntax"></a>语法  
  
```  
/GR[-]  
```  
  
## <a name="remarks"></a>备注  
 当 **/GR**处于打开状态，编译器会定义`_CPPRTTI`预处理器宏。 默认情况下， **/GR**上。 **/GR-** 禁用运行时类型信息。  
  
 使用 **/GR**如果编译器无法以静态方式解决代码中的对象类型。 你通常需要 **/GR**选项时你的代码使用[dynamic_cast 运算符](../../cpp/dynamic-cast-operator.md)或[typeid](../../cpp/typeid-operator.md)。 但是， **/GR**会增加你的映像的.rdata 部分的大小。 如果你的代码不使用**dynamic_cast**或**typeid**， **/GR-** 可能会产生较小的图像。  
  
 有关运行时类型检查的详细信息，请参阅[运行时类型信息](../../cpp/run-time-type-information.md)中*c + + 语言参考*。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击 **“C/C++”** 文件夹。  
  
3.  单击**语言**属性页。  
  
4.  修改**启用运行时类型信息**属性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.RuntimeTypeInfo%2A>。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)