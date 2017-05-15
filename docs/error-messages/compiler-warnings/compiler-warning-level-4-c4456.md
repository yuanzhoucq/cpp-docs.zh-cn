---
title: "编译器警告 （等级 4） C4456 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4456
dev_langs:
- C++
helpviewer_keywords:
- C4456
ms.assetid: 5ab39fc1-0e19-461b-842b-4da80560b044
caps.latest.revision: 0
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 128bd124c2536d86c8b673b54abc4b5505526b41
ms.openlocfilehash: 8698c9a430a79bbec1f6e82b8ac58067317c59a1
ms.contentlocale: zh-cn
ms.lasthandoff: 05/10/2017

---
# <a name="compiler-warning-level-4-c4456"></a>编译器警告 （等级 4） C4456
  
> 声明*标识符*隐藏了以前本地声明
  
声明*标识符*在本地作用域中隐藏具有相同名称的以前的本地声明的声明。 此警告，告知你引用到*标识符*在本地作用域中解析为本地声明的版本中，不以前本地，这可能也可能不是你的意图。 若要解决此问题，我们建议你提供与其他本地名称不会发生冲突的本地变量名称。  
    
## <a name="example"></a>示例
  
下面的示例生成 C4456，因为循环控制变量`int x`和本地变量`double x`中`member_fn`具有相同的名称。 若要解决此问题，请使用不同的本地变量的名称。  
  
```cpp  
// C4456_hide.cpp
// compile with: cl /W4 /c C4456_hide.cpp

struct S {
    void member_fn(unsigned u) {
        double x = 0;
        for (int x = 0; x < 10; ++x) {  // C4456
            u += x; // uses local int x
        } 
        x += u; // uses local double x
    }
} s;
```  

