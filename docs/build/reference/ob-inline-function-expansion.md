---
title: "/Ob（内联函数展开） | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLWCECompilerTool.InlineFunctionExpansion"
  - "VC.Project.VCCLCompilerTool.InlineFunctionExpansion"
  - "/ob"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Ob 编译器选项 [C++]"
  - "/Ob0 编译器选项 [C++]"
  - "/Ob1 编译器选项 [C++]"
  - "/Ob2 编译器选项 [C++]"
  - "任何适用项编译器选项 [C++]"
  - "禁用编译器选项 [C++]"
  - "内联展开, 编译器选项"
  - "内联函数, 函数展开编译器选项 [C++]"
  - "Ob 编译器选项 [C++]"
  - "-Ob 编译器选项 [C++]"
  - "Ob0 编译器选项 [C++]"
  - "-Ob0 编译器选项 [C++]"
  - "Ob1 编译器选项 [C++]"
  - "-Ob1 编译器选项 [C++]"
  - "Ob2 编译器选项 [C++]"
  - "-Ob2 编译器选项 [C++]"
  - "only __inline 编译器选项 [C++]"
ms.assetid: f134e6df-e939-4980-a01d-47425dbc562a
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Ob（内联函数展开）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

控制函数的内联扩展。  
  
## 语法  
  
```  
/Ob{0|1|2}  
```  
  
## 参数  
 **0**  
 禁用内联扩展。  默认情况下，扩展由编译器自行对所有函数进行（通常称为*自动内联*）。  
  
 **1**  
 仅允许对标记为 [inline](../../misc/inline-inline-forceinline.md)、[\_\_inline](../../misc/inline-inline-forceinline.md) 或 [\_\_forceinline](../../misc/inline-inline-forceinline.md) 的函数或是在类声明中定义的 C\+\+ 成员函数中进行扩展。  
  
 **2**  
 默认值。  允许对标记为 `inline`、`__inline` 或 `__forceinline` 的函数或是编译器选择的任何其他函数进行扩展。  
  
 **\/Ob2** 会在使用 [\/O1、\/O2（最小化大小、最大化速度）](../../build/reference/o1-o2-minimize-size-maximize-speed.md) 或 [\/Ox（完全优化）](../../build/reference/ox-full-optimization.md) 时生效。  
  
 此选项要求启用使用 **\/O1**、**\/O2**、**\/Ox** 或 **\/Og** 进行的优化。  
  
## 备注  
 编译器将内联扩展选项和关键字视为建议。  并不保证任何函数都会进行内联扩展。  可以禁用内联扩展，但即使在使用 `__forceinline` 关键字时，也无法强制编译器对特定函数进行内联。  
  
 可以使用 `#pragma` [auto\_inline](../../preprocessor/auto-inline.md) 指令将函数从内联扩展的候选者中排除。  另请参阅 `#pragma` [内部](../../preprocessor/intrinsic.md) 指令。  
  
> [!NOTE]
>  如果指定 **\/Ob**、**\/Os** 或 **\/Ot**，则通过分析测试运行收集的信息会重写本应生效的优化。  有关详细信息，请参阅[按配置文件优化](../../build/reference/profile-guided-optimizations.md)。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  依次展开**“配置属性”**、**“C\/C\+\+”**，然后选择**“优化”**。  
  
3.  修改**“内联函数扩展”**属性。  
  
### 以编程方式设置此编译器选项  
  
-   请参阅<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.InlineFunctionExpansion%2A>。  
  
## 请参阅  
 [\/O 选项（优化代码）](../../build/reference/o-options-optimize-code.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)