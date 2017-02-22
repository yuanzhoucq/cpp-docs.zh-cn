---
title: "/PDBSTRIPPED（去除私有符号） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/pdbstripped"
  - "VC.Project.VCLinkerTool.StripPrivateSymbols"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pdb 文件, 去除私有符号"
  - "/PDBSTRIPPED 链接器选项"
  - "PDB 文件, 去除私有符号"
  - "PDBSTRIPPED 链接器选项"
  - "-PDBSTRIPPED 链接器选项"
ms.assetid: 9b9e0070-6a13-4142-8180-19c003fbbd55
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# /PDBSTRIPPED（去除私有符号）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/PDBSTRIPPED:pdb_file_name  
```  
  
## 备注  
 其中：  
  
 *pdb\_file\_name*  
 链接器创建的去除程序数据库 \(PDB\) 的用户指定名称。  
  
## 备注  
 当使用任何生成 PDB 文件的编译器或链接器选项（[\/DEBUG](../../build/reference/debug-generate-debug-info.md)、[\/Z7](../../build/reference/z7-zi-zi-debug-information-format.md)、\/Zd 或 \/Zi）生成程序图像时，\/PDBSTRIPPED 选项创建第二个程序数据库 \(PDB\) 文件。  此 PDB 文件省略您不希望交付给客户的符号。  第二个 PDB 文件仅包含：  
  
-   公共符号  
  
-   对象文件的列表和可执行文件中由它们参与构成的部分  
  
-   用于遍历堆栈的帧指针优化 \(FPO\) 调试记录  
  
 去除的 PDB 文件不包含：  
  
-   类型信息  
  
-   行号信息  
  
-   基于对象文件的 CodeView 符号，如函数、局部变量和静态数据的符号  
  
 当使用 \/PDBSTRIPPED 时，仍将生成完整的 PDB 文件。  
  
 如果不创建 PDB 文件，则将忽略 \/PDBSTRIPPED。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击“调试”属性页。  
  
4.  修改“去除私有符号”属性。  
  
### 以编程方式设置此链接器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StripPrivateSymbols%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)