---
title: "/errorReport（报告内部编译器错误） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.ErrorReporting"
  - "/errorreport"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/errorReport 编译器选项 [C++]"
  - "-errorReport 编译器选项 [C++]"
ms.assetid: 819828f8-b0a5-412c-9c57-bf822f17e667
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# /errorReport（报告内部编译器错误）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

允许您将内部编译器错误 \(ICE\) 信息直接提供给 Microsoft。  
  
## 语法  
  
```  
/errorReport:[ none | prompt | queue | send ]  
```  
  
## Arguments  
 **none**  
 不收集有关内部编译器错误的报告，或不向 Microsoft 发送报告。  
  
 **prompt**  
 当您收到内部编译器错误时，提示您发送报告。  在开发环境中编译应用程序时，**prompt** 是默认值。  
  
 **queue**  
 对错误报告进行排队。  当使用管理员权限登录时，将显示窗口，因此您可以报告自上次登录以来的任何失败（每三天提示您发送失败报告不超过一次）。  在命令提示下编译应用程序时，**queue** 是默认值。  
  
 **send**  
 自动向 Microsoft 发送内部编译器错误报告。  若要启用此选项，必须先同意 Microsoft 数据收集策略。  首次在计算机上指定 **\/errorReport:send** 时，编译器消息将引导您访问包含 Microsoft 数据收集策略的网站。  
  
 此选项取决于注册表设置。  有关如何设置注册表的适当值的信息，请 [如何打开在 Visual Studio 2008 命令行工具的自动错误报告](http://go.microsoft.com/fwlink/?LinkID=184695) 参见 MSDN 网站。  
  
## 备注  
 当编译器无法处理源代码文件时，将导致内部编译器错误 \(ICE\)。  当发生 ICE 时，编译器不生成输出文件或可用来修复代码的任何有用的诊断。  
  
 在早期版本中，当收到 ICE 时，最好联系 Microsoft 产品支持服务以报告问题。  使用 **\/errorReport**，可以直接向 Microsoft 提供 ICE 信息。  错误报告有助于改进将来的编译器版本。  
  
 用户发送报告的能力取决于计算机和用户策略权限。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开此项目的**“属性页”**对话框。  有关详细信息，请参阅[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“高级”**属性页。  
  
4.  修改**“错误报告”**属性。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ErrorReporting%2A>。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)