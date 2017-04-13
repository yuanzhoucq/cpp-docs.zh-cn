---
title: "编译器警告 （等级 4） C4816 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4816
dev_langs:
- C++
helpviewer_keywords:
- C4816
ms.assetid: 60f730ae-d942-4db9-ab97-41d4a874d8da
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: a9df011e42a1c978deac1dbd3050c99b065e3567
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-4-c4816"></a>编译器警告（等级 4）C4816
“param”：参数具有一个大小为零的数组，该数组将被截断（除非该对象通过引用传递）  
  
 具有大小为零的数组的对象的参数不是按引用传递的。 传递对象时，不会复制该数组。  
  
## <a name="example"></a>示例  
 以下示例生成 C4816：  
  
```  
// C4816.cpp  
// compile with: /W4  
#include <stdio.h>  
  
extern "C" int printf_s(const char *, ...);  
  
#pragma warning(disable : 4200)  
  
struct S1  
{  
    int i;  
    char cArr[];  
};  
  
void TestErr(S1 s1)   // C4816 param with zero-array   
                      // not passed by reference  
{  
    printf_s("%d %c %c\n", s1.i, s1.cArr[0], s1.cArr[1]);  
}  
  
void TestOk(S1 &s1)  
{  
    printf_s("%d %c %c\n", s1.i, s1.cArr[0], s1.cArr[1]);  
}  
  
int main()  
{  
    S1 myS_1 = { 6, 'a', 'b', 'c' };  
    TestErr(myS_1);  
    TestOk(myS_1);  
}  
```
