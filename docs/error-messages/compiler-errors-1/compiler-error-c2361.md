---
title: "编译器错误 C2361 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2361
dev_langs: C++
helpviewer_keywords: C2361
ms.assetid: efbdaeb9-891c-4f7d-97da-89088a8413f3
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3e80c1a1ebcd56b4125ef9aa43e904d9093fc8a9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2361"></a>编译器错误 C2361
identifier 的初始化已跳过 default 标签  
  
 初始化`identifier`可以跳过中`switch`语句。 除非声明将封闭的块中，不能跳过具有初始值设定项的声明。 (除非它被声明在块内，始终在范围变量的结束之前一直`switch`语句。)  
  
 下面的示例生成 C2361:  
  
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
  
 可能的解决方法：  
  
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