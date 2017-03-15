---
title: "__invlpg | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__invlpg"
  - "__invlpg_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "invlpg 指令"
  - "__invlpg 内部函数"
ms.assetid: 3fb3633f-d9b7-4ec0-9e7f-a7f2fa8ed794
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# __invlpg
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 生成 x86 `invlpg` 命令，页无效的将后援缓冲区 \(TLB\)与内存指向由 `Address`。  
  
## 语法  
  
```  
void __invlpg(  
   void* Address  
);  
```  
  
#### 参数  
 \[in\]  `Address`  
 一个 64位地址。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__invlpg`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 内部 `__invlpg` 只发出一个特权命令并可在与权限级别 \(CPL\) 的核心架构的 0。  
  
 此实例只能用作内部。  
  
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)