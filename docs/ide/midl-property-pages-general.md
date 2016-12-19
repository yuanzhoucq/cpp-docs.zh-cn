---
title: "MIDL 属性页：常规 | Microsoft Docs"
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
  - "VC.Project.VCMidlTool.PreprocessorDefinitions"
  - "VC.Project.VCMidlTool.DefaultCharType"
  - "VC.Project.VCMidlTool.WarnAsError"
  - "VC.Project.VCMidlTool.AdditionalIncludeDirectories"
  - "VC.Project.VCMidlTool.WarningLevel"
  - "VC.Project.VCMidlTool.MkTypLibCompatible"
  - "VC.Project.VCMidlTool.GenerateStublessProxies"
  - "VC.Project.VCMidlTool.SuppressStartupBanner"
  - "VC.Project.VCMidlTool.TargetEnvironment"
  - "VC.Project.VCMidlTool.IgnoreStandardIncludePath"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MIDL，属性页"
ms.assetid: 0692484c-a7e6-4270-8df7-981589368399
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MIDL 属性页：常规
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

“MIDL”文件夹中的“常规”属性页指定下列 MIDL 编译器选项：  
  
-   预处理器定义\([\/D](http://msdn.microsoft.com/library/windows/desktop/aa367321)\)  
  
-   附加包含目录\([\/I](http://msdn.microsoft.com/library/windows/desktop/aa367328)\)  
  
-   忽略标准包含路径\([\/no\_def\_idir](http://msdn.microsoft.com/library/windows/desktop/aa367347)\)  
  
-   MkTypLib 兼容\([\/mktyplib203](http://msdn.microsoft.com/library/windows/desktop/aa367332)\)  
  
-   警告等级\([\/W](http://msdn.microsoft.com/library/windows/desktop/aa367383)\)  
  
-   警告视为错误\([\/WX](http://msdn.microsoft.com/library/windows/desktop/aa367387)\)  
  
-   取消显示启动版权标志\([\/nologo](http://msdn.microsoft.com/library/windows/desktop/aa367341)\)  
  
-   MIDL Char 类型\([\/char](http://msdn.microsoft.com/library/windows/desktop/aa367314)\)  
  
-   目标环境\([\/env](http://msdn.microsoft.com/library/windows/desktop/aa367323)\)  
  
-   生成无存根代理\([\/Oicf](http://msdn.microsoft.com/library/windows/desktop/aa367352)\)  
  
 有关如何访问“MIDL”文件夹中的“常规”属性页的信息，请参见[如何：用属性页指定项目属性](../misc/how-to-specify-project-properties-with-property-pages.md)。  
  
 有关如何以编程方式访问 C\+\+ 项目的 MIDL 选项的信息，请参见 <xref:Microsoft.VisualStudio.VCProjectEngine.VCMidlTool> 对象。  
  
## 请参阅  
 [“MIDL”属性页](../ide/midl-property-pages.md)