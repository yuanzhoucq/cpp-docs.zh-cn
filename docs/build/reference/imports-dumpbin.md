---
title: "/IMPORTS (DUMPBIN) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/imports"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/IMPORTS dumpbin 选项"
  - "IMPORTS dumpbin 选项"
  - "-IMPORTS dumpbin 选项"
ms.assetid: 6a296216-2b1b-40f8-8736-cd4553a22456
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# /IMPORTS (DUMPBIN)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/IMPORTS[:file]  
```  
  
 此选项显示导入到可执行文件或 DLL 的 DLL 列表（静态链接的和[延迟加载](../../build/reference/linker-support-for-delay-loaded-dlls.md)）和上述每个 DLL 的各个导入。  
  
 可选 `file` 规范允许指定仅显示某个 DLL 的导入。  例如：  
  
```  
dumpbin /IMPORTS:msvcrt.dll  
```  
  
## 备注  
 此选项显示的输出与 [\/EXPORTS](../../build/reference/dash-exports.md) 输出相似。  
  
 只有 [\/HEADERS](../../build/reference/headers.md) DUMPBIN 选项可用于由 [\/GL](../../build/reference/gl-whole-program-optimization.md) 编译器选项产生的文件。  
  
## 请参阅  
 [DUMPBIN 选项](../../build/reference/dumpbin-options.md)