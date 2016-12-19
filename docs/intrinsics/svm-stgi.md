---
title: "__svm_stgi | Microsoft Docs"
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
  - "__svm_stgi"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__svm_stgi 内部函数"
  - "STGI 指令"
ms.assetid: 96488da4-5587-4e99-8674-627a9e51be84
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __svm_stgi
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 设置全局中断标志。  
  
## 语法  
  
```  
void __svm_stgi(void);  
```  
  
## 备注  
 `__svm_stgi` 功能与 `STGI` 指令是等效的。  全局中断标志确定微处理器是否忽略，延迟或处理中断由于诸如 I\/O 完成、硬件温度警报或调试异常。  
  
 此功能支持宿主的与来宾操作系统及其应用程序的虚拟机监控程序的交互。  有关更多信息，搜索文档， “AMD64 体系结构程序员的手动数量 2:系统编程，”在网站单据数字 24593，版本 3.11 [AMD corporation](http://go.microsoft.com/fwlink/?LinkId=23746) 中，。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__svm_stgi`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [\_\_svm\_clgi](../intrinsics/svm-clgi.md)