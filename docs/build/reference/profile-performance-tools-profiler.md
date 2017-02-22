---
title: "/PROFILE（性能工具分析器） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.Profile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/PROFILE 链接器选项"
  - "-PROFILE 链接器选项"
ms.assetid: e676baa1-5063-47a3-a357-ba0d1f0d1699
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# /PROFILE（性能工具分析器）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

生成可与性能工具探查器一起使用的输出文件。  
  
## 语法  
  
```  
/PROFILE  
```  
  
## 备注  
 \/PROFILE 包含下列链接器选项：  
  
-   [\/OPT:REF](../../build/reference/opt-optimizations.md)  
  
-   \/OPT:NOICF  
  
-   [\/INCREMENTAL:NO](../../build/reference/incremental-link-incrementally.md)  
  
-   [\/FIXED:NO](../../build/reference/fixed-fixed-base-address.md)  
  
 \/PROFILE 使链接器在程序映像中生成一个重定位节。重定位节允许分析器转换程序映像以获取配置文件数据。  
  
 **\/PROFILE** 只可用于企业（团队开发）版本中。有关 PREfast 的更多信息，请参见 [C\/C\+\+ 代码分析概述](../Topic/Code%20Analysis%20for%20C-C++%20Overview.md)。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  展开**“配置属性”**节点。  
  
3.  展开**“链接器”**节点。  
  
4.  选择**“高级”**属性页。  
  
5.  修改**“配置文件”**属性。  
  
### 以编程方式设置此链接器选项  
  
1.  请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Profile%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)