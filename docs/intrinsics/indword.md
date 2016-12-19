---
title: "__indword | Microsoft Docs"
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
  - "__indword_cpp"
  - "__indword"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "in 指令"
  - "__indword intrinsic"
ms.assetid: 1068d686-586e-4e36-b962-d1d7c3315260
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __indword
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 使用 `in` 命令，读取数据的双字从指定的端口。  
  
## 语法  
  
```  
unsigned long __indword(  
   unsigned short Port  
);  
```  
  
#### 参数  
 \[in\] `Port`  
 读取的端口。  
  
## 返回值  
 从端口读取的单词。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__indword`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 此实例只能用作内部。  
  
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)