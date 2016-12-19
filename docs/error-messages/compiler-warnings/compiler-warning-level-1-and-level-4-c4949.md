---
title: "编译器警告（等级 1 和等级 4）C4949 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4949"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4949"
ms.assetid: 34f45a05-c115-49cb-9f67-0bd4f0735d9b
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1 和等级 4）C4949
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

只有使用“\/clr\[:option\]”编译时，杂注“managed”和“unmanaged”才有意义  
  
 如果源代码未使用 [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) 编译，则编译器忽略 [托管](../../preprocessor/managed-unmanaged.md)和非托管杂注。  此警告是信息式的。  
  
 下面的示例生成 C4949：  
  
```  
// C4949.cpp  
// compile with: /LD /W1  
#pragma managed   // C4949  
```  
  
 当在不使用 **\/clr** 的情况下使用 **\#pragma unmanaged** 时，C4949 是等级为 4 的警告。  
  
 下面的示例生成 C4949：  
  
```  
// C4949b.cpp  
// compile with: /LD /W4  
#pragma unmanaged   // C4949  
```