---
title: "__outbytestring | Microsoft Docs"
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
  - "__outbytestring"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rep outsb 指令"
  - "__outbytestring 内部"
  - "outsb 指令"
ms.assetid: c9150661-9c18-427f-bae8-710bba6ed78c
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __outbytestring
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 生成 `rep outsb` 命令，发送 `Buffer` 点的第一个 `Count` 字节数据。 `Port`指定的端口。  
  
## 语法  
  
```  
void __outbytestring(   
   unsigned short Port,   
   unsigned char* Buffer,   
   unsigned long Count   
);  
```  
  
#### 参数  
 \[in\] `Port`  
 发送数据的端口。  
  
 \[in\] `Buffer`  
 将发出指定端口的数据。  
  
 \[in\] `Count`  
 字节数要发送的数据。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__outbytestring`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 此实例只能用作内部。  
  
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)