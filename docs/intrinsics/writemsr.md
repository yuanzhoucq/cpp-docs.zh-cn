---
title: "__writemsr | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__writemsr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "编写模型特定注册指令"
  - "wrmsr 指令"
  - "__writemsr 内部函数"
ms.assetid: 938b1553-51a8-4822-a818-6bed79b0fde5
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# __writemsr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 生成写入样式特定的寄存器 \(`wrmsr`\) 命令。  
  
## 语法  
  
```  
void __writemsr(   
   unsigned long Register,   
   unsigned __int64 Value   
);  
```  
  
#### 参数  
 \[in\] `Register`  
 样式特定的注册。  
  
 \[in\] `Value`  
 要写入的值。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__writemsr`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 此功能只能在内核模式，因此，此实例只能用作内部。  
  
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)