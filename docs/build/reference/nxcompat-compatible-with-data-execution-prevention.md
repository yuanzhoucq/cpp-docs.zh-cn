---
title: "/NXCOMPAT（与数据执行保护兼容） | Microsoft Docs"
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
  - "/NXCOMPAT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/NXCOMPAT 链接器选项"
  - "NXCOMPAT 链接器选项"
  - "-NXCOMPAT 链接器选项"
ms.assetid: 5858e7ff-24d3-4ac3-9046-af2c9e220d9b
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /NXCOMPAT（与数据执行保护兼容）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指示测试的可执行文件与 Windows 数据执行保护功能兼容。  
  
## 语法  
  
```  
/NXCOMPAT[:NO]  
```  
  
## 备注  
 默认情况下，**\/NXCOMPAT** 处于打开状态。  
  
 **\/NXCOMPAT:NO** 可用于将可执行文件显式指定为与数据执行保护不兼容。  
  
 有关数据执行保护的更多信息，请参阅以下文章：  
  
-   [数据执行保护（DEP）特征的详细介绍](http://go.microsoft.com/fwlink/?LinkID=157771)Microsoft帮助和支持网站  
  
-   在MSDN网站上的[数据执行保护](http://go.microsoft.com/fwlink/?LinkID=157770)  
  
-   在MSDN网站上的[数据执行保护 \(Windows Embedded\)](http://go.microsoft.com/fwlink/?LinkID=157768)  
  
### 在 Visual Studio 中设置此链接器选项  
  
1.  打开此项目的**“属性页”**对话框。  有关详细信息，请参见[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击**“命令行”**属性页。  
  
4.  在**“附加选项”**框中键入选项。  
  
### 以编程方式设置此链接器选项  
  
1.  请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)