---
title: "__readmsr | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__readmsr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "读取模型特定寄存器"
  - "rdmsr 指令"
  - "__readmsr 内部函数"
ms.assetid: 7ab1f8e8-72cb-4ce4-817d-3e728a3c9716
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# __readmsr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 生成 `rdmsr` 命令，读取 `register` 指定的样式特定的注册并返回其值。  
  
## 语法  
  
```  
__int64 __readmsr(   
   int register   
);  
```  
  
#### 参数  
 \[in\] `register`  
 读取的样式特定的注册。  
  
## 返回值  
 在指定的寄存器值。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__readmsr`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 此功能才可用内核模式，并且，实例只能用作内部。  
  
 有关更多信息，请参见 AMD 文档。  
  
## 关闭 Microsoft 特定  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)