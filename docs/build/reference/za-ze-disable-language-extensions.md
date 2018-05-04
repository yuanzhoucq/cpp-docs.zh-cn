---
title: -Za，-Ze （禁用语言扩展） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.DisableLanguageExtensions
- /za
- /ze
- VC.Project.VCCLCompilerTool.DisableLanguageExtensions
dev_langs:
- C++
helpviewer_keywords:
- -Za compiler option [C++]
- Za compiler option [C++]
- language extensions, disabling in compiler
- -Ze compiler option [C++]
- language extensions
- enable language extensions
- /Za compiler option [C++]
- /Ze compiler option [C++]
- Disable Language Extensions compiler option
- Ze compiler option [C++]
ms.assetid: 65e49258-7161-4289-a176-7c5c0656b1a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2949a3d60af6d9058f02d12aac1fd86dead5affa
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="za-ze-disable-language-extensions"></a>/Za、/Ze（禁用语言扩展）
**/Za**编译器选项将发出错误对与 ANSI C89 或 ISO C + + 11 不兼容的语言构造。 **/Ze**编译器选项，这将在上，默认情况下，将启用 Microsoft 扩展。  
  
## <a name="syntax"></a>语法  
  
```  
/Za  
/Ze  
```  
  
## <a name="remarks"></a>备注  
  
> [!NOTE]
>  **/Ze**选项已弃用，因为其行为是在默认情况下。 我们建议你使用[/Zc （一致性）](../../build/reference/zc-conformance.md)编译器选项来控制特定的语言扩展功能。 不推荐使用的编译器选项的列表，请参阅**已弃用并删除的编译器选项**主题中[按类别列出的编译器选项](../../build/reference/compiler-options-listed-by-category.md)。  
  
 [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]编译器提供了大量的 ANSI C89、 ISO C99 或 ISO c + + 标准中指定的之外的功能。 这些功能统称为 Microsoft 扩展到 C 和 c + +。 这些扩展时，将按默认情况下，提供的并且不可用 **/Za**指定选项。 有关特定扩展的详细信息，请参阅[Microsoft C 和 c + + 扩展](../../build/reference/microsoft-extensions-to-c-and-cpp.md)。  
  
 我们建议你禁用语言扩展，通过指定 **/Za**选项如果你打算将程序移植到其他环境。 当 **/Za**指定，编译器将 Microsoft 扩展关键字作为简单标识符，禁用的其他 Microsoft 扩展，并自动定义`__STDC__`C 程序的预定义的宏。  
  
 与使用其他编译器选项 **/Za**可能会影响编译器确保标准一致性的方式。 例如， **/Za**和[/fp （指定浮点行为）](../../build/reference/fp-specify-floating-point-behavior.md)可能导致不符合的浮点类型提升行为 ISO C99 或 C + + 11 标准。  
  
 有关指定特定的标准符合的行为设置方法，请参阅[/Zc](../../build/reference/zc-conformance.md)编译器选项。  
  
 有关一致性问题的详细信息[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]，请参阅[非标准行为](../../cpp/nonstandard-behavior.md)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  在导航窗格中，选择**配置属性**， **C/c + +**，**语言**。  
  
3.  修改**禁用语言扩展**属性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableLanguageExtensions%2A>。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [/Zc（一致性）](../../build/reference/zc-conformance.md)