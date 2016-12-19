---
title: "/GA（Windows 应用程序优化） | Microsoft Docs"
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
  - "VC.Project.VCCLCompilerTool.OptimizeForWindowsApplication"
  - "/ga"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/GA 编译器选项 [C++]"
  - "GA 编译器选项 [C++]"
  - "-GA 编译器选项 [C++]"
  - "“Windows 的优化”编译器选项"
ms.assetid: be97323e-15a0-4836-862c-95980b51926a
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /GA（Windows 应用程序优化）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使 .exe 文件的代码能够更加有效地访问线程本地存储区 \(TLS\) 变量。  
  
## 语法  
  
```  
/GA  
```  
  
## 备注  
 在基于 Windows 的程序中，**\/GA** 能够加快对用 [\_\_declspec\(thread\)](../../cpp/declspec.md) 声明的数据的访问。  设置此选项时，假定 [\_\_tls\_index](http://msdn.microsoft.com/library/windows/desktop/ms686749) 宏为 0。  
  
 对 DLL 使用 **\/GA** 可能导致代码生成错误。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“命令行”**属性页。  
  
4.  在**“附加选项”**框中键入编译器选项。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)