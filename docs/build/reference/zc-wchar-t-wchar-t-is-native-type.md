---
title: "/Zc:wchar_t（wchar_t 是本机类型） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLWCECompilerTool.TreatWChar_tAsBuiltInType"
  - "VC.Project.VCCLCompilerTool.TreatWChar_tAsBuiltInType"
  - "/Zc:wchar_t"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Zc 编译器选项 [C++]"
  - "Conformance 编译器选项"
  - "wchar_t 类型"
  - "Zc 编译器选项 [C++]"
  - "-Zc 编译器选项 [C++]"
ms.assetid: b0de5a84-da72-4e5a-9a4e-541099f939e0
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# /Zc:wchar_t（wchar_t 是本机类型）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

根据 C\+\+ 标准将 `wchar_t` 分析为内置类型。  默认情况下，**\/Zc:wchar\_t** 处于打开状态。  
  
## 语法  
  
```  
/Zc:wchar_t[-]  
```  
  
## 备注  
 如果 **\/Zc:wchar\_t** 处于打开状态，`wchar_t` 将映射到 Microsoft 专用本机类型 `__wchar_t`。  如果指定了 **\/Zc:wchar\_t\-**（带有一个减号），`wchar_t` 将映射到 `unsigned short` 的 `typedef`。  （在 Visual C\+\+ 6.0 和更早版本中，`wchar_t` 未作为内置类型实现，但在 wchar.h 中声明为 `unsigned short` 的 `typedef`。不建议使用 **\/Zc:wchar\_t\-**，因为 C\+\+ 标准要求 `wchar_t` 是内置类型。  使用 `typedef` 版本可能导致可移植性问题。  如果你从 Visual C\+\+ 的早期版本升级并遇到编译器错误 [C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md)（因为代码尝试将 `wchar_t` 隐式转换为 `unsigned short`），则建议更改代码来修正错误，而不是设置 **\/Zc:wchar\_t\-**。  
  
 Microsoft 将 `wchar_t` 作为两位无符号值实现。  有关 `wchar_t` 的详细信息，请参阅 [数据类型范围](../../cpp/data-type-ranges.md) 和 [基本类型](../../cpp/fundamental-types-cpp.md)。  
  
 如果你编写了一个新代码，该代码必须与仍使用 `typedef` 版本的 `wchar_t` 的旧代码互操作，则可为 `wchar_t` 的 `unsigned short` 和 `__wchar_t` 变体提供重载，以便让新代码与使用\/未使用 **\/Zc:wchar\_t** 编译的代码链接。  否则，你必须提供两个不同版本的库（一个启用了 **\/Zc:wchar\_t**，另一个未启用）。  即使在这种情况下，仍建议你使用用来编译新代码的同一编译器来生成旧代码。  不要将使用不同编译器编译的二进制文件混合。  
  
 当指定 **\/Zc:wchar\_t** 时，将定义 **\_WCHAR\_T\_DEFINED** 和 **\_NATIVE\_WCHAR\_T\_DEFINED** 符号。  有关详细信息，请参阅[预定义的宏](../../preprocessor/predefined-macros.md)。  
  
 当你的代码使用编译器 COM 全局函数时，由于默认情况下 **\/Zc:wchar\_t** 处于打开状态，建议你通过[注释杂注](../../preprocessor/comment-c-cpp.md)或命令行将对 comsupp.lib 的显式引用更改为对 comsuppw.lib 或 comsuppwd.lib 的显式引用。  （如果必须使用 **\/Zc:wchar\_t\-** 进行编译，则使用 comsupp.lib。）如果包含了 comdef.h 头文件，则会为你指定正确的库。  有关编译器 COM 支持的详细信息，请参阅[编译器 COM 支持](../../cpp/compiler-com-support.md)。  
  
 编译 C 代码时不支持 `wchar_t` 类型。  有关使用 Visual C\+\+ 时的一致性问题的更多信息，请参见 [非标准行为](../../cpp/nonstandard-behavior.md)。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  在左窗格中，展开**“配置属性”**、**“C\/C\+\+”**，然后选择**“语言”**。  
  
3.  修改**“将 wchar\_t 视为内置类型”**属性。  
  
### 以编程方式设置此编译器选项  
  
-   请参阅<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.TreatWChar_tAsBuiltInType%2A>。  
  
## 请参阅  
 [\/Zc（一致性）](../../build/reference/zc-conformance.md)