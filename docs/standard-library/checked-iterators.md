---
title: "已检查的迭代器 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _SECURE_SCL_THROWS
dev_langs: C++
helpviewer_keywords:
- Safe Libraries
- Safe Libraries, C++ Standard Library
- Safe C++ Standard Library
- iterators, checked
- checked iterators
ms.assetid: cfc87df8-e3d9-403b-ab78-e9483247d940
caps.latest.revision: "30"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bbd902066e86d2dbe04e4bc709a1042c40dffe8d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="checked-iterators"></a>Checked Iterators
检查迭代器可确保容器的边界不会被覆盖。 检查迭代器应用于发布版本和调试版本。 有关如何在调试模式下进行编译时使用调试迭代器的详细信息，请参阅[调试迭代器支持](../standard-library/debug-iterator-support.md)。  
  
## <a name="remarks"></a>备注  
有关如何禁止检查迭代器生成警告的信息，请参阅 [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md)。  
  
可以使用 [\_ITERATOR\_DEBUG\_LEVEL](../standard-library/iterator-debug-level.md) 预处理器宏启用或禁用已检查的迭代器功能。 如果将 `_ITERATOR_DEBUG_LEVEL` 定义为 1 或 2，则不安全地使用迭代器时会导致运行时错误，并且程序将会终止。 如果定义为 0，则会禁用检查迭代器。 默认情况下，对于发布版本，`_ITERATOR_DEBUG_LEVEL` 的值为 0，而对于调试版本则为 2。  
  
> [!IMPORTANT]
> 较旧的文档和源代码可参考 [_SECURE_SCL](../standard-library/secure-scl.md) 宏。 使用 `_ITERATOR_DEBUG_LEVEL` 可控制 `_SECURE_SCL`。 有关详细信息，请参阅 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)。  
  
当 `_ITERATOR_DEBUG_LEVEL` 定义为 1 或 2，将执行以下迭代器检查：  
  
