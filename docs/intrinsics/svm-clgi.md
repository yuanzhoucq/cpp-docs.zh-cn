---
title: "__svm_clgi | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__svm_clgi"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLGI 指令"
  - "__svm_clgi 内部函数"
ms.assetid: 6640f5ab-9472-46f9-a042-e15c4f1ff858
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# __svm_clgi
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 清除全局中断标志。  
  
## 语法  
  
```  
void __svm_clgi( void );  
```  
  
## 备注  
 `__svm_clgi` 功能与 `CLGI` 指令是等效的。  全局中断标志确定微处理器是否忽略，延迟或处理中断由于诸如 I\/O 完成、硬件温度警报或调试异常。  
  
 此功能支持宿主的与来宾操作系统及其应用程序的虚拟机监控程序的交互。  有关更多信息，搜索文档， “AMD64 体系结构程序员的手动数量 2:系统编程，”在网站单据数字 24593，版本 3.11 [AMD corporation](http://go.microsoft.com/fwlink/?LinkId=23746) 中，。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__svm_clgi`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [\_\_svm\_stgi](../intrinsics/svm-stgi.md)