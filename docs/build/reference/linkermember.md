---
title: "/LINKERMEMBER | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/linkermember"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/LINKERMEMBER dumpbin 选项"
  - "LINKERMEMBER dumpbin 选项"
  - "-LINKERMEMBER dumpbin 选项"
ms.assetid: c96868c1-d70e-4651-ae36-c55b58b16406
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# /LINKERMEMBER
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/LINKERMEMBER[:{1|2}]  
```  
  
## 备注  
 此选项显示库中定义的公共符号。  指定参数 1 将按对象顺序显示符号及其偏移量。  指定参数 2 将显示对象的偏移量和索引号，然后按字母顺序列出这些符号及每个符号的对象索引。  若要两个输出都获得，指定不带数字参数的 \/LINKERMEMBER。  
  
 只有 [\/HEADERS](../../build/reference/headers.md) DUMPBIN 选项可用于由 [\/GL](../../build/reference/gl-whole-program-optimization.md) 编译器选项产生的文件。  
  
## 请参阅  
 [DUMPBIN 选项](../../build/reference/dumpbin-options.md)