---
title: "__inbyte | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__inbyte"
  - "__inbyte_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "in 指令"
  - "__inbyte 内部函数"
ms.assetid: 03b61799-2a08-474d-adc4-2cbf7c81a4d5
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# __inbyte
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 生成 `in` 命令，返回从端口读取的一个字节指定由 `Port`。  
  
## 语法  
  
```  
unsigned char __inbyte(  
   unsigned short Port  
);  
```  
  
#### 参数  
 \[in\] `Port`  
 读取的端口。  
  
## 返回值  
 从指定端口读取的字节数。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__inbyte`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 关闭 Microsoft 特定  
  
## 备注  
 此实例只能用作内部。  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)