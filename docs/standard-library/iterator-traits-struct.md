---
title: "iterator_traits 结构 | Microsoft Docs"
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
  - "std::iterator_traits"
  - "xutility/std::iterator_traits"
  - "iterator_traits"
  - "std.iterator_traits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "iterator_traits 类"
  - "iterator_traits 结构"
ms.assetid: 8b92c2c5-f658-402f-8ca1-e7ae301b8514
caps.latest.revision: 19
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# iterator_traits 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用的模板帮助器结构指定迭代器应拥有的任何重要类型定义。  
  
## 语法  
  
```  
template<class Iterator>  
    struct iterator_traits {  
        typedef typename Iterator::iterator_category iterator_category;  
        typedef typename Iterator::value_type value_type;  
        typedef typename Iterator::difference_type difference_type;  
        typedef difference_type distance_type;  
        typedef typename Iterator::pointer pointer;  
        typedef typename Iterator::reference reference;  
    };  
template<class Type>  
    struct iterator_traits<Type*> {  
        typedef random_access_iterator_tag iterator_category;  
        typedef Type value_type;  
        typedef ptrdiff_t difference_type;  
        typedef difference_type distance_type;  
        typedef Type *pointer;  
        typedef Type& reference;  
    };  
template<class Type>  
    struct iterator_traits<const Type*> {  
        typedef random_access_iterator_tag iterator_category;  
        typedef Type value_type;  
        typedef ptrdiff_t difference_type;  
        typedef difference_type distance_type;  
        typedef const Type *pointer;  
        typedef const Type& reference;  
    };  
```  
  
## 备注  
 模板结构定义类型成员  
  
-   **iterator\_category**: **Iterator::iterator\_category**的同义词。  
  
-   `value_type`: **Iterator::value\_type**的同义词。  
  
-   `difference_type`: **Iterator::difference\_type**的同义词。  
  
-   `distance_type`: **Iterator::difference\_type.**的同义词  
  
-   **指针**: **Iterator::pointer**的同义词。  
  
-   **引用**: **Iterator::reference**的同义词。  
  
 部分专用化确定重要类型与 **Type \*** 类型或常数 **Type \***对象指针。  
  
 在此实现也可以使用不利用部分专用化的一些模板函数：  
  
```  
template<class Category, class Type, class Diff>  
C _Iter_cat(const iterator<Category, Ty, Diff>&);  
template<class Ty>  
    random_access_iterator_tag _Iter_cat(const Ty *);  
  
template<class Category, class Ty, class Diff>  
Ty *_Val_type(const iterator<Category, Ty, Diff>&);  
template<class Ty>  
    Ty *_Val_type(const Ty *);  
  
template<class Category, class Ty, class Diff>  
Diff *_Dist_type(const iterator<Category, Ty, Diff>&);  
template<class Ty>  
    ptrdiff_t *_Dist_type(const Ty *);  
```  
  
 要更间接数确定同一类型。  使用这些函数为函数调用的参数。  其唯一目的就是提供一种有用的模板类边界到调用函数。  
  
## 示例  
  
```  
// iterator_traits.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <iterator>  
#include <vector>  
#include <list>  
  
using namespace std;  
  
template< class it >  
void  
function( it i1, it i2 )  
{  
   iterator_traits<it>::iterator_category cat;  
   cout << typeid( cat ).name( ) << endl;  
   while ( i1 != i2 )  
   {  
      iterator_traits<it>::value_type x;  
      x = *i1;  
      cout << x << " ";  
      i1++;  
   };     
   cout << endl;  
};  
  
int main( )   
{  
   vector<char> vc( 10,'a' );  
   list<int> li( 10 );  
   function( vc.begin( ), vc.end( ) );  
   function( li.begin( ), li.end( ) );  
}  
```  
  
  **结构 std::random\_access\_iterator\_tag**  
**。**  
**结构 std::bidirectional\_iterator\_tag**  
**0 0 0 0 0 0 0 0 0 0**   
## 要求  
 **头文件：** \<iterator\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [\<iterator\>](../standard-library/iterator.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)