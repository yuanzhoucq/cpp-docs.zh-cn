---
title: 编译器警告 （等级 4） C4456 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4456
dev_langs:
- C++
helpviewer_keywords:
- C4456
ms.assetid: 5ab39fc1-0e19-461b-842b-4da80560b044
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2ca4af4e7353595dc687b77fa87acf70861bcb6f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33295907"
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
