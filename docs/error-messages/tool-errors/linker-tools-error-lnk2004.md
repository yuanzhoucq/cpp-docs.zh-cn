---
title: 链接器工具错误 LNK2004 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2004
dev_langs:
- C++
helpviewer_keywords:
- LNK2004
ms.assetid: 07645371-e67b-4a2c-b0e0-dde24c94ef7e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2619ebc3fcf997574628354a951619cd18a81b46
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33314335"
---
# <a name="linker-tools-error-lnk2004"></a>链接器工具错误 LNK2004
gp 相对修正溢出目标;较短的节节是太大或超出范围。  
  
 部分了过大。  
  
 若要解决此错误，减小的较短的节中，通过显式将数据放入 #pragma 部分 （".sectionname"，以读取、 写入、 long 类型的值） 通过较长的部分，并使用大小`__declspec(allocate(".sectionname"))`上数据定义和声明。  例如，应用于对象的  
  
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
  
 此外可以将逻辑分组的数据移到自己结构，它将大于 8 个字节，编译器将分配长 data 节中的数据的集合。  例如，应用于对象的  
  
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
  
 此错误后跟错误`LNK1165`。