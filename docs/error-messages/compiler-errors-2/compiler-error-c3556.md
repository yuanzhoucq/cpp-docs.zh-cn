---
title: "编译器错误 C3556 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3556
dev_langs: C++
helpviewer_keywords: C3556
ms.assetid: 9b002dcc-494e-414f-9587-20c2a0a39333
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4cff9466ff006f303913f52101db57708020ed8c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3556"></a>编译器错误 C3556
  
> *表达式*: decltype 的参数不正确  
  
编译器无法推导作为 `decltype(`*expression*`)` 类型说明符参数的表达式的类型。  
  
## <a name="example"></a>示例  
  
在下面的代码示例中，编译器无法推导 `myFunction` 参数的类型，因为 `myFunction` 会进行重载。 若要解决此问题，无法使用`static_cast`来创建一个指向特定实例重载函数中指定`decltype`表达式。  
  
```cpp  
// C3556.cpp
// compile with: cl /W4 /EHsc C3556.cpp
#include <iostream>

void myFunction(int);  
void myFunction(float, float); 

void callsMyFunction(decltype(myFunction) fn); // C3556
// One way to fix is to comment out the line above, and
// use static_cast to create specialized function pointer 
// instances:
auto myFunctionInt = static_cast<void(*)(int)>(myFunction);
auto myFunctionFloatFloat = static_cast<void(*)(float,float)>(myFunction);
void callsMyFunction(decltype(myFunctionInt) fn, int n);
void callsMyFunction(decltype(myFunctionFloatFloat) fn, float f, float g);

void myFunction(int i) { 
    std::cout << "called myFunction(" << i << ")" << std::endl; 
} 

void myFunction(float f, float g) { 
    std::cout << "called myFunction(" << f << ", " << g << ")" << std::endl; 
}  

void callsMyFunction(decltype(myFunctionInt) fn, int n) {
    fn(n);
}

void callsMyFunction(decltype(myFunctionFloatFloat) fn, float f, float g) {
    fn(f, g);
}

int main() {
    callsMyFunction(myFunction, 42);
    callsMyFunction(myFunction, 0.1f, 2.3f);
}
```