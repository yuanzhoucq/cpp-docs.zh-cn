---
title: "/FD（IDE 最小重新生成） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/FD"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/FD 编译器选项 [C++]"
  - "FD 编译器选项 [C++]"
  - "-FD 编译器选项 [C++]"
ms.assetid: 7ef21b8c-a448-4bb4-9585-a2a870028e17
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# /FD（IDE 最小重新生成）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**\/FD** 不向用户公开，只有以下情况例外：在 C\+\+ 项目的**“属性页”**对话框中的[命令行](../../ide/command-line-property-pages.md)属性页中，当且仅当没有同时选择 [\/Gm \(启用最小重新生成\)](../../build/reference/gm-enable-minimal-rebuild.md) 时。  **\/FD** 在开发环境外不起作用。  **\/FD** 不在 **cl \/?** 的输出中公开。  
  
 如果在开发环境中不启用 **\/Gm**，将使用 **\/FD**。  **\/FD** 确保 .idb 文件具有足够的依赖项信息。  **\/FD** 仅由开发环境使用，并且不应从命令行或生成脚本使用它。  
  
## 请参阅  
 [输出文件 \(\/F\) 选项](../../build/reference/output-file-f-options.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)