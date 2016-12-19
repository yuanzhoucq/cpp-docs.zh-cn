---
title: "编译器错误 C3883 | Microsoft Docs"
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
  - "C3883"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3883"
ms.assetid: cdd1c1f4-f268-4469-9c62-d52303114b0c
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3883
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“var”: initonly 静态数据成员必须被初始化  
  
 标记为 [initonly](../../dotnet/initonly-cpp-cli.md) 的变量未正确初始化。  
  
 下面的示例生成 C3883：  
  
```  
// C3883.cpp  
// compile with: /clr  
ref struct Y1 {  
   initonly  
   static int staticConst1;   // C3883  
};  
```  
  
 下面的示例演示一个可能的解决方法：  
  
```  
// C3883b.cpp  
// compile with: /clr /c  
ref struct Y1 {  
   initonly  
   static int staticConst2 = 0;  
};  
```  
  
 下面的示例演示如何初始化静态构造函数：  
  
```  
// C3883c.cpp  
// compile with: /clr /LD  
ref struct Y1 {  
   initonly  
   static int staticConst1;  
  
   static Y1() {  
      staticConst1 = 0;  
   }  
};  
```