---
title: "编译器警告（等级 4）C4337 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4337"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4337"
ms.assetid: 70bc72d9-aac5-45cd-abd3-ebe42a05897b
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告（等级 4）C4337
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

交叉引用类型库“typelib1”\(在“typelib2”中\)正在自动导入  
  
 [\#import 指令](../../preprocessor/hash-import-directive-cpp.md)的 auto\_search 特性导致类型库被隐式导入。  
  
 假设磁盘上有两个使用以下两个文件创建的类型库（用 midl.exe 编译）：  
  
```  
// C4337a.idl  
[  
  uuid(F87070BA-C6D9-405C-A8E4-8CD9CA25C12B)  
]  
library C4337aLib  
{  
   [uuid(F87070BA-C6D9-405C-A8E4-8CD9CA25C12C)]  
   enum E_C4337a  
   {  
      one = 0,  
      two = 1,  
      three = 2  
    };  
};  
```  
  
 然后是第二个 .idl 文件，  
  
```  
// C4337b.idl  
[  
   uuid(F87070BA-C6D9-405C-A8E4-8CD9CA25C12D)  
]  
  
library C4337bLib  
{  
   importlib("c4337a.tlb");  
  
   [uuid(F87070BA-C6D9-405C-A8E4-8CD9CA25C12E)]  
   struct S_C4337b  
   {  
      enum E_C4337a e;  
   };  
};  
```  
  
 下面的示例生成 C4337：  
  
```  
// C4337.cpp  
// compile with: /W4 /LD  
#import "c4337b.tlb" auto_search   // C4337  
// explicitly #import all type libraries to resolve  
// #import "C4337a.tlb"  
// #import "C4337b.tlb"  
```