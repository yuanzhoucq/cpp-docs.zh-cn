---
title: "__lidt | Microsoft Docs"
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
  - "__lidt"
  - "__lidt_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LIDT 指令"
  - "__lidt 内部函数"
ms.assetid: 8298d25d-a19e-4900-828d-6b3b09841882
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __lidt
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 使用该值加载中断描述符表注册 \(IDTR\)在指定的内存位置。  
  
## 语法  
  
```  
void __lidt(  
     void *Source);  
```  
  
#### 参数  
  
|Parameter|说明|  
|---------------|--------|  
|\[in\] `Source`|要复制的值的指针 IDTR。|  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__lidt`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 `__lidt` 功能与 `LIDT` 指令等效，并且只能在的核心架构。  有关更多信息，搜索文档， “Intel 体系结构软件开发人员的准则，数量 2:设置命令在该站点引用， [Intel Corporation](http://go.microsoft.com/fwlink/?LinkId=127) ”。  
  
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [\_\_sidt](../intrinsics/sidt.md)