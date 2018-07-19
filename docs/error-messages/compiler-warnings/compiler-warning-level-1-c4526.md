---
title: 编译器警告 （等级 1） C4526 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4526
dev_langs:
- C++
helpviewer_keywords:
- C4526
ms.assetid: 490f8916-5fdc-4cad-b412-76c3382a5976
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5a38d629d61e16b038701522d4bb27a4de7391d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33282894"
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