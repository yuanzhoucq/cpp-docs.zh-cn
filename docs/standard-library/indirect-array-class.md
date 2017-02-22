---
title: "indirect_array 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.indirect_array"
  - "valarray/std::indirect_array"
  - "std::indirect_array"
  - "indirect_array"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "indirect_array 类"
ms.assetid: 10e1eaea-ba5a-405c-a25e-7bdd3eee7fc7
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# indirect_array 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持对象是的子集 valarrays 通过提供了子集数组之间操作的内部，辅助模板类通过指定子集定义 valarray 父级的索引。  
  
## 语法  
  
```  
template<class Type>  
   class indirect_array {  
public:  
   typedef Type value_type;  
   void operator=(  
      const valarray<Type>& x  
   ) const;  
  
   void operator=(  
      const Type& x  
   ) const;  
  
   void operator*=(  
      const valarray<Type>& x  
   ) const;  
  
   void operator/=(  
      const valarray<Type>& x  
   ) const;  
  
   void operator%=(  
      const valarray<Type>& x  
   ) const;  
  
   void operator+=(  
      const valarray<Type>& x  
   ) const;  
  
   void operator-=(  
      const valarray<Type>& x  
   ) const;  
  
   void operator^=(  
      const valarray<Type>& x  
   ) const;  
  
   void operator&=(  
      const valarray<Type>& x  
   ) const;  
  
   void operator|=(  
      const valarray<Type>& x  
   ) const;  
  
   void operator<<=(  
      const valarray<Type>& x  
   ) const;  
  
   void operator>>=(  
      const valarray<Type>& x  
   ) const;  
  
// The rest is private or implementation defined  
}  
```  
  
## 备注  
 类描述对象以及类 **valarray\<size\_t\>xa** 一起存储为对象类 [valarray](../standard-library/valarray-class.md)**\<类型\>va** 的引用，描述元素序列。**valarrayType\<\>** 对象中的对象。  
  
 通过将窗体的 **va\[xa\]** 的表达式只构造  **indirect\_array\<Type\>** 对象。  indirect\_array 类成员的行为像函数然后相应的函数签名定义为 **valarray\<Type\>**，但选择的元素序列仅受影响。  
  
 序列包括[范围](../Topic/valarray::size.md)**xa.**元素，元素变为 **xa**索引 `I` \[`I`\] 在 **va**内。  
  
## 示例：  
  
```  
// indirect_array.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> va ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      va [ i ] =  i;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      va [ i ] =  -1;  
  
   cout << "The initial operand valarray is:  ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << va [ i ] << " ";  
   cout << ")." << endl;  
  
   // Select 2nd, 4th & 6th elements  
   // and assign a value of 10 to them  
   valarray<size_t> indx ( 3 );  
   indx [0] = 2;  
   indx [1] = 4;  
   indx [2] = 6;  
   va[indx] = 10;  
  
   cout << "The modified operand valarray is:  ( ";  
      for (i = 0 ; i < 10 ; i++ )  
         cout << va [ i ] << " ";  
   cout << ")." << endl;  
}  
```  
  
### Output  
  
```  
The initial operand valarray is:  ( 0 -1 2 -1 4 -1 6 -1 8 -1 ).  
The modified operand valarray is:  ( 0 -1 10 -1 10 -1 10 -1 8 -1 ).  
```  
  
## 要求  
 **Header:** \<valarray\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)