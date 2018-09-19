---
title: 编译器错误 C2316 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2316
dev_langs:
- C++
helpviewer_keywords:
- C2316
ms.assetid: 9ad08eb5-060b-4eb0-8d66-0dc134f7bf67
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2868d3a81fcbc94d8b20adcdc775363eb0a8eaeb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033012"
---
# <a name="compiler-error-c2316"></a>编译器错误 C2316

> '*异常*： 不能被捕获，因为析构函数和/或复制构造函数不可访问

通过值或引用捕获了异常，但复制构造函数和/或赋值运算符无法访问。

此代码的 Visual Studio 2003 中之前, 的 Visual c + + 版本接受，但现在会导致错误。

在 Visual Studio 2015 的符合性更改所做的适用于派生自 MFC 异常的错误的 catch 语句，此错误`CException`。 因为`CException`具有继承的私有复制构造函数，类和其派生类是不可复制和值，这也意味着他们不能按值捕获不能传递。 Catch 语句以前会导致在运行时，未捕获的异常的值由捕获 MFC 异常，但现在编译器正确地标识此情形以及报表错误 C2316。 若要解决此问题，我们建议而不是编写自己的异常的处理程序，但如果不是适用于你的代码，捕获 MFC 异常由引用改为使用 MFC TRY/CATCH 宏。

## <a name="example"></a>示例

下面的示例生成 C2316：

```
// C2316.cpp
// compile with: /EHsc
#include <stdio.h>

extern "C" int printf_s(const char*, ...);

struct B
{
public:
    B() {}
    // Delete the following line to resolve.
private:
    // copy constructor
    B(const B&)
    {
    }
};

void f(const B&)
{
}

int main()
{
    try
    {
        B aB;
        f(aB);
    }
    catch (B b) {   // C2316
        printf_s("Caught an exception!\n");
    }
}
```