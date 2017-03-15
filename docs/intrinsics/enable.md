---
title: "_enable | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_enable"
  - "_enable_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_enable intrinsic"
  - "enable intrinsic"
  - "ssm instruction"
ms.assetid: 8bee669b-6bd8-4e25-9383-bb7d57295b4d
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# _enable
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 启用中断。  
  
## 语法  
  
```  
void _enable(void);  
```  
  
## 要求  
  
|内部函数|体系结构|  
|----------|----------|  
|`_enable`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 `_enable` 指示处理器设置中断标志。  在 x86 系统上，此函数会生成“设置中断标志”\(`sti`\) 指令。  
  
 此函数只有在内核模式下才可用。  如果在用户模式下使用，会引发特权指令异常。  
  
## 结束 Microsoft 专用  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)