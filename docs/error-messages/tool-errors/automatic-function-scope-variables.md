---
title: "自动（函数范围）变量 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "自动变量"
  - "函数 [C++], 范围"
  - "范围, 在函数内声明的"
  - "变量, 自动"
ms.assetid: 6e1a14c2-1fb0-4937-8628-8d963cc35ed4
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 自动（函数范围）变量
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在一个函数内声明的变量只能在该函数的范围内使用。  
  
```  
// LNK2019_AV.cpp  
// compile with: /c  
void test(void);  
  
static int lnktest3 = 3;  
int lnktest4 = 4;  
  
int main() {  
   static int lnktest1 = 1;  
   int lnktest2 = 2;  
   test();  
}  
```  
  
 然后，  
  
```  
// LNK2019_AV_2.cpp  
// compile with: LNK2019_AV.cpp  
// LNK2019 expected  
extern int lnktest1;  
extern int lnktest2;  
extern int lnktest3;  
extern int lnktest4;  
  
void test(void) {  
   int i = 0;  
   i = lnktest1;  
   i = lnktest2;  
   i = lnktest3;  
   i = lnktest4;   // OK  
}  
```  
  
## 请参阅  
 [链接器工具错误 LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)