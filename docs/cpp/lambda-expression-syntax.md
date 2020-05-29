---
title: Lambda 表达式语法
ms.date: 05/07/2019
helpviewer_keywords:
- lambda expressions [C++], syntax
ms.assetid: 5d6154a4-f34d-4a15-970d-7e7de45f54e9
ms.openlocfilehash: 9ac2fdea1a8fc8dcf2b03059455c3141daf86aa8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179648"
---
# <a name="lambda-expression-syntax"></a>Lambda 表达式语法

本文演示了 lambda 表达式的语法和结构化元素。 有关 lambda 表达式的说明，请参阅[Lambda 表达式](../cpp/lambda-expressions-in-cpp.md)。

## <a name="function-objects-vs-lambdas"></a>函数对象与 lambda

编写代码时，您可能会使用函数指针和函数对象来解决问题和执行计算，尤其是在使用[ C++标准库算法](../cpp/algorithms-modern-cpp.md)时。 函数指针和函数对象各有利弊。例如，函数指针具有最低的语法开销，但不保持范围内的状态，函数对象可保持状态，但需要类定义的语法开销。

lambda 结合了函数指针和函数对象的优点并避免其缺点。 lambda 与函数对象相似的是灵活并且可以保持状态，但不同的是其简洁的语法不需要显式类定义。 使用 lambda，你可以编写出比等效的函数对象代码更简洁、更不容易出错的代码。

以下示例将比较 lambda 的用途和函数对象的用途。 第一个示例使用 lambda 向控制台打印 `vector` 对象中的每个元素是偶数还是奇数。 第二个示例使用函数对象来完成相同任务。

## <a name="example-1-using-a-lambda"></a>示例 1：使用 lambda

此示例将 lambda 传递到**for_each**函数。 该 lambda 打印一个结果，该结果指出 `vector` 对象中的每个元素是偶数还是奇数。

### <a name="code"></a>代码

```cpp
// even_lambda.cpp
// compile with: cl /EHsc /nologo /W4 /MTd
#include <algorithm>
#include <iostream>
#include <vector>
using namespace std;

int main()
{
   // Create a vector object that contains 9 elements.
   vector<int> v;
   for (int i = 1; i < 10; ++i) {
      v.push_back(i);
   }

   // Count the number of even numbers in the vector by
   // using the for_each function and a lambda.
   int evenCount = 0;
   for_each(v.begin(), v.end(), [&evenCount] (int n) {
      cout << n;
      if (n % 2 == 0) {
         cout << " is even " << endl;
         ++evenCount;
      } else {
         cout << " is odd " << endl;
      }
   });

   // Print the count of even numbers to the console.
   cout << "There are " << evenCount
        << " even numbers in the vector." << endl;
}
```

```Output
1 is odd
2 is even
3 is odd
4 is even
5 is odd
6 is even
7 is odd
8 is even
9 is odd
There are 4 even numbers in the vector.
```

### <a name="comments"></a>注释

在此示例中， **for_each**函数的第三个参数是 lambda。 `[&evenCount]` 部分指定表达式的捕获子句，`(int n)` 指定参数列表，剩余部分指定表达式的主体。

## <a name="example-2-using-a-function-object"></a>示例 2：使用函数对象

有时 lambda 过于庞大，无法在上一示例的基础上大幅度扩展。 下一个示例将函数对象（而不是 lambda）与**for_each**函数一起使用，以生成与示例1相同的结果。 两个示例都在 `vector` 对象中存储偶数的个数。 为保持运算的状态，`FunctorClass` 类通过引用存储 `m_evenCount` 变量作为成员变量。 若要执行该操作，`FunctorClass` 实现函数调用运算符 **（）** 。 Microsoft C++编译器生成的代码可与示例1中的 lambda 代码大小和性能相当。 对于类似本文中示例的基本问题，较为简单的 lambda 设计可能优于函数对象设计。 但是，如果你认为该功能在将来可能需要重大扩展，则使用函数对象设计，这样代码维护会更简单。

有关**运算符（）** 的详细信息，请参阅[函数调用](../cpp/function-call-cpp.md)。 有关**for_each**函数的详细信息，请参阅[for_each](../standard-library/algorithm-functions.md#for_each)。

### <a name="code"></a>代码

```cpp
// even_functor.cpp
// compile with: /EHsc
#include <algorithm>
#include <iostream>
#include <vector>
using namespace std;

class FunctorClass
{
public:
    // The required constructor for this example.
    explicit FunctorClass(int& evenCount)
        : m_evenCount(evenCount) { }

    // The function-call operator prints whether the number is
    // even or odd. If the number is even, this method updates
    // the counter.
    void operator()(int n) const {
        cout << n;

        if (n % 2 == 0) {
            cout << " is even " << endl;
            ++m_evenCount;
        } else {
            cout << " is odd " << endl;
        }
    }

private:
    // Default assignment operator to silence warning C4512.
    FunctorClass& operator=(const FunctorClass&);

    int& m_evenCount; // the number of even variables in the vector.
};

int main()
{
    // Create a vector object that contains 9 elements.
    vector<int> v;
    for (int i = 1; i < 10; ++i) {
        v.push_back(i);
    }

    // Count the number of even numbers in the vector by
    // using the for_each function and a function object.
    int evenCount = 0;
    for_each(v.begin(), v.end(), FunctorClass(evenCount));

    // Print the count of even numbers to the console.
    cout << "There are " << evenCount
        << " even numbers in the vector." << endl;
}
```

```Output
1 is odd
2 is even
3 is odd
4 is even
5 is odd
6 is even
7 is odd
8 is even
9 is odd
There are 4 even numbers in the vector.
```

## <a name="see-also"></a>另请参阅

[Lambda 表达式](../cpp/lambda-expressions-in-cpp.md)<br/>
[Lambda 表达式的示例](../cpp/examples-of-lambda-expressions.md)<br/>
[generate](../standard-library/algorithm-functions.md#generate)<br/>
[generate_n](../standard-library/algorithm-functions.md#generate_n)<br/>
[for_each](../standard-library/algorithm-functions.md#for_each)<br/>
[异常规范 (throw)](../cpp/exception-specifications-throw-cpp.md)<br/>
[编译器警告（等级 1）C4297](../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md)<br/>
[Microsoft 专用的修饰符](../cpp/microsoft-specific-modifiers.md)
