---
title: "_disable | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_disable_cpp"
  - "_disable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_disable intrinsic"
  - "disable intrinsic"
  - "rsm instruction"
ms.assetid: 52da3df9-815c-4524-9839-6d1742cff5c6
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# _disable
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 禁用中断。  
  
## 语法  
  
```  
void _disable(void);  
```  
  
## 要求  
  
|内部函数|体系结构|  
|----------|----------|  
|`_disable`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 `_disable` 指示处理器去清除中断标记。  在 x86 系统上，此函数会生成“清除中断标记”\(`cli`\) 指令。  
  
 此函数只有在内核模式下才可用。  如果在用户模式下使用，运行时会出现特权指令异常。  
  
 在 ARM 平台上，此例程只能用作内部函数。  
  
## 结束 Microsoft 专用  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)