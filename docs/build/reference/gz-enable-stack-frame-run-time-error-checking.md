---
title: -GZ (启用堆栈帧运行时错误检查) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /gz
dev_langs:
- C++
helpviewer_keywords:
- -GZ compiler option [C++]
- release-build errors
- /GZ compiler option [C++]
- GZ compiler option [C++]
- debug builds, catch release-build errors
ms.assetid: b3efeeff-d5e3-4057-91c9-f6fc73d0270c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 31224fa3b2809cbc7b7f29868ad4c3e6a89954e0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373548"
---
# <a name="gz-enable-stack-frame-run-time-error-checking"></a>/GZ（启用堆栈帧运行时错误检查）
执行相同的操作[/RTC （运行时错误检查）](../../build/reference/rtc-run-time-error-checks.md)选项。 已否决。  
  
## <a name="syntax"></a>语法  
  
```  
/GZ  
```  
  
## <a name="remarks"></a>备注  
 **/GZ**仅供非优化使用 ([/Od （禁用 （调试））](../../build/reference/od-disable-debug.md)) 生成。  
  
 **/GZ**自 Visual Studio 2005; 起弃用使用[/RTC （运行时错误检查）](../../build/reference/rtc-run-time-error-checks.md)相反。 不推荐使用的编译器选项的列表，请参阅**已弃用并删除的编译器选项**中[按类别列出的编译器选项](../../build/reference/compiler-options-listed-by-category.md)。  
  
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