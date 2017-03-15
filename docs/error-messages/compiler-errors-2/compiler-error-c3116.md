---
title: "编译器错误 C3116 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3116"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3116"
ms.assetid: 597463e1-a5cc-4ed3-a917-eae9a61d3312
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器错误 C3116
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“storage specifier”: 接口方法的存储类无效  
  
 使用了 `typedef`、`register` 或 `static` 作为接口方法的存储类。  在接口成员上不允许这些存储类。  
  
 下面的示例生成 C3116：  
  
```  
// C3116.cpp  
__interface ImyInterface  
{  
   static void myFunc();   // C3116  
};  
```