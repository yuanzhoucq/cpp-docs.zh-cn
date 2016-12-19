---
title: "/LINENUMBERS | Microsoft Docs"
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
  - "/linenumbers"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/LINENUMBERS dumpbin 选项"
  - "行号"
  - "LINENUMBERS dumpbin 选项"
  - "-LINENUMBERS dumpbin 选项"
ms.assetid: 1681d582-2c2f-484e-9920-109959549055
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /LINENUMBERS
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/LINENUMBERS  
```  
  
## 备注  
 此选项显示 COFF 行号。  如果对象文件是用程序数据库 \(\/Zi\)、C7 兼容 \(\/Z7\) 或仅限行号 \(\/Zd\) 编译的，则它包含行号。  如果可执行文件或 DLL 是与生成调试信息 \(\/DEBUG\) 链接的，则它包含 COFF 行号。  
  
 只有 [\/HEADERS](../../build/reference/headers.md) DUMPBIN 选项可用于由 [\/GL](../../build/reference/gl-whole-program-optimization.md) 编译器选项产生的文件。  
  
## 请参阅  
 [DUMPBIN 选项](../../build/reference/dumpbin-options.md)