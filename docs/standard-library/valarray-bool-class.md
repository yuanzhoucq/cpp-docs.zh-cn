---
title: "valarray&lt;bool&gt; 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "valarray<bool>"
  - "valarray/std::valarray<bool>"
  - "std::valarray<bool>"
  - "std.valarray<bool>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "valarray<bool> 类"
ms.assetid: fc0e7121-4758-4ea5-86c3-f04448f04acf
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# valarray&lt;bool&gt; 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

模板类 **valarray\<Type\>** 的专用版本给 `bool`类型的元素。  
  
## 语法  
  
```  
  
class valarray<bool>  
  
```  
  
## 示例  
  
```  
// valarray_bool.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 10 ), vaR ( 10 );  
   valarray<bool> vaBool ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )   
      vaL [ i ] =  -i;  
   for ( i = 1 ; i < 10 ; i += 2 )   
      vaL [ i ] =  i;  
   for ( i = 0 ; i < 10 ; i++ )   
      vaR [ i ] =  i;  
  
   cout << "The initial Left valarray is: ( ";  
   for ( i = 0 ; i < 10 ; i++ )  
      cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial Right valarray is: ( ";  
   for ( i = 0 ; i < 10 ; i++ )  
      cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaBool = ( vaL < vaR );  
   cout << "The result of the less-than comparison "  
   << "test is the\n valarray<bool>: ( ";  
   for ( i = 0 ; i < 10 ; i++ )  
      cout << vaBool [ i ] << " ";  
   cout << ")." << endl;  
}  
```  
  
  **最初的 valarray 是：\(0 1 \-2 3 \-4 5 \-6 7 \-8 9\)。**  
**最初正确 valarray 是：\(0 1 2 3 4 5 6 7 8 9\)。**  
**小于比较实例方法是测试的结果。**  
 **valarray\<bool\>: \( 0 0 1 0 1 0 1 0 1 0 \)。**   
## 要求  
 **Header:** \<valarray\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [valarray 类](../standard-library/valarray-class.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)