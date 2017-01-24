---
title: "/IDLOUT（命名 MIDL 输出文件） | Microsoft Docs"
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
  - "/idlout"
  - "VC.Project.VCLinkerTool.MergedIDLBaseFileName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".idl 文件, 路径"
  - "/IDLOUT 链接器选项"
  - "IDL 文件, 路径"
  - "IDLOUT 链接器选项"
  - "-IDLOUT 链接器选项"
  - "MIDL"
  - "MIDL, 输出文件名"
ms.assetid: 10d00a6a-85b4-4de1-8732-e422c6931509
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /IDLOUT（命名 MIDL 输出文件）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/IDLOUT:[path\]filename  
```  
  
## 参数  
 *path*  
 绝对或相对路径规范。  指定路径仅影响 .idl 文件的位置；所有其他文件都放在项目目录中。  
  
 *filename*  
 指定 MIDL 编译器所创建的 .idl 文件的名称。  未假定任何文件扩展名；如果要用 .idl 扩展名，指定 *filename*.idl。  
  
## 备注  
 \/IDLOUT 选项指定 .idl 文件的名称和扩展名。  
  
 当链接具有 [module](../../windows/module-cpp.md) 特性的项目时，MIDL 编译器由 Visual C\+\+ 链接器调用。  
  
 \/IDLOUT 还指定与 MIDL 编译器关联的其他输出文件的文件名：  
  
-   *filename*.tlb  
  
-   *filename*\_p.c  
  
-   *filename*\_i.c  
  
-   *filename*.h  
  
 *filename* 是传递给 \/IDLOUT 的参数。  如果指定了 [\/TLBOUT](../../build/reference/tlbout-name-dot-tlb-file.md)，则 .tlb 将从 \/TLBOUT *filename* 获取其名称。  
  
 如果既不指定 \/IDLOUT 也不指定 \/TLBOUT，则链接器将创建 vc70.tlb、vc70.idl、vc70\_p.c、vc70\_i.c 和 vc70.h。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击“嵌入的 IDL”属性页。  
  
4.  修改“合并的 IDL 基文件名”属性。  
  
### 以编程方式设置此链接器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MergedIDLBaseFileName%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)   
 [\/IGNOREIDL（不将特性处理到 MIDL 中）](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)   
 [\/MIDL（指定 MIDL 命令行选项）](../../build/reference/midl-specify-midl-command-line-options.md)   
 [Building an Attributed Program](../../windows/building-an-attributed-program.md)