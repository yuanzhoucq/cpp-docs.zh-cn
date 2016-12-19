---
title: "编译器错误 C2361 | Microsoft Docs"
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
  - "C2361"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2361"
ms.assetid: efbdaeb9-891c-4f7d-97da-89088a8413f3
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2361
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“default”标签跳过“identifier”的初始化操作  
  
 在 `switch` 语句中可以跳过 `identifier` 的初始化。  不能跳过带有初始值设定项的声明，除非该声明包括在块中。（直到 `switch` 语句结尾变量始终在范围内，除非该变量在块中声明。）  
  
 下面的示例生成 C2361：  
  
```  
// C2361.cpp  
void func( void ) {  
   int x;  
   switch (x) {  
   case 0 :  
      int i = 1;  
      { int j = 1; }  
   default :   // C2361 error  
      int k = 1;  
   }  
}  
```  
  
 可能的解决方案：  
  
```  
// C2361b.cpp  
// compile with: /c  
void func( void ) {  
   int x = 0;  
   switch (x) {  
   case 0 :  
      { int j = 1; int i = 1;}  
   default :  
      int k = 1;  
   }  
}  
```