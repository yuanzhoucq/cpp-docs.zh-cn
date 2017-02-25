---
title: "/IGNOREIDL（不将特性处理到 MIDL 中） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.IgnoreEmbeddedIDL"
  - "/ignoreidl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/IGNOREIDL 链接器选项"
  - "IGNOREIDL 链接器选项"
  - "-IGNOREIDL 链接器选项"
ms.assetid: 29514098-6a1c-4317-af2f-1dc268972780
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# /IGNOREIDL（不将特性处理到 MIDL 中）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/IGNOREIDL  
```  
  
## 备注  
 \/IGNOREIDL 选项指定不应将源代码中的任何 [IDL 特性](../../windows/idl-attributes.md)处理到 .idl 文件中。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击“嵌入的 IDL”属性页。  
  
4.  修改“忽略嵌入的 IDL”属性。  
  
### 以编程方式设置此链接器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreEmbeddedIDL%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)   
 [\/IDLOUT（命名 MIDL 输出文件）](../../build/reference/idlout-name-midl-output-files.md)   
 [\/TLBOUT（命名 .TLB 文件）](../../build/reference/tlbout-name-dot-tlb-file.md)   
 [\/MIDL（指定 MIDL 命令行选项）](../../build/reference/midl-specify-midl-command-line-options.md)   
 [Building an Attributed Program](../../windows/building-an-attributed-program.md)