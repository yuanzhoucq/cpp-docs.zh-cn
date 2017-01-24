---
title: "/FORCE（强制文件输出） | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.ForceLink"
  - "/force"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/FORCE 链接器选项"
  - "链接器中的文件输出"
  - "FORCE 链接器选项"
  - "-FORCE 链接器选项"
ms.assetid: b1e9a218-a5eb-4e60-a4a4-65b4be15e5da
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /FORCE（强制文件输出）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/FORCE:[MULTIPLE|UNRESOLVED]  
```  
  
## 备注  
 即使引用了符号但未定义或多次定义符号，\/FORCE 选项也通知链接器创建有效的 .exe 文件或 DLL。  
  
 \/FORCE 选项可以带一个可选参数：  
  
-   使用 \/FORCE:MULTIPLE 可创建输出文件，而不管 LINK 是否找到了符号的多个定义。  
  
-   使用 \/FORCE:UNRESOLVED 可创建输出文件，而不管 LINK 是否找到未定义的符号。如果未解析入口点符号，则将忽略 \/FORCE:UNRESOLVED。  
  
 不带参数的 \/FORCE 表示多次定义和未解析。  
  
 用该选项创建的文件可能不会按预期运行。  当指定 \/FORCE 选项时，链接器将不增量链接。  
  
 如果使用 **\/clr** 编译模块，则 **\/FORCE** 将不会创建映像。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击**“命令行”**属性页。  
  
4.  将该选项键入**“附加选项”**框中。  
  
### 以编程方式设置此链接器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)