---
title: 数组 (C++)
ms.date: 11/14/2019
helpviewer_keywords:
- declaring arrays [C++], about declaring arrays
- multidimensional arrays [C++]
- arrays [C++]
ms.assetid: 3f5986aa-485c-4ba4-9502-67e2ef924238
ms.openlocfilehash: 91c57a9c4ef190dcace1813dd81739ac72e6b358
ms.sourcegitcommit: 217fac22604639ebd62d366a69e6071ad5b724ac
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188994"
---
# <a name="arrays-c"></a>数组 (C++)

数组是一系列相同类型的对象，该对象占用一个连续的内存区域。 传统的 C 样式数组是许多 bug 的源，但仍很常见，尤其是在较旧的代码库中。 在新式C++中，强烈建议使用本节中所述的[std：： vector](../standard-library/vector-class.md)或[std：： array](../standard-library/array-class-stl.md)而不是 C 样式数组。 这两个标准库类型都将其元素存储为连续的内存块，但提供了更高的类型安全性和可保证指向序列内有效位置的迭代器。 有关详细信息，请参阅[容器（ C++现代）](containers-modern-cpp.md)。

## <a name="stack-declarations"></a>堆栈声明

在C++数组声明中，数组大小在变量名称之后指定，而不是在类型名称之后指定为其他某些语言。 下面的示例声明一个在堆栈上分配的1000双精度数组。 由于编译器必须知道要分配的堆栈空间量，因此必须以整数文本或作为常量表达式的形式提供元素数;它不能使用在运行时计算的值。 为数组中的每个元素分配默认值0。 如果没有分配默认值，则每个元素最初都将包含发生在该位置的任何随机值。

```cpp
    constexpr size_t size = 1000;

    // Declare an array of doubles to be allocated on the stack
    double numbers[size] {0};

    // Assign a new value to the first element
    numbers[0] = 1;

    // Assign a value to each subsequent element
    // (numbers[1] is the second element in the array.)
    for (size_t i = 1; i < size; i++)
    {
        numbers[i] = numbers[i-1] * 1.1;
    }

    // Access each element
    for (size_t i = 0; i < size; i++)
    {
        std::cout << numbers[i] << " ";
    }
```

数组中的第一个元素是第0个元素，最后一个元素是（*n*-1）元素，其中*n*是数组可以包含的元素数。 声明中的元素数量必须是整型，并且必须大于0。 你有责任确保你的程序永远不会将值传递到大于 `(size - 1)`的下标运算符。

仅当数组是**结构**或**联合**中的最后一个字段时，并且在 Microsoft 扩展（/ze）启用时，才合法数组的大小。

基于堆栈的数组比基于堆的数组分配和访问速度更快，但元素数不能太大，以致于占用太多堆栈内存。 太多多少依赖于你的程序。 可以使用分析工具来确定数组是否太大。

## <a name="heap-declarations"></a>堆声明

如果需要的数组太大，无法在堆栈上分配，或在编译时无法知道其大小，则可以使用[新的\[\]](new-operator-cpp.md)表达式在堆上进行分配。 运算符返回指向第一个元素的指针。 可以对指针变量使用下标运算符，就像在基于堆栈的数组中一样。 还可以使用[指针算法](../c-language/pointer-arithmetic.md)将指针移动到数组中的任意元素。 你需要负责确保：

- 始终保留原始指针地址的副本，以便在不再需要数组时可以删除内存。
- 不会递增或递减超出数组界限的指针地址。

下面的示例演示如何在运行时在堆上定义数组，以及如何使用下标运算符或使用指针算法访问数组元素：

