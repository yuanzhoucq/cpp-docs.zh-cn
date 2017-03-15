---
title: "/PDB（使用程序数据库） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/pdb"
  - "VC.Project.VCLinkerTool.ProgramDatabaseFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pdb 文件, 创建"
  - "/PDB 链接器选项"
  - "PDB 文件, 创建"
  - "PDB 链接器选项"
  - "-PDB 链接器选项"
ms.assetid: d23db0ce-10cb-427a-bc60-d6b2a852723d
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# /PDB（使用程序数据库）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/PDB:filename  
```  
  
## 备注  
 其中：  
  
 *filename*  
 链接器创建的程序数据库 \(PDB\) 的用户指定名称。  该名称将会替换默认名称。  
  
## 备注  
 默认情况下，若指定了 [\/DEBUG](../../build/reference/debug-generate-debug-info.md)，链接器将创建保存调试信息的程序数据库 \(PDB\)。  PDB 的默认文件名由程序的基名称和 .pdb 扩展名组成。  
  
 使用 \/PDB:*filename* 指定 PDB 文件的名称。  如果未指定 \/DEBUG，将忽略 \/PDB 选项。  
  
 PDB 文件最大可达 2GB。  
  
 有关更多信息，请参见[用作链接器输入的 .pdb 文件](../../build/reference/dot-pdb-files-as-linker-input.md)。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击“调试”属性页。  
  
4.  修改“生成程序数据库文件”属性。  
  
### 以编程方式设置此链接器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProgramDatabaseFile%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)