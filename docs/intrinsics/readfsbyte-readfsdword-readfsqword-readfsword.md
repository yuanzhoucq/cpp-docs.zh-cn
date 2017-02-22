---
title: "__readfsbyte、__readfsdword、__readfsqword、__readfsword | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__readfsword"
  - "__readfsdword"
  - "__readfsbyte"
  - "__readfsqword"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__readfsword 内部函数"
  - "readfsword 内部函数"
  - "__readfsdword 内部函数"
  - "readfsbyte 内部函数"
  - "__readfsbyte 内部函数"
  - "readfsdword 内部函数"
  - "readfsqword 内部函数"
  - "__readfsqword 内部函数"
ms.assetid: f6ee7203-4179-402c-a464-0746c84ce6ac
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# __readfsbyte、__readfsdword、__readfsqword、__readfsword
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 从偏移量的指定位置读取内存相对 FS 段开头。  
  
## 语法  
  
```  
unsigned char __readfsbyte(   
   unsigned long Offset   
);  
unsigned short __readfsword(   
   unsigned long Offset   
);  
unsigned long __readfsdword(   
   unsigned long Offset  
);  
unsigned __int64 __readfsqword(   
   unsigned long Offset   
);  
```  
  
#### 参数  
 \[in\] `Offset`  
 从最初读取的 `FS` 的偏移量。  
  
## 返回值  
 字节、单词、双字或多次字长的内存内容 \(如指示名为调用的函数\) 在位置 `FS:[``Offset``]`。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__readfsbyte`|x86|  
|`__readfsdword`|x86|  
|`__readfsqword`|x86|  
|`__readfsword`|x86|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 这些实例仅可用作内部。  
  
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [\_\_writefsbyte, \_\_writefsdword, \_\_writefsqword, \_\_writefsword](../intrinsics/writefsbyte-writefsdword-writefsqword-writefsword.md)   
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)