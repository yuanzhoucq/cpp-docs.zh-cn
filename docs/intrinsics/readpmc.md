---
title: "__readpmc | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__readpmc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Read Performance Monitoring Counters 指令"
  - "__readpmc intrinsic"
  - "rdpmc 指令"
ms.assetid: 14ed45a6-28b6-4635-8437-a597c04b43d4
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# __readpmc
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 生成 `rdpmc` 命令，读取 `counter`指定的性能监视计数器。  
  
## 语法  
  
```  
unsigned __int64 __readpmc(   
   unsigned long counter   
);  
```  
  
#### 参数  
 \[in\] `counter`  
 使用读取相反的性能。  
  
## 返回值  
 指定的性能计数器的值。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__readpmc`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 此内部函数可以在仅内核模式，并且，实例只能用作内部。  
  
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)