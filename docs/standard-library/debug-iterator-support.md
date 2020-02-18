---
title: 调试迭代器支持
ms.date: 09/13/2018
helpviewer_keywords:
- Safe Libraries
- Safe Libraries, C++ Standard Library
- Safe C++ Standard Library
- C++ Standard Library, debug iterator support
- iterators, debug iterator support
- iterators, incompatible
- incompatible iterators
- debug iterator support
ms.assetid: f3f5bd15-4be8-4d64-a4d0-8bc0761c68b6
ms.openlocfilehash: f43367fd58d8ab2a62fb2312efcd9fc9ec0cfc42
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416202"
---
# <a name="debug-iterator-support"></a>调试迭代器支持

Visual c + + 运行库检测到不正确使用的迭代器，并在运行时断言和显示一个对话框。 若要启用调试迭代器支持，必须使用 c + + 标准库和 C 运行库的调试版本来编译你的程序。 有关详细信息，请参阅 [ CRT 库功能](../c-runtime-library/crt-library-features.md)。 有关如何使用经过检查的迭代器的信息，请参阅[经过检查的迭代器](../standard-library/checked-iterators.md)。

C++ 标准描述了成员函数可能会如何导致一个容器的迭代器无效。 两个示例包括：

- 擦除容器中的元素会导致该元素的迭代器无效。

- 通过使用推送或插入增加[向量](../standard-library/vector.md)的大小会导致进入 `vector` 的迭代器无效。

## <a name="invalid-iterators"></a>迭代器无效

如果在调试模式下编译此示例程序，则在运行时它将断言并终止。

```cpp
// iterator_debugging_0.cpp
// compile by using /EHsc /MDd
#include <vector>
#include <iostream>

int main() {
   std::vector<int> v {10, 15, 20};
   std::vector<int>::iterator i = v.begin();
   ++i;

   std::vector<int>::iterator j = v.end();
   --j;

   std::cout << *j << '\n';

   v.insert(i,25);

   std::cout << *j << '\n'; // Using an old iterator after an insert
}
```

## <a name="using-_iterator_debug_level"></a>使用 _ITERATOR_DEBUG_LEVEL

可以使用预处理器宏 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) 关闭调试版本中迭代器的调试功能。 此程序不会断言，但仍会触发未定义的行为。

```cpp
// iterator_debugging_1.cpp
// compile by using: /EHsc /MDd
#define _ITERATOR_DEBUG_LEVEL 0
#include <vector>
#include <iostream>

int main() {
    std::vector<int> v {10, 15, 20};

   std::vector<int>::iterator i = v.begin();
   ++i;

   std::vector<int>::iterator j = v.end();
   --j;

   std::cout << *j << '\n';

   v.insert(i,25);

   std::cout << *j << '\n'; // Using an old iterator after an insert
}
```

```Output
20
-572662307
```

## <a name="unitialized-iterators"></a>未初始化迭代器

如果在初始化之前尝试使用迭代器，断言也会发生，如下所示：

```cpp
// iterator_debugging_2.cpp
// compile by using: /EHsc /MDd
#include <string>
using namespace std;

int main() {
   string::iterator i1, i2;
   if (i1 == i2)
      ;
}
```

## <a name="incompatible-iterators"></a>迭代器不兼容

下面的代码示例引发断言，因为指向 [for_each](../standard-library/algorithm-functions.md#for_each) 算法的两个迭代器不兼容。 算法会执行检查以确定提供给它们的迭代器是否引用相同的容器。

```cpp
// iterator_debugging_3.cpp
// compile by using /EHsc /MDd
#include <algorithm>
#include <vector>
using namespace std;

int main()
{
    vector<int> v1 {10, 20};
    vector<int> v2 {10, 20};

    // The next line asserts because v1 and v2 are
    // incompatible.
    for_each(v1.begin(), v2.end(), [] (int& elem) { elem *= 2; } );
}
```

请注意，本示例使用 lambda 表达式 `[] (int& elem) { elem *= 2; }` 而不是某个函数。 虽然此选项对于断言失败没有任何影响 - 类似函数会导致相同的故障，lambda 是完成 compact 函数对象任务非常有用的方式。 有关 lambda 表达式的详细信息，请参阅 [Lambda 表达式](../cpp/lambda-expressions-in-cpp.md)。

## <a name="iterators-going-out-of-scope"></a>迭代器超出范围

调试迭代器检查还会导致在**for**循环中声明的迭代器变量在**for**循环范围结束时超出范围。

```cpp
// iterator_debugging_4.cpp
// compile by using: /EHsc /MDd
#include <vector>
#include <iostream>
int main() {
   std::vector<int> v {10, 15, 20};

   for (std::vector<int>::iterator i = v.begin(); i != v.end(); ++i)
      ;   // do nothing
   --i;   // C2065
}
```

## <a name="destructors-for-debug-iterators"></a>调试迭代器的析构函数

调试迭代器具有不平常的析构函数。 如果析构函数未运行，但对象的内存被释放，则可能会发生访问冲突和数据损坏。 请看以下示例：

```cpp
// iterator_debugging_5.cpp
// compile by using: /EHsc /MDd
#include <vector>
struct base {
   // TO FIX: uncomment the next line
   // virtual ~base() {}
};

struct derived : base {
   std::vector<int>::iterator m_iter;
   derived( std::vector<int>::iterator iter ) : m_iter( iter ) {}
   ~derived() {}
};

int main() {
   std::vector<int> vect( 10 );
   base * pb = new derived( vect.begin() );
   delete pb;  // doesn't call ~derived()
   // access violation
}
```

## <a name="see-also"></a>另请参阅

[C++ 标准库概述](../standard-library/cpp-standard-library-overview.md)
