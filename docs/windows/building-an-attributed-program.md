---
title: "Building an Attributed Program | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tlb files"
  - "MIDL"
  - "MIDL, linker output"
  - "IDL files"
  - "tlb files, building attributed programs"
  - ".tlb files, building attributed programs"
  - "IDL files, building"
  - "attributes [C++], building type libraries and .idl files"
  - ".tlb files"
  - ".idl files, building"
  - "type libraries, linker options for building"
ms.assetid: 04997b5f-bf2c-46ec-b868-c4adebbef5f4
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Building an Attributed Program
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在将 Visual C\+\+ 属性到源代码后，您可以 Visual C\+\+ 编译器生成类型库和您的 .idl 文件。  下列链接器选项可帮助您生成 .tlb 和 .idl 文件:  
  
-   [\/IDLOUT](../build/reference/idlout-name-midl-output-files.md)  
  
-   [\/IGNOREIDL](../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)  
  
-   [\/MIDL](../build/reference/midl-specify-midl-command-line-options.md)  
  
-   [\/TLBOUT](../build/reference/tlbout-name-dot-tlb-file.md)  
  
 一些项目包含多个独立 .idl 文件。  这些用于生成两个或多个 .tlb 文件，并选择绑定到该资源块。  此方案在 Visual C\+\+ 当前不支持。  
  
 此外， Visual C\+\+ 链接器将输出所有 IDL 相关的属性信息为单个 MIDL 文件。  将无法生成两个类型从单个项目的库。  
  
## 请参阅  
 [Concepts](../windows/attributed-programming-concepts.md)