---
title: "__inbytestring | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__inbytestring"
  - "__inbytestring_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rep insb 指令"
  - "__inbytestring 内部函数"
ms.assetid: fe549556-e7a3-4af3-8ebf-8a7dc3cb233b
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# __inbytestring
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 使用 `rep insb` 命令，读取从指定端口的数据。  
  
## 语法  
  
```  
void __inbytestring(  
   unsigned short Port,  
   unsigned char* Buffer,  
   unsigned long Count  
);  
```  
  
#### 参数  
 \[in\] `Port`  
 读取的端口。  
  
 \[out\] `Buffer`  
 从端口读取的数据写入此处。  
  
 \[in\] `Count`  
 字节数读取。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__inbytestring`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 此实例只能用作内部。  
  
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)