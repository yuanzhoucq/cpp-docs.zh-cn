---
title: "/ERRORREPORT（报告内部链接器错误） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/ERRORREPORT"
  - "VC.Project.VCLinkerTool.ErrorReporting"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/ERRORREPORT 链接器选项"
  - "ERRORREPORT 链接器选项"
  - "-ERRORREPORT 链接器选项"
ms.assetid: f5fab595-a2f1-4eb0-ab5c-1c0fbd3d8c28
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# /ERRORREPORT（报告内部链接器错误）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/errorReport:[ none | prompt | queue | send ]  
```  
  
## 备注  
 允许您将内部编译器错误 \(ICE\) 信息直接提供给 Microsoft。  
  
 选项 **\/errorReport:send** 尝试自动发送错误信息到 Microsoft，但成功与否取决于注册表设置。  有关在注册表中如何设置相应值的更多信息，请参见 MSDN 网站上 [How to Turn on Automatic Error Reporting in Visual Studio 2008 Command\-line Tools（如何在 Visual Studio 2008 的命令行工具中打开自动错误报告）](http://go.microsoft.com/fwlink/?LinkID=184695)。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开此项目的**“属性页”**对话框。  有关详细信息，请参阅[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“配置属性”**文件夹。  
  
3.  单击**“链接器”**文件夹。  
  
4.  单击**“高级”**属性页。  
  
5.  修改**“错误报告”**属性。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ErrorReporting%2A>。  
  
## 请参阅  
 [\/errorReport（报告内部编译器错误）](../../build/reference/errorreport-report-internal-compiler-errors.md)   
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)