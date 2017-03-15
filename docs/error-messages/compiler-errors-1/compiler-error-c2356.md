---
title: "编译器错误 C2356 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2356"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2356"
ms.assetid: 84d5a816-9a61-4d45-9978-38e485bbf767
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C2356
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

初始化段在翻译单元期间不能更改  
  
 可能的原因：  
  
-   `#pragma init_seg` 的前面是段初始化代码  
  
-   `#pragma init_seg` 的前面是另一个 `#pragma init_seg`  
  
 要解决此错误，将该段初始化代码移到模块的开始处。  如果必须初始化多个区域，请将它们移到单独的模块中。  
  
 下面的示例生成 C2356：  
  
```  
// C2356.cpp  
#pragma warning(disable : 4075)  
  
int __cdecl myexit(void (__cdecl *)());  
int __cdecl myexit2(void (__cdecl *)());  
  
#pragma init_seg(".mine$m",myexit)  
#pragma init_seg(".mine$m",myexit2)   // C2356  
```