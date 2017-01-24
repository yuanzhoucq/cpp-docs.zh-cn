---
title: "调试迭代器支持 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_HAS_ITERATOR_DEBUGGING symbol"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "调试迭代器支持"
  - "不兼容的迭代器"
  - "迭代器, 调试迭代器支持"
  - "迭代器, 不兼容的"
  - "安全库"
  - "安全库, 标准 C++ 库"
  - "安全标准 C++ 库"
  - "标准 C++ 库, 调试迭代器支持"
ms.assetid: f3f5bd15-4be8-4d64-a4d0-8bc0761c68b6
caps.latest.revision: 22
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 调试迭代器支持
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 运行库检测不正确迭代器，并使用断言和显示该对话框在运行时。  若要启用调试迭代器支持，必须使用 C. 运行库的调试版本编译程序。  有关详细信息，请参阅[CRT 库功能](../c-runtime-library/crt-library-features.md)。  有关如何使用该迭代器的信息，请参见 [经过检查的迭代器](../standard-library/checked-iterators.md)。  
  
 C\+\+ 标准描述成员函数如何使迭代器与容器变为无效。  两个示例是：  
  
-   取消从容器的一个元素使迭代器指向元素变为无效。  
  
-   增加的大小 \( [矢量](../standard-library/vector.md) 推送或插入\) 导致到迭代器的 `vector` 变为无效。  
  
## 示例  
 如果编译下面程序调试模式，在运行时则断言并终止。  
  
```cpp  
/* compile with /EHsc /MDd */  
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
  
   std::cout<<*j<<'\n';  
  
   v.insert(i,25);   
  
   std::cout<<*j<<'\n'; // Using an old iterator after an insert  
}  
  
```  
  
## 示例  
 您可以使用符号 [\_HAS\_ITERATOR\_DEBUGGING](../standard-library/has-iterator-debugging.md) 关闭在调试版本的迭代器在调试功能。  以下程序无法断言，触发，但仍未定义的行为。  
  
> [!IMPORTANT]
>  使用 `_ITERATOR_DEBUG_LEVEL` 控制 `_HAS_ITERATOR_DEBUGGING`。  有关详细信息，请参阅[\_ITERATOR\_DEBUG\_LEVEL](../standard-library/iterator-debug-level.md)。  
  
```cpp  
// iterator_debugging.cpp  
// compile with: /EHsc /MDd  
#define _HAS_ITERATOR_DEBUGGING 0  
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
  
   std::cout<<*j<<'\n';  
  
   v.insert(i,25);   
  
   std::cout<<*j<<'\n'; // Using an old iterator after an insert  
}  
```  
  
  **20**  
**\-572662307**   
## 示例  
 断言会发生，如果尝试使用迭代器，在初始化之前，如下所示：  
  
```cpp  
/* compile with /EHsc /MDd */  
#include <string>  
using namespace std;  
int main() {  
   string::iterator i1, i2;  
   if (i1 == i2)  
      ;  
}  
```  
  
## 示例  
 因为指向 [for\_each](../Topic/for_each.md) 算法的两个迭代器不兼容，下面的代码示例将导致断言。  检查算法确定提供给其迭代器是否引用同一个容器。  
  
```cpp  
/* compile with /EHsc /MDd */  
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
  
    // The next line will assert because v1 and v2 are  
    // incompatible.  
    for_each(v1.begin(), v2.end(), [] (int& elem) { elem *= 2; } );  
}  
```  
  
 请注意此示例使用 lambda 表达式 `[] (int& elem) { elem *= 2; }` 而不是 functor。  尽管此与选择无关断言失败的 functor 将生成相同的 lambda 失败是一种非常有用的方式完成压缩函数对象任务。  有关 lambda 表达式的更多信息，请参见 [lambda 表达式](../cpp/lambda-expressions-in-cpp.md)。  
  
## 示例  
 调试也将检查的迭代器在 `for` 声明导致循环超出范围的迭代器变量，在 `for` 循环范围的末尾。  
  
```cpp  
// debug_iterator.cpp  
// compile with: /EHsc /MDd  
#include <vector>  
#include <iostream>  
int main() {  
   std::vector<int> v ;  
  
   v.push_back(10);  
   v.push_back(15);  
   v.push_back(20);  
  
   for (std::vector<int>::iterator i = v.begin() ; i != v.end(); ++i)  
   ;  
   --i;   // C2065  
}  
```  
  
## 示例  
 调试迭代器有重要的析构函数。  如果析构函数不运行，无论出于什么原因，访问冲突和数据损坏可能发生。  请看以下示例：  
  
```cpp  
/* compile with: /EHsc /MDd */  
#include <vector>  
struct base {  
   // FIX: uncomment the next line  
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
  
## 请参阅  
 [STL 概述](../standard-library/cpp-standard-library-overview.md)