---
title: "__readdr | Microsoft Docs"
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
  - "__readdr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__readdr 内部函数"
ms.assetid: 061b05da-c85e-4052-b392-106f14bb84f1
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __readdr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

读取指定的值调试注册。  
  
## 语法  
  
```  
unsigned         __readdr(unsigned int DebugRegister);  
unsigned __int64 __readdr(unsigned int DebugRegister);  
```  
  
#### 参数  
 \[in\] `DebugRegister`  
 标识调试注册的常数 0 到 7\)。  
  
## 返回值  
 指定的值调试注册。  
  
## 备注  
 这些内部可用内核模式，并且，实例仅可用作内部。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__readdr`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [\_\_readeflags](../intrinsics/readeflags.md)