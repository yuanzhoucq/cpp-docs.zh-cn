---
title: "__writefsbyte, __writefsdword, __writefsqword, __writefsword | Microsoft Docs"
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
  - "__writefsword"
  - "__writefsbyte"
  - "__writefsqword"
  - "__writefsdword"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "writefsbyte 内部函数"
  - "__writefsword 内部函数"
  - "writefsqword 内部函数"
  - "writefsdword 内部函数"
  - "__writefsdword 内部函数"
  - "__writefsqword 内部函数"
  - "__writefsbyte 内部函数"
  - "writefsword 内部函数"
ms.assetid: 23ac6e8e-bc91-4e90-a4c6-da02993637ad
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __writefsbyte, __writefsdword, __writefsqword, __writefsword
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 可补偿的指定位置写入内存相对 FS 段开头。  
  
## 语法  
  
```  
void __writefsbyte(   
   unsigned long Offset,   
   unsigned char Data   
);  
void __writefsword(   
   unsigned long Offset,   
   unsigned short Data   
);  
void __writefsdword(   
   unsigned long Offset,   
   unsigned long Data   
);  
void __writefsqword(   
   unsigned long Offset,   
   unsigned __int64 Data   
);  
```  
  
#### 参数  
 \[in\] `Offset`  
 从最初 FS 的偏移量写入。  
  
 \[in\] `Data`  
 要写入的值。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__writefsbyte`|x86|  
|`__writefsword`|x86|  
|`__writefsdword`|x86|  
|`__writefsqword`|x86|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 这些实例仅可用作内部。  
  
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [\_\_readfsbyte、\_\_readfsdword、\_\_readfsqword、\_\_readfsword](../intrinsics/readfsbyte-readfsdword-readfsqword-readfsword.md)   
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)