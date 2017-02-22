---
title: "__svm_invlpga | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__svm_invlpga"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__svm_invlpga 内部函数"
  - "INVLPGA 指令"
ms.assetid: aa6578ce-8278-464b-8815-a0fc45330915
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# __svm_invlpga
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 无效在计算机将查找旁边的缓冲区的地址转换项。  参数指定页的虚拟地址和地址空间标识符无效。  
  
## 语法  
  
```  
void __svm_invlpga(  
     void *Va,  
     int ASID);  
```  
  
#### 参数  
  
|Parameter|说明|  
|---------------|--------|  
|\[in\] `Va`|无效的页的虚拟地址。|  
|\[in\] `ASID`|无效的页的 \(ASID\)地址空间标识符。|  
  
## 备注  
 `__svm_invlpga` 功能与 `INVLPGA` 指令是等效的。  此功能支持宿主的与来宾操作系统及其应用程序的虚拟机监控程序的交互。  有关更多信息，搜索文档， “AMD64 体系结构程序员的手动数量 2:系统编程，”在网站单据数字 24593，版本 3.11 [AMD corporation](http://go.microsoft.com/fwlink/?LinkId=23746) 中，。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__svm_invlpga`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)