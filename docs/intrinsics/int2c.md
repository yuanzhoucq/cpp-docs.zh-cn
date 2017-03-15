---
title: "__int2c | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__int2c"
  - "__int2c_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "int2c 内部函数"
  - "int 2c 指令"
  - "__int2c 内部函数"
ms.assetid: aa20ff30-adef-42bb-8577-8010f3122f8e
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# __int2c
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 生成 `int 2c` 命令，触发 `2c` 中断。  
  
## 语法  
  
```  
void __int2c(void);  
```  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__int2c`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)