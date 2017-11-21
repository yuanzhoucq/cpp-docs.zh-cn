---
title: "编译器警告 （等级 1） C4526 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4526
dev_langs: C++
helpviewer_keywords: C4526
ms.assetid: 490f8916-5fdc-4cad-b412-76c3382a5976
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 00ffa9e20781d8d5d1405d6bf5546b47a6530b88
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4526"></a>编译器警告（等级 1）C4526
function： 静态成员函数不能重写虚函数虚拟 function'override 忽略，将隐藏虚函数  
  
 静态成员函数满足要重写虚函数，这使得虚拟和静态成员函数的条件。  
  
 下面的代码生成 C4526:  
  
```  
// C4526.cpp  
// compile with: /W1 /c  
// C4526 expected  
struct myStruct1 {  
   virtual void __stdcall func( int ) = 0;  
};  
  
struct myStruct2: public myStruct1 {  
   static void __stdcall func( int );  
};  
```  
  
 以下是可能的修复方法：  
  
-   如果该函数用于重写基类的虚函数，则移除静态说明符。  
  
-   如果该函数本来就是静态成员函数，重命名它，以便它不会冲突与基类虚函数。