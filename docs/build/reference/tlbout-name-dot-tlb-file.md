---
title: "/TLBOUT（命名 .TLB 文件） | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.TypeLibraryFile"
  - "/tlbout"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".tlb 文件, 重命名"
  - "/TLBOUT 链接器选项"
  - "tlb 文件, 重命名"
  - "TLBOUT 链接器选项"
  - "-TLBOUT 链接器选项"
ms.assetid: 0df6d078-2e48-46c9-a1a5-02674d85dce8
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /TLBOUT（命名 .TLB 文件）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/TLBOUT:[path\]filename  
```  
  
## 备注  
 其中：  
  
 *path*  
 应在其中创建 .tlb 文件的绝对或相对路径规范。  
  
 *filename*  
 指定 MIDL 编译器创建的 .tlb 文件的名称。  不假定文件扩展名；如果需要 .tlb 扩展名，则指定 *filename*.tlb。  
  
## 备注  
 \/TLBOUT 选项指定 .tlb 文件的名称和扩展名。  
  
 当链接具有 [module](../../windows/module-cpp.md) 特性的项目时，MIDL 编译器由 Visual C\+\+ 链接器调用。  
  
 如果未指定 \/TLBOUT，则 .tlb 文件将从 [\/IDLOUT](../../build/reference/idlout-name-midl-output-files.md) *filename* 获取其名称。  如果未指定 \/IDLOUT，则 .tlb 文件将称为 vc70.tlb。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击“嵌入的 IDL”属性页。  
  
4.  修改“类型库”属性。  
  
### 以编程方式设置此链接器选项  
  
1.  请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryFile%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)   
 [\/IGNOREIDL（不将特性处理到 MIDL 中）](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)   
 [\/MIDL（指定 MIDL 命令行选项）](../../build/reference/midl-specify-midl-command-line-options.md)   
 [Building an Attributed Program](../../windows/building-an-attributed-program.md)