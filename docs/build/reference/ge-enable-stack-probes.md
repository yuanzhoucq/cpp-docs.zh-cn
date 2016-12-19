---
title: "/Ge（启用堆栈探测） | Microsoft Docs"
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
  - "/ge"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Ge 编译器选项 [C++]"
  - "启用堆栈探测"
  - "Ge 编译器选项 [C++]"
  - "-Ge 编译器选项 [C++]"
  - "堆栈检查调用"
  - "堆栈探测"
  - "堆栈, 堆栈探测"
ms.assetid: 4b54deae-4e3c-4bfa-95f3-ba23590f7258
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Ge（启用堆栈探测）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

为需要局部变量存储的每个函数调用激活堆栈探测。  
  
## 语法  
  
```  
/Ge  
```  
  
## 备注  
 此机制在重写堆栈探测的功能时非常有用。  建议使用 [\/Gh（启用 \_penter 挂钩函数）](../../build/reference/gh-enable-penter-hook-function.md) 而不是重写堆栈探测。  
  
 [\/Gs（控制堆栈检查调用）](../../build/reference/gs-control-stack-checking-calls.md) 具有同样的作用。  
  
 不推荐使用 **\/Ge**；编译器将生成堆栈检查。  有关详细信息，请参阅[Deprecated Compiler Options in Visual C\+\+ 2005](http://msdn.microsoft.com/zh-cn/aa59fce3-50b8-4f66-9aeb-ce09a7a84cce)。  
  
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