---
title: "/GR（启用运行时类型信息） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/gr"
  - "VC.Project.VCCLWCECompilerTool.RuntimeTypeInfo"
  - "VC.Project.VCCLCompilerTool.RuntimeTypeInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Gr 编译器选项 [C++]"
  - "启用运行时类型信息编译器选项 [C++]"
  - "Gr 编译器选项 [C++]"
  - "-Gr 编译器选项 [C++]"
  - "RTTI 编译器选项"
ms.assetid: d1f9f850-dcec-49fd-96ef-e72d01148906
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# /GR（启用运行时类型信息）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

添加代码以在运行时检查对象类型。  
  
## 语法  
  
```  
/GR[-]  
```  
  
## 备注  
 当 **\/GR** 启用时，编译器将定义 `_CPPRTTI` 预处理器宏。  默认情况下，**\/GR** 处于打开状态。  **\/GR\-** 将禁用运行时类型信息。  
  
 如果编译器无法在代码中静态解析对象类型，则使用 **\/GR**。  当代码使用 [dynamic\_cast 运算符](../../cpp/dynamic-cast-operator.md) 或 [typeid](../../cpp/typeid-operator.md) 时，通常需要 **\/GR** 选项。  但是，**\/GR** 会导致映像的 .rdata 节增大。  如果您的代码不使用 **dynamic\_cast** 或 **typeid**，则使用 **\/GR\-** 可能会生成较小的映像。  
  
 有关运行时类型检查的更多信息，请参见“C\+\+ 语言参考”中的[运行时类型信息](../../cpp/run-time-type-information.md)。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“语言”**属性页。  
  
4.  修改**“启用运行时类型信息”**属性。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.RuntimeTypeInfo%2A>。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)