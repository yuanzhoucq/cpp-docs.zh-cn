---
title: "-Zc: wchar_t （wchar_t 是本机类型） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLWCECompilerTool.TreatWChar_tAsBuiltInType
- VC.Project.VCCLCompilerTool.TreatWChar_tAsBuiltInType
- /Zc:wchar_t
dev_langs: C++
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- wchar_t type
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: b0de5a84-da72-4e5a-9a4e-541099f939e0
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3375e39120fdc8f2b0d8d5502aa6def997511ff5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="zcwchart-wchart-is-native-type"></a>/Zc:wchar_t（wchar_t 是本机类型）
根据 C++ 标准将 `wchar_t` 分析为内置类型。 默认情况下， **/zc: wchar_t**上。  
  
## <a name="syntax"></a>语法  
  
```  
/Zc:wchar_t[-]  
```  
  
## <a name="remarks"></a>备注  
 如果**/zc: wchar_t**处于打开状态，`wchar_t`映射到的 Microsoft 专用本机类型`__wchar_t`。 如果**/Zc:wchar_t-** （带有一个减号） 指定，则`wchar_t`映射到`typedef`为`unsigned short`。 （在 Visual C++ 6.0 和更早版本中，`wchar_t` 未作为内置类型实现，但在 wchar.h 中声明为 `typedef` 的 `unsigned short`。我们不建议**/Zc:wchar_t-**因为 c + + 标准要求`wchar_t`是内置类型。 使用 `typedef` 版本可能导致可移植性问题。 如果你从 Visual c + + 的早期版本升级并遇到编译器错误[C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md)因为代码尝试将隐式转换`wchar_t`到`unsigned short`，我们建议你更改代码以改为修复此错误，设置的**/Zc:wchar_t-**。  
  
 Microsoft 将 `wchar_t` 作为两位无符号值实现。 有关详细信息`wchar_t`，请参阅[数据类型范围](../../cpp/data-type-ranges.md)和[基本类型](../../cpp/fundamental-types-cpp.md)。  
  
 如果你编写新代码具有与较旧仍将使用的代码进行互操作`typedef`版本`wchar_t`，你可以同时提供重载`unsigned short`和`__wchar_t`变体`wchar_t`，以便可以与链接你的代码使用代码编译**/zc: wchar_t**或如果没有该编译的代码。 否则，你必须提供两个不同版本的库-一个使用，另一个未**/zc: wchar_t**启用。 即使在这种情况下，仍建议你使用用来编译新代码的同一编译器来生成旧代码。 不要将使用不同编译器编译的二进制文件混合。  
  
 当**/zc: wchar_t**指定，则**_WCHAR_T_DEFINED**和**_NATIVE_WCHAR_T_DEFINED**定义了符号。 有关更多信息，请参见 [Predefined Macros](../../preprocessor/predefined-macros.md)。  
  
 如果你的代码使用编译器 COM 全局函数，因为**/zc: wchar_t**现在在默认情况下，我们建议你更改对 comsupp.lib 的显式引用[注释杂注](../../preprocessor/comment-c-cpp.md)或命令行-为对 comsuppw.lib 或 comsuppwd.lib。 (如果必须使用编译**/Zc:wchar_t-**，使用 comsupp.lib。)如果你包含了 comdef.h 头文件，则会为你指定正确的库。 有关编译器 COM 支持的信息，请参阅[编译器 COM 支持](../../cpp/compiler-com-support.md)。  
  
 编译 C 代码时不支持 `wchar_t` 类型。 有关使用 Visual c + + 一致性问题的详细信息，请参阅[非标准行为](../../cpp/nonstandard-behavior.md)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  在左窗格中，展开**配置属性**， **C/c + +**，然后选择**语言**。  
  
3.  修改**wchar_t 视为内置类型**属性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.TreatWChar_tAsBuiltInType%2A>。  
  
## <a name="see-also"></a>请参阅  
 [/Zc （一致性）](../../build/reference/zc-conformance.md)