-   所有标准迭代器（例如，[vector::iterator](../standard-library/vector-class.md#iterator)）都会进行检查。  
  
-   如果输出迭代器是经检查的迭代器，则调用标准库函数（如 [std:: copy](../standard-library/algorithm-functions.md#copy)）将获得检查的行为。  
  
-   如果输出迭代器是未检查的迭代器，则调用标准库函数时将导致编译器警告。  
  
-   如果存在超出容器边界的访问，则以下函数将产生运行时错误：  
  
|||||  
|-|-|-|-|  
|[basic_string::operator\[\]](../standard-library/basic-string-class.md#op_at)|[bitset::operator\[\]](../standard-library/bitset-class.md#op_at)|[back](../standard-library/deque-class.md#back)|[front](../standard-library/deque-class.md#front)|  
|[deque::operator\[\]](../standard-library/deque-class.md#op_at)|[back](../standard-library/list-class.md#back)|[front](../standard-library/list-class.md#front)|[back](../standard-library/queue-class.md#back)|  
|[front](../standard-library/queue-class.md#front)|[vector::operator\[\]](../standard-library/vector-class.md#op_at)|[back](../standard-library/vector-class.md#back)|[front](../standard-library/vector-class.md#front)|  
  
当 `_ITERATOR_DEBUG_LEVEL` 定义为 0 时：  
  
-   所有标准迭代器均未检查。 迭代器可以移动到容器边界之外，从而导致未定义的行为。  
  
-   如果输出迭代器是经检查的迭代器，则调用标准库函数（如 `std::copy`）将获得检查的行为。  
  
-   如果输出迭代器是未经检查的迭代器，则调用标准库函数将获得检查的行为。  
  
检查迭代器是指，当尝试移动到容器边界之外时，会调用 `invalid_parameter_handler` 的迭代器。 有关 `invalid_parameter_handler` 的详细信息，请参阅[参数验证](../c-runtime-library/parameter-validation.md)。  
  
支持经检查的迭代器的迭代器适配器为 [checked_array_iterator 类](../standard-library/checked-array-iterator-class.md)和 [unchecked_array_iterator 类](../standard-library/unchecked-array-iterator-class.md)。  
  
## <a name="example"></a>示例  
  
使用设置为 1 或 2 的 `_ITERATOR_DEBUG_LEVEL` 进行编译时，如果试图通过使用某些类的索引运算符来访问位于容器边界之外的元素，将会发生运行时错误。  
  
```cpp  
// checked_iterators_1.cpp  
// cl.exe /Zi /MDd /EHsc /W4  
  
#define _ITERATOR_DEBUG_LEVEL 1  
  
#include <vector>  
#include <iostream>  
  
using namespace std;  
  
int main()  
{  
   vector<int> v;  
   v.push_back(67);  
  
   int i = v[0];  
   cout << i << endl;  
  
   i = v[1]; //triggers invalid parameter handler  
}  
```  
  
此程序将输出“67”然后弹出一个断言失败对话框，其中包含与失败有关的附加信息。  
  
## <a name="example"></a>示例  
  
同样，使用设置为 1 或 2 的 `_ITERATOR_DEBUG_LEVEL` 进行编译时，如果试图通过使用 `front` 或容器类中的 `back` 来访问某一元素（当容器为空时），将会发生运行时错误。  
  
```cpp  
// checked_iterators_2.cpp  
// cl.exe /Zi /MDd /EHsc /W4  
#define _ITERATOR_DEBUG_LEVEL 1  
  
#include <vector>  
#include <iostream>  
  
using namespace std;  
  
int main()  
{  
   vector<int> v;  
  
   int& i = v.front(); // triggers invalid parameter handler  
}  
```  
  
此程序将弹出一个断言失败对话框，其中包含与失败有关的附加信息。  
  
## <a name="example"></a>示例  
  
下面的代码演示各种迭代器使用情形，并提供各个情形的注释。 默认情况下，`_ITERATOR_DEBUG_LEVEL` 在调试版本中设置为 2，在零售版本中设置为 0。  
  
```cpp  
// checked_iterators_3.cpp  
// cl.exe /MTd /EHsc /W4  
  
#include <algorithm>  
#include <array>  
#include <iostream>  
#include <iterator>  
#include <numeric>  
#include <string>  
#include <vector>  
  
using namespace std;  
  
template <typename C> 
void print(const string& s, const C& c)  
{  
    cout << s;  
  
    for (const auto& e : c) {  
        cout << e << " ";  
    }  
  
    cout << endl;  
}  
  
int main()  
{  
    vector<int> v(16);  
    iota(v.begin(), v.end(), 0);  
    print("v: ", v);  
  
    // OK: vector::iterator is checked in debug mode  
    // (i.e. an overrun causes a debug assertion)  
    vector<int> v2(16);  
    transform(v.begin(), v.end(), v2.begin(), [](int n) { return n * 2; });  
    print("v2: ", v2);  
  
    // OK: back_insert_iterator is marked as checked in debug mode  
    // (i.e. an overrun is impossible)  
    vector<int> v3;  
    transform(v.begin(), v.end(), back_inserter(v3), [](int n) { return n * 3; });  
    print("v3: ", v3);  
  
    // OK: array::iterator is checked in debug mode  
    // (i.e. an overrun causes a debug assertion)  
    array<int, 16> a4;  
    transform(v.begin(), v.end(), a4.begin(), [](int n) { return n * 4; });  
    print("a4: ", a4);  
  
    // OK: Raw arrays are checked in debug mode  
    // (an overrun causes a debug assertion)  
    // NOTE: This applies only when raw arrays are given to C++ Standard Library algorithms!  
    int a5[16];  
    transform(v.begin(), v.end(), a5, [](int n) { return n * 5; });  
    print("a5: ", a5);  
  
    // WARNING C4996: Pointers cannot be checked in debug mode  
    // (an overrun causes undefined behavior)  
    int a6[16];  
    int * p6 = a6;  
    transform(v.begin(), v.end(), p6, [](int n) { return n * 6; });  
    print("a6: ", a6);  
  
    // OK: stdext::checked_array_iterator is checked in debug mode  
    // (an overrun causes a debug assertion)  
    int a7[16];  
    int * p7 = a7;  
    transform(v.begin(), v.end(), stdext::make_checked_array_iterator(p7, 16), [](int n) { return n * 7; });  
    print("a7: ", a7);  
  
    // WARNING SILENCED: stdext::unchecked_array_iterator is marked as checked in debug mode  
    // (it performs no checking, so an overrun causes undefined behavior)  
    int a8[16];  
    int * p8 = a8;  
    transform(v.begin(), v.end(), stdext::make_unchecked_array_iterator(p8), [](int n) { return n * 8; });  
    print("a8: ", a8);  
}  
  
```  
  
使用 `cl.exe /EHsc /W4 /MTd checked_iterators_3.cpp` 编译此代码时，编译器会发出警告，但编译成无错误的可执行文件：  
  
```Output  
algorithm(1026) : warning C4996: 'std::_Transform1': Function call with parameters 
that may be unsafe - this call relies on the caller to check that the passed values 
are correct. To disable this warning, use -D_SCL_SECURE_NO_WARNINGS. See documentation 
on how to use Visual C++ 'Checked Iterators'  
```  
  
在命令行运行时，可执行文件将生成以下输出：  
  
```Output  
v: 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15  
v2: 0 2 4 6 8 10 12 14 16 18 20 22 24 26 28 30  
v3: 0 3 6 9 12 15 18 21 24 27 30 33 36 39 42 45  
a4: 0 4 8 12 16 20 24 28 32 36 40 44 48 52 56 60  
a5: 0 5 10 15 20 25 30 35 40 45 50 55 60 65 70 75  
a6: 0 6 12 18 24 30 36 42 48 54 60 66 72 78 84 90  
a7: 0 7 14 21 28 35 42 49 56 63 70 77 84 91 98 105  
a8: 0 8 16 24 32 40 48 56 64 72 80 88 96 104 112 120  
```  
  
## <a name="see-also"></a>另请参阅  
 [C++ 标准库概述](../standard-library/cpp-standard-library-overview.md)   
 [调试迭代器支持](../standard-library/debug-iterator-support.md)

