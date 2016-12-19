---
title: "__sidt | Microsoft Docs"
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
  - "__sidt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sidt 指令"
  - "__sidt 内部函数"
ms.assetid: 01e83d14-6e63-4dea-8f64-5a0339d69641
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __sidt
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 在指定的内存位置中断描述符 \(IDTR\)表寄存器值。  
  
## 语法  
  
```  
void __sidt(  
     void *Destination);  
```  
  
#### 参数  
  
|Parameter|说明|  
|---------------|--------|  
|\[in\] `Destination`|对存储 IDTR 的内存位置的指针。|  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__sidt`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 `__sidt` 功能与 `SIDT` 指令是等效的。  有关更多信息，搜索文档， “Intel 体系结构软件开发人员的准则，数量 2:设置命令在该站点引用， [Intel Corporation](http://go.microsoft.com/fwlink/?LinkId=127) ”。  
  
## 关闭 Microsoft 特定  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [\_\_lidt](../intrinsics/lidt.md)