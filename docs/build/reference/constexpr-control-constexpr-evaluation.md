---
title: -constexpr （控制 constexpr 计算） |Microsoft Docs
ms.custom: ''
ms.date: 08/15/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /constexpr
- -constexpr
dev_langs:
- C++
helpviewer_keywords:
- /constexpr control constexpr evaluation [C++]
- -constexpr control constexpr evaluation [C++]
- constexpr control constexpr evaluation [C++]
ms.assetid: 76d56784-f5ad-401d-841d-09d1059e8b8c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 475702792686a3de8d1ae52bd9e40ef113c49da1
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43202569"
---
# <a name="constexpr-control-constexpr-evaluation"></a>/constexpr （控制 constexpr 计算）  
  
使用 **/constexpr**编译器选项的控件的参数**constexpr**在编译时计算。  
  
## <a name="syntax"></a>语法  
  
> **/constexpr:**<em>N</em>  
> **/constexpr:**<em>N</em>  
> **/constexpr:**<em>N</em>  
  
## <a name="arguments"></a>自变量  
  
**深度**<em>N</em>  
限制的递归深度**constexpr**函数调用到*N*级别。 默认值为 512。  
  
**回溯**<em>N</em>  
显示最多*N* **constexpr**诊断中的评估。 默认值为 10。  
  
**步骤**<em>N</em>  
终止**constexpr**评估后的*N*步骤。 默认值为 100,000。  
  
## <a name="remarks"></a>备注  
  
**/Constexpr**编译器选项可控制的编译时计算**constexpr**表达式。 评估步骤、 递归级别和反向跟踪深度控制以阻止编译器上花费太多时间**constexpr**评估。 有关详细信息**constexpr**语言元素，请参阅[constexpr （c + +）](../../cpp/constexpr-cpp.md)。  

**/Constexpr**选项是在 Visual Studio 2015 开始提供。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1. 打开你的项目**属性页**对话框。   
  
2. 下**配置属性**，展开**C/c + +** 文件夹，然后选择**命令行**属性页。  
  
3. 输入任何 **/constexpr**编译器选项，在**其他选项**框。 选择**确定**或**应用**以保存所做的更改。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>请参阅  
  
[编译器选项](../../build/reference/compiler-options.md)   
[设置编译器选项](../../build/reference/setting-compiler-options.md)