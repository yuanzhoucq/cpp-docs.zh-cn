---
title: "/Wp64（检测 64 位可迁移性问题） | Microsoft Docs"
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
  - "VC.Project.VCCLWCECompilerTool.Detect64BitPortabilityProblems"
  - "VC.Project.VCCLCompilerTool.Detect64BitPortabilityProblems"
  - "/wp64"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Wp64 编译器选项 [C++]"
  - "64 位编译器 [C++], 检测可迁移性问题"
  - "Wp64 编译器选项 [C++]"
  - "-Wp64 编译器选项 [C++]"
ms.assetid: 331ae5aa-e627-4d03-8f63-dd2c2d76dadd
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Wp64（检测 64 位可迁移性问题）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此编译器选项已过时。 在 Visual Studio 2013 之前的 Visual Studio 版本中，此选项可检测类型的 64 位可移植性问题，这些问题也用 [\_\_w64](../../cpp/w64.md) 关键字标记。  
  
## 语法  
  
```  
/Wp64  
```  
  
## 备注  
 默认情况下，在 Visual Studio 2013 之前的 Visual Studio 版本中，**\/Wp64** 编译器选项在 Visual C\+\+ 32 位编译器中处于关闭状态，在 Visual C\+\+ 64 位编译器中处于打开状态。  
  
> [!IMPORTANT]
>  [\/Wp64](../../build/reference/wp64-detect-64-bit-portability-issues.md) 编译器选项和 [\_\_w64](../../cpp/w64.md) 关键字在 Visual Studio 2010 和 Visual Studio 2012 中已弃用，从 Visual Studio 2013 开始不受支持。 如果转换使用此开关的项目，在转换过程中不会迁移该开关。 若要在 Visual Studio 2010 或 Visual Studio 2012 中使用此选项，则必须在项目属性**“命令行”**部分中的**“其他选项”**下输入编译器开关。 如果在命令行中使用 **\/Wp64** 编译器选项，编译器将发出命令行警告 D9002。 不要使用此选项和关键字来检测 64 位可移植性问题，而应使用面向 64 位平台的 Visual C\+\+ 编译器并指定 [\/W4](../../build/reference/compiler-option-warning-level.md) 选项。 有关详细信息，请参阅 [配置 64 位的程序](../../build/configuring-programs-for-64-bit-visual-cpp.md)。  
  
 在 32 位操作系统上测试以下类型的变量，如同在 64 位操作系统上使用的一样：  
  
-   int  
  
-   long  
  
-   指针  
  
 如果通常通过使用 64 位编译器编译应用程序，则可以仅在 32 位编译中禁用 **\/Wp64**，因为 64 位编译器会检测所有问题。 有关如何面向 Windows 64 位操作系统的详细信息，请参阅 [配置 64 位的程序](../../build/configuring-programs-for-64-bit-visual-cpp.md)。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目“属性页”对话框。  
  
     有关详细信息，请参阅 [如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  点击“命令行”属性页。  
  
4.  修改“附加选项”框以包括 **\/Wp64**。  
  
### 以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Detect64BitPortabilityProblems%2A>。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [配置 64 位的程序](../../build/configuring-programs-for-64-bit-visual-cpp.md)