---
title: "random_access_iterator_tag 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "xutility/std::random_access_iterator_tag"
  - "random_access_iterator_tag"
  - "std.random_access_iterator_tag"
  - "std::random_access_iterator_tag"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "random_access_iterator_tag 类"
  - "random_access_iterator_tag 结构"
ms.assetid: 59f5b741-c5b4-459c-ad0a-3b67cddeea23
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# random_access_iterator_tag 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

A 类提供了一个返回类型 **迭代器种类** 代表随机访问迭代器的函数.  
  
## 语法  
  
```  
  
   struct random_access_iterator_tag  
: public bidirectional_iterator_tag {};  
```  
  
## 备注  
 类别选择算法类标记为使用编译标记。  模板函数需要查找其迭代器参数最具体的类，以便能够使用最高效的算法在编译时。  对于 `Iterator`类型，必须定义了每个迭代器 `iterator_traits`\<`Iterator`\>**::iterator\_category** 是描绘迭代器的行为的最具体的类标记。  
  
 类型与 **迭代器**\<**Iter**\>**::iterator\_categoryIter**，在描述可以服务为随机访问迭代器的对象时。  
  
## 示例  
  
```  
// iterator_rait.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
#include <list>  
  
using namespace std;  
  
int main( )  
{  
   vector<int> vi;  
   vector<char> vc;  
   list<char> lc;  
   iterator_traits<vector<int>:: iterator>::iterator_category cati;  
   iterator_traits<vector<char>:: iterator>::iterator_category catc;  
   iterator_traits<list<char>:: iterator>::iterator_category catlc;  
  
   // These are both random-access iterators  
   cout << "The type of iterator for vector<int> is "  
       << "identified by the tag:\n "   
       << typeid ( cati ).name( ) << endl;  
   cout << "The type of iterator for vector<char> is "  
       << "identified by the tag:\n "   
       << typeid ( catc ).name( ) << endl;  
   if ( typeid ( cati ) == typeid( catc ) )  
      cout << "The iterators are the same." << endl << endl;  
   else  
      cout << "The iterators are not the same." << endl << endl;  
  
   // But the list iterator is bidirectinal, not random access  
   cout << "The type of iterator for list<char> is "  
       << "identified by the tag:\n "   
       << typeid (catlc).name( ) << endl;  
  
   // cout << ( typeid ( vi.begin( ) ) == typeid( vc.begin( ) ) ) << endl;  
   if ( typeid ( vi.begin( ) ) == typeid( vc.begin( ) ) )  
      cout << "The iterators are the same." << endl;  
   else  
      cout << "The iterators are not the same." << endl;  
   // A random-access iterator is a bidirectional iterator.  
   cout << ( void* ) dynamic_cast< iterator_traits<list<char>:: iterator>  
          ::iterator_category* > ( &catc ) << endl;  
}  
```  
  
## 示例输出  
 将生成下面关于x86的输出。  
  
```  
The type of iterator for vector<int> is identified by the tag:  
 struct std::random_access_iterator_tag  
The type of iterator for vector<char> is identified by the tag:  
 struct std::random_access_iterator_tag  
The iterators are the same.  
  
The type of iterator for list<char> is identified by the tag:  
 struct std::bidirectional_iterator_tag  
The iterators are not the same.  
0012FF3B  
```  
  
## 要求  
 **头文件：** \<iterator\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [bidirectional\_iterator\_tag 结构](../standard-library/bidirectional-iterator-tag-struct.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)