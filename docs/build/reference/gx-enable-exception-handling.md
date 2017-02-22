---
title: "/GX（启用异常处理） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/gx"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/GX 编译器选项 [C++]"
  - "cl.exe 编译器, 异常处理"
  - "启用异常处理编译器选项 [C++]"
  - "异常处理, 启用"
  - "GX 编译器选项 [C++]"
  - "-GX 编译器选项 [C++]"
ms.assetid: 933b43ba-de77-4ff8-a48b-7074de90bc1c
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# /GX（启用异常处理）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

启用同步异常处理，并假定 `extern` C 函数从不引发异常。  
  
## 语法  
  
```  
/GX  
```  
  
## 备注  
 它等效于 [\/EH（异常处理模型）](../../build/reference/eh-exception-handling-model.md)。  
  
 当从开发环境内部编译时，默认情况下 **\/GX** 有效。  当使用命令行工具时，默认情况下启用 **\/GX\-**。  
  
 有关详细信息，请参阅[C\+\+ 异常处理](../../cpp/cpp-exception-handling.md)。  
  
 **\/GX** 已弃用；请改用 [\/EH（异常处理模型）](../../build/reference/eh-exception-handling-model.md)。  有关详细信息，请参阅[Deprecated Compiler Options in Visual C\+\+ 2005](http://msdn.microsoft.com/zh-cn/aa59fce3-50b8-4f66-9aeb-ce09a7a84cce)。  
  
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