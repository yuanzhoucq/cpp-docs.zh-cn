---
title: "__getcallerseflags | Microsoft Docs"
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
  - "_getcallerseflags"
  - "_getcallerseflags_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_getcallerseflags 内部函数"
ms.assetid: 2386596f-33aa-4cc7-b026-5a834637270a
caps.latest.revision: 15
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __getcallerseflags
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 返回从调用方上下文的 EFLAGS 值。  
  
## 语法  
  
```  
unsigned int __getcallerseflags(void);  
```  
  
## 返回值  
 从调用方上下文的 EFLAGS 值。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__getcallerseflags`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 此实例只能用作内部。  
  
## 示例  
  
```  
// getcallerseflags.cpp  
// processor: x86, x64  
  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(__getcallerseflags)  
  
unsigned int g()  
{  
    unsigned int EFLAGS = __getcallerseflags();  
    printf_s("EFLAGS 0x%x\n", EFLAGS);  
    return EFLAGS;  
}  
unsigned int f()  
{  
    return g();  
}  
  
int main()  
{  
    unsigned int i;  
    i = f();  
    i = g();  
    return 0;  
}  
```  
  
  **EFLAGS 0x202**  
**EFLAGS 0x206**   
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)