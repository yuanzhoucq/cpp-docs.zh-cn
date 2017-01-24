---
title: "MIDL 属性页：高级 | Microsoft Docs"
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
  - "VC.Project.VCMidlTool.ErrorCheckBounds"
  - "VC.Project.VCMidlTool.ErrorCheckStubData"
  - "VC.Project.VCMidlTool.ErrorCheckAllocations"
  - "VC.Project.VCMidlTool.CPreprocessOptions"
  - "VC.Project.VCMidlTool.UndefinePreprocessorDefinitions"
  - "VC.Project.VCMidlTool.EnableErrorChecks"
  - "VC.Project.VCMidlTool.RedirectOutputAndErrors"
  - "VC.Project.VCMidlTool.ErrorCheckEnumRange"
  - "VC.Project.VCMidlTool.StructMemberAlignment"
  - "VC.Project.VCMidlTool.ErrorCheckRefPointers"
  - "VC.Project.VCMidlTool.ValidateParameters"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MIDL，属性页"
ms.assetid: d1c92e01-f403-4ed6-ab45-4043a3c9c6bb
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MIDL 属性页：高级
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

“MIDL”文件夹中的“高级”属性页指定下列 MIDL 编译器选项：  
  
-   启用错误检查 \([\/error](http://msdn.microsoft.com/library/windows/desktop/aa367324)\)  
  
-   检查分配 \([\/error](http://msdn.microsoft.com/library/windows/desktop/aa367324)\)  
  
-   检查绑定 \([\/error](http://msdn.microsoft.com/library/windows/desktop/aa367324)\)  
  
-   检查枚举范围 \([\/error](http://msdn.microsoft.com/library/windows/desktop/aa367324)\)  
  
-   检查引用指针 \([\/error](http://msdn.microsoft.com/library/windows/desktop/aa367324)\)  
  
-   检查存根 \(stub\) 数据 \([\/error](http://msdn.microsoft.com/library/windows/desktop/aa367324)\)  
  
-   验证参数 \([\/robust](http://msdn.microsoft.com/library/windows/desktop/aa367363)\) \*  
  
-   结构成员对齐 \([\/Zp](http://msdn.microsoft.com/library/windows/desktop/aa367388)\)  
  
-   重定向输出 \([\/o](http://msdn.microsoft.com/library/windows/desktop/aa367351)\)  
  
-   C 预处理选项 \([\/cpp\_opt](http://msdn.microsoft.com/library/windows/desktop/aa367318)\)  
  
-   取消定义预处理器 \([\/U](http://msdn.microsoft.com/library/windows/desktop/aa367373)\)  
  
 \* \/robust 仅在为 Windows 2000 或更高版本的计算机生成时使用。  如果生成 ATL 项目并且需要使用 \/robust，请将 dlldatax.c 文件中的此行：  
  
```  
#define _WIN32_WINNT 0x0400   //for Windows NT 4.0 or Windows 95 with DCOM  
to   
#define _WIN32_WINNT 0x0500   //for Windows NT 4.0 or Windows 95 with DCOM  
```  
  
 有关如何访问“MIDL”文件夹中的“高级”属性页的信息，请参见[如何：用属性页指定项目属性](../misc/how-to-specify-project-properties-with-property-pages.md)。  
  
 有关如何以编程方式访问 C\+\+ 项目的 MIDL 选项的信息，请参见 <xref:Microsoft.VisualStudio.VCProjectEngine.VCMidlTool>。  
  
## 请参阅  
 [“MIDL”属性页](../ide/midl-property-pages.md)