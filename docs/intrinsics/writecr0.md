---
title: "__writecr0 | Microsoft Docs"
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
  - "_writecr0"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_writecr0 内部函数"
ms.assetid: a143d08d-0333-4e1b-91b4-4acb2ae91b5a
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __writecr0
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 写入 CR0 寄存器值 `Data` 。  
  
## 语法  
  
```  
void writecr0(   
   unsigned __int64 Data   
);  
```  
  
#### 参数  
 \[in\] `Data`  
 写入的值设置为 CR0 注册。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__writecr0`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 此内部只有在内核模式，并且，实例只能用作内部。  
  
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)