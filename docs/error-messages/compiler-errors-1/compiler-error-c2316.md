---
title: 编译器错误 C2316
ms.date: 07/08/2019
f1_keywords:
- C2316
helpviewer_keywords:
- C2316
ms.assetid: 9ad08eb5-060b-4eb0-8d66-0dc134f7bf67
ms.openlocfilehash: 5a3d9052775a5e1cbedfd58ccaaf0ff039a8475d
ms.sourcegitcommit: 07b34ca1c1fecced9fadc95de15dc5fee4f31e5a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2019
ms.locfileid: "67693448"
---
# <a name="compiler-error-c2316"></a>编译器错误 C2316

> '*class_type*： 不能被捕获，因为析构函数和/或复制构造函数是不可访问或已删除

捕获一个异常。 通过值或引用，但复制构造函数、 赋值运算符，或它们都是不可访问。

## <a name="remarks"></a>备注

在 Visual Studio 2015 的符合性更改所做的适用于派生自 MFC 异常的错误的 catch 语句，此错误`CException`。 因为`CException`具有继承的私有复制构造函数，类和及其派生类不是可复制，并且不能传递值，这还意味着无法通过值捕获它们。 Catch 按以前会导致在运行时未捕获的异常的值捕获 MFC 异常的语句。 现在，编译器正确指明这种情况下，并报告错误 C2316。 若要解决此问题，我们建议使用 MFC TRY/CATCH 宏，而不是编写您自己的异常处理程序。 如果不是适用于你的代码，捕获 MFC 异常由引用改为。

## <a name="example"></a>示例

下面的示例生成 C2316，并显示了如何修复此错误：

```cpp
// C2316.cpp
// compile with: /EHsc
#include <stdio.h>

struct B
{
public:
    B() {}
    // Delete the following line to resolve.
private:
    // copy constructor
    B(const B&) {}
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
    catch (B b)    // C2316
    {
        printf_s("Caught an exception!\n");
    }
}
```
