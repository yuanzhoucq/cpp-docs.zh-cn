---
title: "链接器工具错误 LNK2004 | Microsoft Docs"
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
  - "LNK2004"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2004"
ms.assetid: 07645371-e67b-4a2c-b0e0-dde24c94ef7e
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链接器工具错误 LNK2004
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“target”的 gp 相对链接地址信息溢出；短节“section”太大或超出范围。  
  
 节太大。  
  
 要解决此错误，请减小短节的大小，方法是通过 \#pragma 节（“.sectionname”、读、写、长）显式将数据放在长节中，或者对数据定义和声明使用 `__declspec(allocate(".sectionname"))`。例如，  
  
```  
#pragma section(".data$mylong", read, write, long)  
__declspec(allocate(".data$mylong"))  
char    rg0[1] = { 1 };  
char    rg1[2] = { 1 };  
char    rg2[4] = { 1 };  
char    rg3[8] = { 1 };  
char    rg4[16] = { 1 };  
char    rg5[32] = { 1 };  
```  
  
 还可以将逻辑上属于一个组的数据移到它自己的结构中，该结构将是一个大于 8 个字节的数据的集合，编译器将其分配在长数据节中。例如，  
  
```  
// from this...  
int     w1  = 23;  
int     w2 = 46;  
int     w3 = 23*3;  
int     w4 = 23*4;  
  
// to this...  
struct X {  
    int     w1;  
    int     w2;  
    int     w3;  
    int     w4;  
} x  = { 23, 23*2, 23*3, 23*4 };  
  
```  
  
 该错误之后为错误 `LNK1165`。