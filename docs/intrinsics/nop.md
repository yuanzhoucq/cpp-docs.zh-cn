---
title: "__nop | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__nop"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "nop 指令"
  - "__nop 内部函数"
ms.assetid: 7a2a938b-87e0-476d-a348-03ea7635b6b9
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# __nop
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 生成不执行操作的特定于平台的机器码。  
  
## 语法  
  
```  
void __nop();  
```  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__nop`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 特定于 Microsoft 的结尾  
  
## 备注  
 `__nop` 功能与 `NOP` 指令是等效的。  有关更多信息，搜索文档， “Intel 体系结构软件开发人员的准则，数量 2:设置命令在该站点引用， [Intel Corporation](http://go.microsoft.com/fwlink/?LinkId=127) ”。  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [\_\_noop](../intrinsics/noop.md)