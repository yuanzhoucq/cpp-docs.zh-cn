---
title: "向后兼容性 | Microsoft Docs"
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
  - "c.programs"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "向后兼容性"
  - "向后兼容性, C 运行库"
  - "兼容性, C 运行库"
  - "CRT, 兼容性"
ms.assetid: cc3175cf-97fd-492f-b329-5791aea63090
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 向后兼容性
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

对于产品在版本之间的兼容性，OLDNAMES.LIB 库映射旧名称的新名称。  例如, `open` 映射到 `_open`。  下面的组合必须显式链接OLDNAMES.LIB才能编译命令行选项:  
  
-   `/Zl` \(请忽略默认库名从对象文件\) 和 `/Ze` \(默认 \- 使用 Microsoft 扩展\)  
  
-   `/link` \(linker 控件\)，其 `/NOD` \(无默认搜索库\) 和 `/Ze`  
  
 有关编译器命令行选项的更多信息，请参见 [编译器引用](../build/reference/compiler-options.md)。  
  
## 请参阅  
 [兼容性](../c-runtime-library/compatibility.md)