---
title: "位域的存储 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 4816a241-1580-4d1c-82ed-13d359733959
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 位域的存储
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**ANSI 3.5.2.1** int 内的位域的分配顺序  
  
 在整数中按照从最高有效位到最低有效位的顺序来分配位域。  在以下代码中  
  
```  
struct mybitfields  
{  
   unsigned a : 4;  
   unsigned b : 5;  
   unsigned c : 7;  
} test;  
  
int main( void )  
{  
   test.a = 2;  
   test.b = 31;  
   test.c = 0;  
}  
```  
  
 这些位将按如下所示排列：  
  
```  
00000001 11110010  
cccccccb bbbbaaaa  
```  
  
 由于 80x86 处理器将整数值的低字节存储在高字节之前，因此上面的整数 0x01F2 将按 0xF2 后跟 0x01 的形式存储在物理内存中。  
  
## 请参阅  
 [结构、联合、枚举和位域](../c-language/structures-unions-enumerations-and-bit-fields.md)