---
title: "快速编译 | Microsoft Docs"
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
  - "cl.exe 编译器, 性能"
  - "编译, 性能"
  - "快速编译"
  - "性能, cle.exe 编译器"
ms.assetid: 5fead136-ba69-40c8-8e25-236f89d5990a
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 快速编译
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

要提高编译的速度：  
  
-   使用[最小重新生成](../../build/reference/gm-enable-minimal-rebuild.md)，其中，只有当某个源文件依赖于头文件中的类的更改时，C\+\+ 编译器才重新编译它。  
  
-   [创建预编译头文件](../../build/reference/creating-precompiled-header-files.md)并使用[预编译头选项](../../build/reference/yc-create-precompiled-header-file.md)。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)