---
title: "数组 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "数组 [C++]"
  - "声明数组, 关于声明数组"
  - "多维数组"
ms.assetid: 3f5986aa-485c-4ba4-9502-67e2ef924238
caps.latest.revision: 12
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 数组 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

数组是类似对象的集合。  数组最简单的用例是矢量，可以按以下序列声明矢量：  
  
```  
  
      decl-specifier identifier [ constant-expression ]  
decl-specifier identifier []  
decl-specifier identifer [][ constant-expression] . . .  
decl-specifier identifier [ constant-expression ]  
[ constant-expression ] . . .  
```  
  
 1.  声明说明符：  
  
-   可选存储类说明符。  
  
-   可选 **const** 和\/或 `volatile` 说明符。  
  
-   数组元素的类型名称。  
  
 2.  声明符：  
  
-   标识符。  
  
-   用方括号 **\[\] 括起来的整型的常数表达式。**如果使用额外方括号声明多个维度，则可省略第一组括号中的常数表达式。  
  
-   包含常数表达式的可选附加方括号。  
  
 3.  可选初始值设定项。请参阅[初始值设定项](../cpp/initializers.md)。  
  
 数组中的元素数目由常数表达式给定。  数组中的第一个元素是 0th 元素，最后一个元素是 \(*n*\-1\) 元素，其中 *n* 是数组可以包含的元素数。  *constant\-expression* 必须是整型且必须大于 0。  仅当数组是 `struct` 或“联合”中的最后一个字段并启用 Microsoft 扩展 \(\/Ze\) 时，零大小的数组才是合法的。  
  
 以下示例说明如何在运行时定义数组：  
  
```  
// arrays.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main() {  
   using namespace std;  
   int size = 3, i = 0;  
  
   int* myarr = new int[size];  
  
   for (i = 0 ; i < size ; i++)  
      myarr[i] = 10;  
  
   for (i = 0 ; i < size ; i++)  
      printf_s("myarr[%d] = %d\n", i, myarr[i]);  
  
   delete [] myarr;  
}  
```  
  
 数组是派生类型，可以从函数、引用和 `void` 之外的任何其他派生类型或基本类型构造。  
  
 从其他数组构造的数组是多维数组。  通过按顺序放置多个括起来的常数表达式来指定这些多维数组。  例如，考虑此声明：  
  
```  
int i2[5][7];  
```  
  
 它指定类型为 `int` 的数组，从概念上以五行七列的二维矩阵排列，如下图所示：  
  
 ![多维数组的概念布局](../cpp/media/vc38rc1.png "vc38RC1")  
多维数组的概念性布局  
  
 在具有初始值设定项列表的多维数组的声明中（如[初始值设定项](../cpp/initializers.md)中所述），可以省略指定第一个维度的边界的常数表达式。  例如：  
  
```  
// arrays2.cpp  
// compile with: /c  
const int cMarkets = 4;  
// Declare a float that represents the transportation costs.  
double TransportCosts[][cMarkets] = {   
   { 32.19, 47.29, 31.99, 19.11 },  
   { 11.29, 22.49, 33.47, 17.29 },  
   { 41.97, 22.09,  9.76, 22.55 }  
};  
```  
  
 前面的声明定义四列三行的数组。  行表示工厂，列表示从工厂装运到的市场。  值是从工厂运输到市场的成本。  忽略数组的第一个维度，但编译器会通过检查该初始值设定项来填充它。  
  
 本节中的主题：  
  
-   [使用数组](../cpp/using-arrays-cpp.md)  
  
-   [表达式中的数组](../cpp/arrays-in-expressions.md)  
  
-   [下标运算符的解释](../cpp/interpretation-of-subscript-operator.md)  
  
-   [数组类型的间接寻址](../cpp/indirection-on-array-types.md)  
  
-   [C\+\+ 数组的排序](../cpp/ordering-of-cpp-arrays.md)  
  
## 示例  
 省略多维数组的第一个维度的边界规范的技术也可用于函数声明中，如下所示：  
  
```  
// multidimensional_arrays.cpp  
// compile with: /EHsc  
// arguments: 3  
#include <limits>   // Includes DBL_MAX  
#include <iostream>  
  
const int cMkts = 4, cFacts = 2;  
  
// Declare a float that represents the transportation costs  
double TransportCosts[][cMkts] = {   
   { 32.19, 47.29, 31.99, 19.11 },  
   { 11.29, 22.49, 33.47, 17.29 },  
   { 41.97, 22.09,  9.76, 22.55 }    
};  
  
// Calculate size of unspecified dimension  
const int cFactories = sizeof TransportCosts /  
                  sizeof( double[cMkts] );  
  
double FindMinToMkt( int Mkt, double myTransportCosts[][cMkts], int mycFacts);  
  
using namespace std;  
  
int main( int argc, char *argv[] ) {  
   double MinCost;  
  
   if (argv[1] == 0) {  
      cout << "You must specify the number of markets." << endl;  
      exit(0);  
   }  
   MinCost = FindMinToMkt( *argv[1] - '0', TransportCosts, cFacts);  
   cout << "The minimum cost to Market " << argv[1] << " is: "  
       << MinCost << "\n";  
}  
  
double FindMinToMkt(int Mkt, double myTransportCosts[][cMkts], int mycFacts) {  
   double MinCost = DBL_MAX;  
  
   for( int i = 0; i < cFacts; ++i )  
      MinCost = (MinCost < TransportCosts[i][Mkt]) ?  
         MinCost : TransportCosts[i][Mkt];  
  
   return MinCost;  
}  
```  
  
  **市场 3 的最低成本为：17.29**   
## 注释  
 编写函数 `FindMinToMkt`，以便添加不需要更改任何代码而仅需重新编译的新工厂。  
  
## 请参阅  
 [C\+\+ Abstract Declarators](http://msdn.microsoft.com/zh-cn/e7e18c18-0cad-4450-942b-d27e1d4dd088)