```cpp

void do_something(size_t size)
{
    // Declare an array of doubles to be allocated on the heap
    double* numbers = new double[size]{ 0 };

    // Assign a new value to the first element
    numbers[0] = 1;

    // Assign a value to each subsequent element
    // (numbers[1] is the second element in the array.)
    for (size_t i = 1; i < size; i++)
    {
        numbers[i] = numbers[i - 1] * 1.1;
    }

    // Access each element with subscript operator
    for (size_t i = 0; i < size; i++)
    {
        std::cout << numbers[i] << " ";
    }

    // Access each element with pointer arithmetic
    // Use a copy of the pointer for iterating
    double* p = numbers;

    for (size_t i = 0; i < size; i++)
    {
        // Dereference the pointer, then increment it
        std::cout << *p++ << " ";
    }

    // Alternate method:
    // Reset p to numbers[0]:
    p = numbers;

    // Use address of pointer to compute bounds.
    // The compiler computes size as the number
    // of elements * (bytes per element).
    while (p < (numbers + size))
    {
        // Dereference the pointer, then increment it
        std::cout << *p++ << " ";
    }

    delete[] numbers; // don't forget to do this!

}
int main()
{
    do_something(108);
}

```

## <a name="initializing-arrays"></a>初始化数组

可以在循环中、一次或在单个语句中初始化一个数组。 以下两个数组的内容相同：

```cpp
    int a[10];
    for (int i = 0; i < 10; ++i)
    {
        a[i] = i + 1;
    }

    int b[10]{ 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };
```

## <a name="passing-arrays-to-functions"></a>将数组传递给函数

当数组传递到函数时，它将作为指向第一个元素的指针传递。 这适用于基于堆栈和堆的数组。 指针不包含其他大小或类型信息。 此行为称为*指针衰减*。 将数组传递给函数时，必须始终在单独的参数中指定元素数。 此行为还意味着数组元素在数组传递到函数时不会被复制。 若要防止函数修改元素，请将参数指定为指向**const**元素的指针。

下面的示例演示了一个函数，该函数接受一个数组和一个长度。 指针指向原始数组，而不是副本。 由于参数不是**常量**，因此函数可以修改数组元素。

```cpp
void process(double p*, const size_t len)
{
    std::cout << "process:\n";
    for (size_t i = 0; i < len; ++i)
    {
        // do something with p[i]
    }
}
```

将数组声明为 const，使其在函数块中为只读：

```cpp
void process(const double p*, const size_t len);
```

也可以通过这些方式声明同一函数，不会更改行为。 数组仍作为指向第一个元素的指针传递：

```cpp
// Unsized array
void process(const double p[] const size_t len);

// Fixed-size array. Length must still be specified explicitly.
void process(const double p[1000], const size_t len);
```

## <a name="multidimensional-arrays"></a>多维数组

从其他数组构造的数组是多维数组。 通过按顺序放置多个括起来的常数表达式来指定这些多维数组。 例如，考虑此声明：

```cpp
int i2[5][7];
```

它指定类型为**int**的数组，在概念上按五行和七列的二维矩阵排列，如下图所示：

![多维&#45;数组的概念性布局](../cpp/media/vc38rc1.gif "多维&#45;数组的概念性布局") <br/>
多维数组的概念布局

对于具有初始值设定项列表的 initializers 数组的声明（如[初始值设定](../cpp/initializers.md)项中所述），可以省略指定第一个维度边界的常量表达式。 例如：

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

在 n 维数组类型上使用间接寻址运算符（*）将生成一维数组。 如果 n 为 1，则将生成标量（或数组元素）。

C++ 数组按行优先顺序存储。 行优先顺序意味着最后一个下标变化最快。

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

   for( size_t i = 0; i < cFacts; ++i )
      MinCost = (MinCost < TransportCosts[i][Mkt]) ?
         MinCost : TransportCosts[i][Mkt];

   return MinCost;
}
```

```Output
The minimum cost to Market 3 is: 17.29
```

编写函数 `FindMinToMkt`，以便添加不需要更改任何代码而仅需重新编译的新工厂。

## <a name="initializing-arrays"></a>初始化数组

如果类具有构造函数，该类的数组将由构造函数初始化。 如果初始值设定项列表中的项少于数组中的元素，则默认的构造函数将用于剩余元素。 如果没有为类定义默认构造函数，初始值设定项列表必须完整，即数组中的每个元素都必须有一个初始值设定项。

考虑定义了两个构造函数的`Point` 类：

```cpp
// initializing_arrays1.cpp
class Point
{
public:
   Point()   // Default constructor.
   {
   }
   Point( int, int )   // Construct from two ints
   {
   }
};

