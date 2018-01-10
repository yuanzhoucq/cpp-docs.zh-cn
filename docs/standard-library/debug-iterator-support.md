---
title: "调试迭代器支持 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ea016877744bed8e91f8e7144560969b2dbca745
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="debug-iterator-support"></a>Debug Iterator Support
Visual c + + 运行库检测到不正确使用的迭代器，并在运行时断言和显示一个对话框。 若要启用调试迭代器支持，必须使用 c + + 标准库和 C 运行库的调试版本来编译你的程序。 有关详细信息，请参阅 [ CRT 库功能](../c-runtime-library/crt-library-features.md)。 有关如何使用经过检查的迭代器的信息，请参阅[经过检查的迭代器](../standard-library/checked-iterators.md)。  
  
 C++ 标准描述了成员函数可能会如何导致一个容器的迭代器无效。 两个示例包括：  
  
-   擦除容器中的元素会导致该元素的迭代器无效。  
  
-   通过使用推送或插入增加[向量](../standard-library/vector.md)的大小会导致进入 `vector` 的迭代器无效。  
  
## <a name="example"></a>示例  
如果在调试模式下编译此示例程序，则在运行时它将断言并终止。  
  
```cpp  
// iterator_debugging_0.cpp  
// compile by using /EHsc /MDd  
#include <vector>  
#include <iostream>  
  
int main() {  
   std::vector<int> v ;  
  
   v.push_back(10);  
   v.push_back(15);  
   v.push_back(20);  
  
   std::vector<int>::iterator i = v.begin();  
   ++i;  
  
   std::vector<int>::iterator j = v.end();  
   --j;  
  
   std::cout << *j << '\n';  
  
   v.insert(i,25);   
  
   std::cout << *j << '\n'; // Using an old iterator after an insert  
}  
```  
  
## <a name="example"></a>示例  
可以使用预处理器宏 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) 关闭调试版本中迭代器的调试功能。 此程序不会断言，但仍会触发未定义的行为。  
  
```cpp  
// iterator_debugging_1.cpp  
// compile by using: /EHsc /MDd  
#define _ITERATOR_DEBUG_LEVEL 0  
#include <vector>  
#include <iostream>  
  
int main() {  
   std::vector<int> v ;  
  
   v.push_back(10);  
   v.push_back(15);  
   v.push_back(20);  
  
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
  
## <a name="example"></a>示例  
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
  
## <a name="example"></a>示例  
下面的代码示例引发断言，因为指向 [for_each](../standard-library/algorithm-functions.md#for_each) 算法的两个迭代器不兼容。 算法会执行检查以确定提供给它们的迭代器是否引用相同的容器。  
  
```cpp  
// iterator_debugging_3.cpp  
// compile by using /EHsc /MDd  
#include <algorithm>  
#include <vector>  
using namespace std;  
  
int main()  
{  
    vector<int> v1;  
    vector<int> v2;  
  
    v1.push_back(10);  
    v1.push_back(20);  
  
    v2.push_back(10);  
    v2.push_back(20);  
  
    // The next line asserts because v1 and v2 are  
    // incompatible.  
    for_each(v1.begin(), v2.end(), [] (int& elem) { elem *= 2; } );  
}  
```  
  
请注意，本示例使用 lambda 表达式 `[] (int& elem) { elem *= 2; }` 而不是某个函数。 虽然此选项对于断言失败没有任何影响 - 类似函数会导致相同的故障，lambda 是完成 compact 函数对象任务非常有用的方式。 有关 lambda 表达式的详细信息，请参阅 [Lambda 表达式](../cpp/lambda-expressions-in-cpp.md)。  
  
## <a name="example"></a>示例  
当 `for` 循环作用域结束时，调试迭代器检查也会导致 `for` 循环中声明的迭代器变量超出范围。  
  
```cpp  
// iterator_debugging_4.cpp  
// compile by using: /EHsc /MDd  
#include <vector>  
#include <iostream>  
int main() {  
   std::vector<int> v ;  
  
   v.push_back(10);  
   v.push_back(15);  
   v.push_back(20);  
  
   for (std::vector<int>::iterator i = v.begin(); i != v.end(); ++i)  
      ;   // do nothing  
   --i;   // C2065  
}  
```  
  
## <a name="example"></a>示例  
调试迭代器具有不平常的析构函数。 如果析构函数不能运行，无论什么原因，可能发生访问冲突和数据损坏。 请看以下示例：  
  
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
  
## <a name="see-also"></a>请参阅  
[C++ 标准库概述](../standard-library/cpp-standard-library-overview.md)




