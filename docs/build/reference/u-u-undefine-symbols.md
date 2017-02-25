---
title: "/U、/u（未定义符号） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.UndefinePreprocessorDefinitions"
  - "VC.Project.VCCLWCECompilerTool.UndefinePreprocessorDefinitions"
  - "VC.Project.VCCLCompilerTool.UndefineAllPreprocessorDefinitions"
  - "/u"
  - "VC.Project.VCCLWCECompilerTool.UndefineAllPreprocessorDefinitions"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/U 编译器选项 [C++]"
  - "U 编译器选项 [C++]"
  - "-U 编译器选项 [C++]"
  - "“取消定义符号”编译器选项"
ms.assetid: 7bc0474f-6d1f-419b-807d-0d8816763b2a
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# /U、/u（未定义符号）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**\/U** 编译器选项可取消定义指定的预处理器符号。  **\/u** 编译器选项可取消定义编译器定义的特定于 Microsoft 的符号。  
  
## 语法  
  
```  
/U[ ]symbol  
/u  
```  
  
## Arguments  
 `symbol`  
 要取消定义的预处理器符号。  
  
## 备注  
 **\/U** 和 **\/u** 选项都无法取消定义用 **\#define** 指令创建的符号。  
  
 **\/U** 选项可以取消定义以前用 **\/D** 选项定义的符号。  
  
 默认情况下，编译器可定义以下特定于 Microsoft 的符号。  
  
|符号|功能|  
|--------|--------|  
|\_CHAR\_UNSIGNED|默认 char 类型为 unsigned。  在指定 [\/J](../../build/reference/j-default-char-type-is-unsigned.md) 选项时定义。|  
|\_CPPRTTI|为用 [\/GR](../../build/reference/gr-enable-run-time-type-information.md) 选项编译的代码定义。|  
|\_CPPUNWIND|为用 [\/EHsc](../../build/reference/eh-exception-handling-model.md) 选项编译的代码定义。|  
|\_DLL|在指定 [\/MD](../../build/reference/md-mt-ld-use-run-time-library.md) 选项时定义。|  
|\_M\_IX86|默认情况下，为 x86 目标定义为 600。|  
|\_MSC\_VER|有关详细信息，请参阅[预定义的宏](../../preprocessor/predefined-macros.md)。|  
|\_WIN32|为 WIN32 应用程序定义。  始终定义。|  
|\_MT|在指定 [\/MD 或 \/MT](../../build/reference/md-mt-ld-use-run-time-library.md) 选项时定义。|  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“高级”**属性页。  
  
4.  修改**“取消定义预处理器”**或**“取消定义所有预处理器”**属性。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefineAllPreprocessorDefinitions%2A>或 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefinePreprocessorDefinitions%2A>。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [\/J（默认 char 类型是无符号的）](../../build/reference/j-default-char-type-is-unsigned.md)   
 [\/GR（启用运行时类型信息）](../../build/reference/gr-enable-run-time-type-information.md)   
 [\/EH（异常处理模型）](../../build/reference/eh-exception-handling-model.md)   
 [\/MD、\/MT、\/LD（使用运行库）](../../build/reference/md-mt-ld-use-run-time-library.md)