// An array of Point objects can be declared as follows:
Point aPoint[3] = {
   Point( 3, 3 )     // Use int, int constructor.
};

int main()
{
}
```

`aPoint` 的第一个元素是使用构造函数 `Point( int, int )` 构造的；剩余的两个元素是使用默认构造函数构造的。

静态成员数组（无论是否为**const** ）可以在其定义（类声明的外部）中进行初始化。 例如：

```cpp
// initializing_arrays2.cpp
class WindowColors
{
public:
    static const char *rgszWindowPartList[7];
};

const char *WindowColors::rgszWindowPartList[7] = {
    "Active Title Bar", "Inactive Title Bar", "Title Bar Text",
    "Menu Bar", "Menu Bar Text", "Window Background", "Frame"   };
int main()
{
}
```

## <a name="accessing-array-elements"></a>访问数组元素

您可以使用数组下标运算符 (`[ ]`) 访问数组的各个元素。 如果一维数组用于无下标的表达式中，则数组名称的计算结果为一个指向该数组中第一个元素的指针。

```cpp
// using_arrays.cpp
int main() {
   char chArray[10];
   char *pch = chArray;   // Evaluates to a pointer to the first element.
   char   ch = chArray[0];   // Evaluates to the value of the first element.
   ch = chArray[3];   // Evaluates to the value of the fourth element.
}
```

使用多维数组时，可以在表达式中使用各种组合。

```cpp
// using_arrays_2.cpp
// compile with: /EHsc /W1
#include <iostream>
using namespace std;
int main() {
   double multi[4][4][3];   // Declare the array.
   double (*p2multi)[3];
   double (*p1multi);

   cout << multi[3][2][2] << "\n";   // C4700 Use three subscripts.
   p2multi = multi[3];               // Make p2multi point to
                                     // fourth "plane" of multi.
   p1multi = multi[3][2];            // Make p1multi point to
                                     // fourth plane, third row
                                     // of multi.
}
```

在前面的代码中，`multi` 是**double**类型的三维数组。 `p2multi` 指针指向大小为3的**双精度**类型的数组。 在此示例中，该数组与一个、两个和三个下标一起使用。 尽管更为常见的是指定所有下标（如在 `cout` 语句中），但有时选择数组元素的特定子集会很有用，如 `cout` 后面的语句中所示。

## <a name="overloading-subscript-operator"></a>重载下标运算符

与其他运算符一样，下标运算符（`[]`）可由用户重新定义。 如果没有重载下标运算符，下标运算符的默认行为是使用以下方法组合数组名称和下标：

`*((array_name) + (subscript))`

像涉及指针类型的所有加法中一样，缩放将自动执行以调整类型的大小。 因此，生成的值不是来自数组名称的源的*n*个字节;相反，它是数组的第*n*个元素。 有关此转换的详细信息，请参阅[加法运算符](additive-operators-plus-and.md)。

同样，对于多维数组，将使用以下方法获取地址：

`((array_name) + (subscript1 * max2 * max3 * ... * maxn) + (subscript2 * max3 * ... * maxn) + ... + subscriptn))`

## <a name="arrays-in-expressions"></a>表达式中的数组

如果数组类型的标识符出现在 `sizeof`、地址（`&`）或引用的初始化之外的表达式中，则它将转换为指向第一个数组元素的指针。 例如：

```cpp
char szError1[] = "Error: Disk drive not ready.";
char *psz = szError1;
```

指针 `psz` 指向数组 `szError1` 的第一个元素。 与指针不同，数组是不可修改的左值。 因此，以下赋值是非法的：

```cpp
szError1 = psz;
```

## <a name="see-also"></a>另请参阅

[std：： array](../standard-library/array-class-stl.md)
