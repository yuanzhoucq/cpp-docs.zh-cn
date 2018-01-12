---
title: "编译器警告 （等级 4） C4457 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4457
dev_langs: C++
helpviewer_keywords: C4457
ms.assetid: 02fd149a-917d-4f67-97a6-eb714572271f
caps.latest.revision: "0"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 77965ba08b311768b54788692d3f5b7fa724f5b8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4457"></a>编译器警告 （等级 4） C4457
  
> 声明*标识符*隐藏函数参数
  
声明*标识符*在本地作用域中隐藏相同名为函数参数的声明。 此警告，告知你引用到*标识符*在本地作用域中解析为本地声明的版本中，不使用参数可能会也可能不是你的意图。 若要解决此问题，我们建议你提供与参数名称不会发生冲突的本地变量名称。  
    
## <a name="example"></a>示例
  
下面的示例生成 C4457，因为参数`x`和本地变量`x`中`member_fn`具有相同的名称。 若要解决此问题，请使用不同的参数和局部变量名称。  
  
```cpp  
// C4457_hide.cpp
// compile with: cl /W4 /c C4457_hide.cpp

struct S {
    void member_fn(unsigned x) {
        double a = 0;
        for (int x = 0; x < 10; ++x) {  // C4457
            a += x; // uses local x
        } 
        a += x; // uses parameter x
    }
} s;
```  
