---
title: "tuple 类 | Microsoft Docs"
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
  - "tr1::tuple"
  - "std.tr1.tuple"
  - "tuple"
  - "tr1.tuple"
  - "std::tr1::tuple"
  - "tuple/std::tr1::tuple"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tuple 类"
  - "tuple 类 [TR1]"
ms.assetid: c38749be-ae4d-41f3-98ea-6aa3250de9a3
caps.latest.revision: 19
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# tuple 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定长包装元素序列。  
  
## 语法  
  
```  
template<class T1, class T2, ..., class TN>  
class tuple {  
public:  
    tuple();  
    explicit tuple(P1, P2, ..., PN);              // 0 < N  
    tuple(const tuple&);  
    template <class U1, class U2, ..., class UN>  
        tuple(const tuple<U1, U2, ..., UN>&);  
    template <class U1, class U2>  
        tuple(const pair<U1, U2>&);               // N == 2  
    void swap(tuple& right);  
    tuple& operator=(const tuple&);  
    template <class U1, class U2, ..., class UN>  
        tuple& operator=(const tuple<U1, U2, ..., UN>&);  
    template <class U1, class U2>  
        tuple& operator=(const pair<U1, U2>&);    // N == 2  
    };  
```  
  
#### 参数  
 `TN`  
 第 N 个元素的元组类型。  
  
## 备注  
 模板类描述 `T1`类型存储，N `T2`对象，…，`TN`，其中分别，其中 `0 <= N <= Nmax`。  元组实例 `tuple<T1, T2, ..., TN>` 的范围是其模板参数的数量。`N` 模板参数的 `Ti` 的索引和相应的值存储的该类型为 `i - 1`。  因此，我们 1，而从计算类型到此文档的 N，从 0 到 N \- 1. 中对应的索引范围。  
  
## 示例  
  
```  
// tuple.cpp  
// compile with: /EHsc  
  
#include <vector>  
#include <iomanip>  
#include <iostream>  
#include <tuple>  
#include <string>  
  
using namespace std;  
  
typedef tuple <int, double, string> ids;  
  
void print_ids(const ids& i)  
{  
   cout << "( "  
        << get<0>(i) << ", "   
        << get<1>(i) << ", "   
        << get<2>(i) << " )." << endl;  
}  
  
int main( )  
{  
   // Using the constructor to declare and initialize a tuple  
   ids p1(10, 1.1e-2, "one");  
  
   // Compare using the helper function to declare and initialize a tuple  
   ids p2;  
   p2 = make_tuple(10, 2.22e-1, "two");  
  
   // Making a copy of a tuple  
   ids p3(p1);  
  
   cout.precision(3);  
   cout << "The tuple p1 is: ( ";  
   print_ids(p1);  
   cout << "The tuple p2 is: ( ";  
   print_ids(p2);  
   cout << "The tuple p3 is: ( ";  
   print_ids(p3);  
  
   vector<ids> v;  
  
   v.push_back(p1);  
   v.push_back(p2);  
   v.push_back(make_tuple(3, 3.3e-2, "three"));  
  
   cout << "The tuples in the vector are" << endl;  
   for(vector<ids>::const_iterator i = v.begin(); i != v.end(); ++i)  
   {  
      print_ids(*i);  
   }  
}  
```  
  
  **元组 p1 是：\(10，0.011，一\)。**  
**元组 p2 是：\(10，0.222，两\)。**  
**元组 p3 是：\(10，0.011，一\)。**  
**在矢量的元组。**  
**\(10，0.011，一\)。**  
**\(10，0.222，两\)。**  
**\(3，0.033，三个\)。**   
## 要求  
 **页眉：** \<元组\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [\<tuple\>](../standard-library/tuple.md)   
 [make\_tuple 函数](../Topic/make_tuple%20Function.md)