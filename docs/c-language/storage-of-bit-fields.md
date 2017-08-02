---
title: "位域的存储 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 4816a241-1580-4d1c-82ed-13d359733959
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: b0e25945ff20adcccce060363601cfc1a1a1f6fd
ms.contentlocale: zh-cn
ms.lasthandoff: 05/18/2017

---
# <a name="storage-of-bit-fields"></a>位域的存储
**ANSI 3.5.2.1** int 内的位域的分配顺序  
  
 在整数中按照从最高有效位到最低有效位的顺序来分配位域。 在以下代码中  
  
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
  
## <a name="see-also"></a>另请参阅  
 [结构、联合、枚举和位域](../c-language/structures-unions-enumerations-and-bit-fields.md)
