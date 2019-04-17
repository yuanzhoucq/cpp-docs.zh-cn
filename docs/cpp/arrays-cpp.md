---
title: 数组 (C++)
ms.date: 11/19/2018
helpviewer_keywords:
- declaring arrays [C++], about declaring arrays
- multidimensional arrays [C++]
- arrays [C++]
ms.assetid: 3f5986aa-485c-4ba4-9502-67e2ef924238
ms.openlocfilehash: 176e358bd0217ac914eb4ee6079126d3f429b6dd
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2018
ms.locfileid: "52176874"
---
# <a name="arrays-c"></a>数组 (C++)

数组是类似对象的集合。 数组最简单的用例是矢量，可以按以下序列声明矢量：

> *声明说明符* *标识符* **\[** *常量表达式* **]**<br/>
> *声明说明符* *标识符*  **\[]**<br/>
> *声明说明符* *标识符* **\[]\[** *常量表达式* **]** 。 . .<br/>
> *声明说明符* *标识符* **\[** *常量表达式* **]**  **\[** *常数表达式* **]** 。 . .

1. 声明说明符：

   - 可选存储类说明符。

   - 可选**const**和/或**易失性**说明符。

   - 数组元素的类型名称。

1. 声明符：

   - 标识符。

   - 括在方括号内，整型类型的常量表达式 **\[]**。 如果使用额外方括号声明多个维度，在第一组括号可省略常量表达式。

   - 包含常数表达式的可选附加方括号。

1. 可选初始值设定项。 有关详细信息，请参阅[初始值设定项](../cpp/initializers.md)。

由给定数组中元素的数目*常数表达式*。 数组中的第一个元素是 0th 元素，并最后一个元素是 (*n*-1) 元素，其中*n*是该数组可以包含的元素数目。 *常数表达式*必须为整型类型和必须大于 0。 仅当数组中的最后一个字段时，大小为零的数组是合法**struct**或**union**和启用 Microsoft 扩展 (/Ze) 时。

以下示例说明如何在运行时定义数组：

```cpp
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

数组是派生的类型，因此可以从其他函数的引用，除外的派生或基本类型构造并**void**。

从其他数组构造的数组是多维数组。 通过按顺序放置多个括起来的常数表达式来指定这些多维数组。 例如，考虑此声明：

```cpp
int i2[5][7];
```

指定类型的数组**int**、 从概念上讲排列在五个行和七列的二维矩阵中，如下图中所示：

![一个多概念性布局&#45;维数组](../cpp/media/vc38rc1.gif "多的概念性布局&#45;维数组") <br/>
多维数组的概念布局

在声明中的多维数组的具有初始值设定项列表 (如中所述[初始值设定项](../cpp/initializers.md))，可以省略指定第一个维度的边界的常数表达式。 例如：

```cpp
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

前面的声明定义四列三行的数组。 行表示工厂，列表示从工厂装运到的市场。 值是从工厂运输到市场的成本。 忽略数组的第一个维度，但编译器会通过检查该初始值设定项来填充它。

本节中的主题：

- [使用数组](../cpp/using-arrays-cpp.md)

- [表达式中的数组](../cpp/arrays-in-expressions.md)

- [下标运算符的解释](../cpp/interpretation-of-subscript-operator.md)

- [数组类型的间接寻址](../cpp/indirection-on-array-types.md)

- [C++ 数组的排序](../cpp/ordering-of-cpp-arrays.md)

## <a name="example"></a>示例

省略多维数组的第一个维度的边界规范的技术也可用于函数声明中，如下所示：

```cpp
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

```Output
The minimum cost to Market 3 is: 17.29
```

## <a name="comments"></a>注释

编写函数 `FindMinToMkt`，以便添加不需要更改任何代码而仅需重新编译的新工厂。
