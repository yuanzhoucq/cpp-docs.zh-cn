---
title: "编译器错误 C2813 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2813"
ms.assetid: 6cf2135f-7b82-42d1-909a-5e864308a09c
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2813
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#import 不支持 \/MP  
  
 如果在编译器命令中指定 **\/MP** 编译器选项以及两个或更多文件进行编译，并且其中一个或多个文件包含 [\#import](../../preprocessor/hash-import-directive-cpp.md) 预处理器指令，则会发出 C2813。[\#import](../../preprocessor/hash-import-directive-cpp.md) 指令从指定类型库中的类型生成 C\+\+ 类，然后将这些类写入两个头文件。 不支持 [\#import](../../preprocessor/hash-import-directive-cpp.md) 指令，因为如果多个编译单元导入相同类型库，则这些单元在同时尝试写入相同头文件时会产生冲突。  
  
 此编译器错误和 **\/MP** 编译器选项是 [!INCLUDE[vs_orcas_long](../../atl/reference/includes/vs_orcas_long_md.md)] 中新增的。  
  
## 示例  
 下面的示例生成 C2813。 “compile with:”注释中的命令行向编译器指示使用 **\/MP** 和 **\/c** 编译器选项编译多个文件。 其中至少有一个文件包含 [\#import](../../preprocessor/hash-import-directive-cpp.md) 指令。 为了测试此示例，我们对相同文件使用了两次。  
  
```  
// C2813.cpp // compile with: /MP /c C2813.cpp C2813.cpp #import "C:\windows\system32\stdole2.tlb"   // C2813 int main() { }  
```