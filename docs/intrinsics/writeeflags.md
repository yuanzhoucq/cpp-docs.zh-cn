---
title: "__writeeflags | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__writeeflags"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__writeeflags 内部函数"
ms.assetid: a62a522c-d7fa-4f10-a620-a3b32bdf3f17
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# __writeeflags
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

写入程序状态和控件 \(EFLAGS\) 注册的指定值。  
  
## 语法  
  
```  
void __writeeflags(unsigned Value);  
void __writeeflags(unsigned __int64 Value);  
```  
  
#### 参数  
  
|Parameter|说明|  
|---------------|--------|  
|\[in\] `Value`|写入的值设置为 EFLAGS 注册。  `Value` 参数时间长度为 32 位 32 位平台上为 64 位和 64 位平台上。|  
  
## 备注  
 这些实例仅可用作内部。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__writeeflags`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 关闭 Microsoft 特定  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [\_\_readeflags](../intrinsics/readeflags.md)