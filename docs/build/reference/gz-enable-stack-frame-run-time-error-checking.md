---
title: "/GZ（启用堆栈帧运行时错误检查） | Microsoft Docs"
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
  - "/gz"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/GZ 编译器选项 [C++]"
  - "调试版本, 捕捉版本生成错误"
  - "GZ 编译器选项 [C++]"
  - "-GZ 编译器选项 [C++]"
  - "发行版本错误"
ms.assetid: b3efeeff-d5e3-4057-91c9-f6fc73d0270c
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /GZ（启用堆栈帧运行时错误检查）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

执行与 [\/RTC（运行时错误检查）](../../build/reference/rtc-run-time-error-checks.md) 选项相同的操作。  已否决。  
  
## 语法  
  
```  
/GZ  
```  
  
## 备注  
 **\/GZ** 仅用于非优化的 \([\/Od（禁用（调试））](../../build/reference/od-disable-debug.md)\) 生成。  
  
 **\/GZ** 已弃用；请改用 [\/RTC（运行时错误检查）](../../build/reference/rtc-run-time-error-checks.md)。  有关详细信息，请参阅[Deprecated Compiler Options in Visual C\+\+ 2005](http://msdn.microsoft.com/zh-cn/aa59fce3-50b8-4f66-9aeb-ce09a7a84cce)。  
  
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