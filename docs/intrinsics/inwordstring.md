---
title: "__inwordstring | Microsoft Docs"
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
  - "__inwordstring"
  - "__inwordstring_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__inwordstring intrinsic"
  - "rep insw 指令"
ms.assetid: 6de37939-017a-4740-9e3d-7de78a30daba
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __inwordstring
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 使用 `rep insw` 命令，读取从指定端口的数据。  
  
## 语法  
  
```  
void __inwordstring(  
   unsigned short Port,  
   unsigned short* Buffer,  
   unsigned long Count  
);  
```  
  
#### 参数  
 \[in\] `Port`  
 读取的端口。  
  
 \[out\] `Buffer`  
 从端口读取的数据写入此处。  
  
 \[in\] `Count`  
 数据的运行的数目阅读。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__inwordstring`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 此实例只能用作内部。  
  
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)