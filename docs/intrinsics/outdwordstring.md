---
title: "__outdwordstring | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__outdwordstring"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "outsb 指令"
  - "__outdwordstring 内部函数"
  - "rep outsd 指令"
ms.assetid: 55b31a65-aab7-4b5c-b61d-d9e2fb0c497a
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# __outdwordstring
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 生成 `rep outsd`命令，将开始在 `Buffer` I\/O 端口的 `Count` 双字指定由 `Port`。  
  
## 语法  
  
```  
void __outdwordstring(   
   unsigned short Port,   
   unsigned long* Buffer,   
   unsigned long Count   
);  
```  
  
#### 参数  
 \[in\] `Port`  
 发送数据的端口。  
  
 \[in\] `Buffer`  
 对于将发出指定端口的数据的指针。  
  
 \[in\] `Count`  
 发送的双字数。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__outdwordstring`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 此实例只能用作内部。  
  
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)