---
title: "__shiftright128 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__shiftright128"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__shiftright128 intrinsic"
ms.assetid: 5419a6c4-0de1-43fb-b314-4faa5b2d051f
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# __shiftright128
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 将 128 位数量（表示为两个 64 位数量 `LowPart` 和 `HighPart`）按 `Shift` 指定的位数右移并返回低 64 位结果。  
  
## 语法  
  
```  
unsigned __int64 __shiftright128(     unsigned __int64 LowPart,     unsigned __int64 HighPart,     unsigned char Shift  );  
```  
  
#### 参数  
 \[in\] `LowPart`  
 要位移的 128 位数量的低 64 位。  
  
 \[in\] `HighPart`  
 要位移的 128 位数量的高 64 位。  
  
 \[in\] `Shift`  
 要位移的位数。  
  
## 返回值  
 结果的低 64 位。  
  
## 要求  
  
|内部函数|体系结构|  
|----------|----------|  
|`__shiftright128`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 `Shift` 值始终是模 64，如果调用 `__shiftright128(0, 1, 64)`，该函数将向右位移高部分 `0` 位并返回低部分的 `0` 而不是另外预期的 `1`。  
  
## 示例  
 有关示例，请参阅[\_\_shiftleft128](../intrinsics/shiftleft128.md)。  
  
## 结束 Microsoft 专用  
  
## 请参阅  
 [\_\_shiftleft128](../intrinsics/shiftleft128.md)   
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)