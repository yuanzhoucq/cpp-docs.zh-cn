---
title: "__writegsbyte, __writegsdword, __writegsqword, __writegsword | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__writegsbyte"
  - "__writegsqword"
  - "__writegsdword"
  - "__writegsword"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__writegsqword 内部函数"
  - "__writegsbyte 内部函数"
  - "__writegsword 内部函数"
  - "__writegsdword 内部函数"
ms.assetid: 7746cf6d-2259-4139-9aab-c07dd75c8037
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# __writegsbyte, __writegsdword, __writegsqword, __writegsword
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 可补偿的指定位置写入内存相对 GS 段开头。  
  
## 语法  
  
```  
void __writegsbyte(   
   unsigned long Offset,   
   unsigned char Data   
);  
void __writegsword(   
   unsigned long Offset,   
   unsigned short Data   
);  
void __writegsdword(   
   unsigned long Offset,   
   unsigned long Data   
);  
void __writegsqword(   
   unsigned long Offset,   
   unsigned __int64 Data   
);  
```  
  
#### 参数  
 \[in\] `Offset`  
 从最初 GS 的偏移量写入。  
  
 \[in\] `Data`  
 要写入的值。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__writegsbyte`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`__writegsdword`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`__writegsqword`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`__writegsword`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 这些内部函数可以在仅内核模式，并且，这些实例只能用作内部。  
  
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [\_\_readgsbyte、\_\_readgsdword、\_\_readgsqword、\_\_readgsword](../intrinsics/readgsbyte-readgsdword-readgsqword-readgsword.md)   
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)