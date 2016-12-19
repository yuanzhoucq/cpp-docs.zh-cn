---
title: "__writecr4 | Microsoft Docs"
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
  - "_writecr4"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_writecr4 内部函数"
ms.assetid: ab7651d7-b86b-4be7-a0a0-7263099c70fc
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __writecr4
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 写入 CR4 寄存器值 `Data` 。  
  
## 语法  
  
```  
void writecr4(   
   unsigned __int64 Data   
);  
```  
  
#### 参数  
 \[in\] `Data`  
 写入的值设置为 CR4 注册。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__writecr4`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 此内部只有在内核模式，并且，实例只能用作内部。  
  
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)