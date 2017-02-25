---
title: "__outwordstring | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__outwordstring"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rep outsw 指令"
  - "__outwordstring 内部函数"
  - "outsw 指令"
ms.assetid: b470c7a0-1de9-4370-886a-b2c3a1f842f4
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# __outwordstring
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 生成 `rep outsw` 命令，将开始在 `Buffer` I\/O 端口的 `Count` 运行指定的 `Port`。  
  
## 语法  
  
```  
void __outwordstring(   
   unsigned short Port,   
   unsigned short* Buffer,   
   unsigned long Count   
);  
```  
  
#### 参数  
 \[in\] `Port`  
 发送数据的端口。  
  
 \[in\] `Buffer`  
 对于将发出指定端口的数据的指针。  
  
 \[in\] `Count`  
 发送的运行的数目。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__outwordstring`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 此实例只能用作内部。  
  
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)