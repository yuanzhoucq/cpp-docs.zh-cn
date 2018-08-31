---
title: -guard （启用控制流保护） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /guard
- VC.Project.VCCLCompilerTool.ControlFlowGuard
dev_langs:
- C++
ms.assetid: be495323-f59f-4cf3-a6b6-8ee69e6a19dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6c65bafc14f5ef29db89ddc0a4647193231f7e19
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2018
ms.locfileid: "43131665"
---
# <a name="guard-enable-control-flow-guard"></a>/guard（启用控制流保护）
允许编译器生成控制流保护安全性检查。  
  
## <a name="syntax"></a>语法  
  
```  
/guard:cf[-]  
```  
  
## <a name="remarks"></a>备注  
 **/guard:cf** 选项使编译器在编译时为间接调用目标分析控制流，然后插入代码以在运行时验证目标。 默认情况下， **/guard:cf** 处于关闭状态，必须显式启用它。 若要显式禁用此选项，请使用 **/guard:cf-**。 

**Visual Studio 2017 和更高版本**： 此选项将添加为临界**切换**生成的语句跳转表。
  
 当指定 **/guard:cf** 控制流监护 (CFG) 选项时，编译器和链接器会插入额外的运行时安全性检查，以检测会危及你的代码的尝试。 在编译和链接期间，将分析代码中的所有间接调用以查找当代码正确时它能够到达的每个位置。 此信息存储在你二进制文件标头的额外结构中。 编译器还会在代码中的每个间接调用之前插入检查，以确保目标是已验证过的位置之一。 如果运行时 CFG 感知的操作系统上检查失败，操作系统将关闭该程序。  
  
 常见的软件攻击充分利用的是处理极端或意外输入中的 Bug。 构思巧妙应用程序输入可能会覆盖包含指向可执行代码的指针的位置。 这可用来将控制流重定向到由攻击者控制的代码。 CFG 运行时检查不会修复你可执行文件中的数据损坏 Bug。 而是使攻击者难以利用它们来执行任意代码。 CFG 是一种缓解工具，用于防止对你代码中函数入口点以外的位置进行调用。 它类似于数据执行保护 (DEP)、  [/GS](../../build/reference/gs-buffer-security-check.md) 堆栈检查以及 [/DYNAMICBASE](../../build/reference/dynamicbase-use-address-space-layout-randomization.md) 和 [/HIGHENTROPYVA](../../build/reference/highentropyva-support-64-bit-aslr.md) 地址空间布局随机化 (ASLR) 如何降低你的代码成为攻击向量的可能性。  
  
 必须将 **/guard:cf** 选项传递给编译器和链接器以生成使用 CFG 利用缓解技术的代码。 如果你的二进制文件是使用单个 `cl` 命令生成的，则编译器会将该选项传递到链接器。 如果你分别编译和链接，则必须同时在编译器和链接器命令上设置该选项。 /DYNAMICBASE 链接器选项也是必需的。 若要验证你的二进制文件具有 CFG 数据，请使用 `dumpbin /headers /loadconfig` 命令。 支持 CFG 的二进制文件在 EXE 或 DLL 的特征列表中具有 `Guard` ，并且 Guard 标志包括 `CF Instrumented` 和 `FID table present`。  
  
 **/guard:cf** 选项与 [/ZI](../../build/reference/z7-zi-zi-debug-information-format.md) （编辑并继续调试信息）或 [/clr](../../build/reference/clr-common-language-runtime-compilation.md) （公共语言运行时编译）不兼容。  
  
 使用 **/guard:cf** 编译的代码可以链接到不是使用该选项编译的库和对象文件。 当还通过使用 **/guard:cf** 选项链接以及在 CFG 感知的操作系统上运行时，仅此代码具有 CFG 保护。 由于不使用此选项编译的代码不会停止攻击，因此我们建议你将此选项用于你编译的所有代码上。 有用于 CFG 检查的较小的运行时成本，但编译器分析会尝试优化去除可证明是安全的间接跳转上的检查。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  依次选择 **“配置属性”**、 **“C/C++”** 和 **“代码生成”**。  
  
3.  选择 **“控制流保护”** 属性。  
  
4.  在下拉控件中，选择 **“是”** 以启用控制流保护，或选择 **“否”** 加以禁用。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)