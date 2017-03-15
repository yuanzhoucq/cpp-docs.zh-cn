---
title: "/DEF（指定模块定义文件） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.ModuleDefinitionFile"
  - "/def"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/DEF 链接器选项"
  - "DEF 链接器选项"
  - "-DEF 链接器选项"
  - "模块定义文件"
  - "模块定义文件, 指定"
ms.assetid: 6497fa68-65f0-48ca-8f66-b87166fc631a
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# /DEF（指定模块定义文件）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/DEF:filename  
```  
  
## 备注  
 其中：  
  
 *filename*  
 要传递到链接器的模块定义文件 \(.def\) 的名称。  
  
## 备注  
 \/DEF 选项将模块定义文件\(.def\)传递到链接器。  只能为 LINK 指定一个 .def 文件。  有关 .def 文件的详细信息，请参见[模块定义文件](../../build/reference/module-definition-dot-def-files.md)。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击“输入”属性页。  
  
4.  修改“模块定义文件”属性。  
  
 若要从开发环境内指定 .def 文件，应将它连同其他文件一起添加到项目，然后将该文件指定给 \/DEF 选项。  
  
### 以编程方式设置此链接器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ModuleDefinitionFile%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)