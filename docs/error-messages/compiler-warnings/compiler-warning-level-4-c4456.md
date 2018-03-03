---
title: "编译器警告 （等级 4） C4456 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4456
dev_langs:
- C++
helpviewer_keywords:
- C4456
ms.assetid: 5ab39fc1-0e19-461b-842b-4da80560b044
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9e298f092f546c589606be42b6e7b9faed15ddd4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
