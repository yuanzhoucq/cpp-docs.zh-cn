---
title: "编译器错误 C2383 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2383
dev_langs:
- C++
helpviewer_keywords:
- C2383
ms.assetid: 6696221d-879c-477a-a0f3-a6edc15fd3d7
caps.latest.revision: 11
author: corob-msft
ms.author: corob
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
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: faa2aa2c29ea34009f0812a3796d450a6877ca48
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c2383"></a>编译器错误 C2383
*符号*︰ 默认自变量不能存在于此符号  
  
 C + + 编译器不允许在指向函数的指针上的默认自变量。  
  
 Visual Studio 2005 中之前, 的版本中的 Visual c + + 编译器接受此代码，但现在会导致错误。 对于适用于所有版本的 Visual c + + 的代码，现在将默认值分配给指针到函数参数。  
  
## <a name="example"></a>示例  
 下面的示例生成 C2383，并显示可能的解决方法︰  
  
```cpp  
// C2383.cpp  
// compile with: /c   
void (*pf)(int = 0);   // C2383  
void (*pf)(int);   // OK  
```
