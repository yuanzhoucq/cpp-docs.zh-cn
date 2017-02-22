---
title: "/MIDL（指定 MIDL 命令行选项） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/midl"
  - "VC.Project.VCLinkerTool.MidlCommandFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/MIDL 链接器选项"
  - "MIDL"
  - "MIDL 链接器选项"
  - "-MIDL 链接器选项"
  - "MIDL, 命令行选项"
ms.assetid: 22dc259e-b34c-4ed3-a380-4beb734482c1
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# /MIDL（指定 MIDL 命令行选项）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/MIDL:@file  
```  
  
## 备注  
 其中：  
  
 `file`  
 包含 [MIDL 命令行选项](http://msdn.microsoft.com/library/windows/desktop/aa366839)的文件的名称。  
  
## 备注  
 将 IDL 文件转换为 TLB 文件的所有选项都必须在 `file` 中给定；不能在链接器的命令行上指定 MIDL 命令行选项。  如果未指定 \/MIDL，调用 MIDL 编译器时将只使用 IDL 文件名，不使用任何其他选项。  
  
 该文件中的每行应包含一个 MIDL 命令行选项。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击“嵌入的 IDL”属性页。  
  
4.  修改“MIDL 命令”属性。  
  
### 以编程方式设置此链接器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MidlCommandFile%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)   
 [\/IDLOUT（命名 MIDL 输出文件）](../../build/reference/idlout-name-midl-output-files.md)   
 [\/IGNOREIDL（不将特性处理到 MIDL 中）](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)   
 [\/TLBOUT（命名 .TLB 文件）](../../build/reference/tlbout-name-dot-tlb-file.md)   
 [Building an Attributed Program](../../windows/building-an-attributed-program.md)