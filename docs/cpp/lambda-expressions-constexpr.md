---
title: constexpr C++ 中的 Lambda 表达式 |Microsoft 文档
ms.custom: ''
ms.date: 07/19/2017
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- lambda expressions [C++], constexpr
ms.assetid: b56346cd-fbff-475f-aeaa-ed2010c6d6f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b78fa3de7777ffc6702902cf967a405595caf12f
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408198"
---
# <a name="constexpr-lambda-expressions-in-c"></a>constexpr C++ 中的 Lambda 表达式
**Visual Studio 2017 版本 15.3 及更高版本**(适用于[/std: c + + 17](../build/reference/std-specify-language-standard-version.md)): 可能作为声明的 lambda 表达式**constexpr**或固定表达式中使用时的每个初始化常量表达式中允许包含它捕获或引入的数据成员。  

```cpp
    int y = 32;
    auto answer = [y]() constexpr 
    {
        int x = 10;
        return y + x; 
    };

    constexpr int Increment(int n) 
    {
        return [n] { return n + 1; }();
    }
``` 
Lambda 是隐式**constexpr**如果其结果满足的要求**constexpr**函数：
```cpp
    auto answer = [](int n) 
    {
        return 32 + n; 
    };

    constexpr int response = answer(10);
``` 
如果 lambda 是隐式或显式**constexpr**，并将其转换为函数指针，生成的函数也是**constexpr**:

```cpp
    auto Increment = [](int n)
    {
        return n + 1;
    };

    constexpr int(*inc)(int) = Increment;
```
  
## <a name="see-also"></a>请参阅  
 [C++ 语言参考](../cpp/cpp-language-reference.md)   
 [C++ 标准库中的函数对象](../standard-library/function-objects-in-the-stl.md)   
 [函数调用](../cpp/function-call-cpp.md)   
 [for_each](../standard-library/algorithm-functions.md#for_each)