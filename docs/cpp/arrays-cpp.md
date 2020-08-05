---
title: 数组 (C++)
ms.date: 08/03/2020
helpviewer_keywords:
- declaring arrays [C++], about declaring arrays
- multidimensional arrays [C++]
- arrays [C++]
ms.assetid: 3f5986aa-485c-4ba4-9502-67e2ef924238
ms.openlocfilehash: cb949f9a17a6b751dae40202bf82e6cb321b526b
ms.sourcegitcommit: 4eda68a0b3c23d8cefa56b7ba11583412459b32f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87565958"
---
# <a name="arrays-c"></a>数组 (C++)

数组是一系列相同类型的对象，该对象占用一个连续的内存区域。 传统的 C 样式数组是许多 bug 的源，但仍很常见，尤其是在较旧的代码库中。 在现代 c + + 中，强烈建议使用本部分中所述的[std：： vector](../standard-library/vector-class.md)或[std：： array](../standard-library/array-class-stl.md)而不是 c 样式数组。 这两个标准库类型都将其元素存储为连续的内存块。 但是，它们提供了更高的类型安全性，并支持保证指向序列内有效位置的迭代器。 有关详细信息，请参阅[容器 (新式 c + +) ](containers-modern-cpp.md)。

## <a name="stack-declarations"></a>堆栈声明

在 c + + 数组声明中，数组大小在变量名称之后指定，而不是在类型名称之后指定为其他某些语言。 下面的示例声明一个在堆栈上分配的1000双精度数组。 元素数必须以整数文本形式提供，或者作为常量表达式提供。 这是因为编译器必须知道要分配多少堆栈空间;不能使用在运行时计算的值。 为数组中的每个元素分配默认值0。 如果没有分配默认值，则每个元素最初都包含在该内存位置发生的任何随机值。

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

数组中的第一个元素是第零个元素。 最后一个元素是 (*n*-1) 元素，其中*n*是数组可以包含的元素数。 声明中的元素数量必须是整型，并且必须大于0。 你有责任确保你的程序永远不会将值传递到大于的下标运算符 `(size - 1)` 。

仅当数组是或中的最后一个字段 **`struct`** **`union`** ，并且启用了 Microsoft 扩展 (**`/Za`** 或 **`/permissive-`** 未将其设置) 时，零大小的数组才合法。

基于堆栈的数组的分配和访问速度比基于堆的数组更快。 但是，堆栈空间是有限的。 数组元素的数目不能太大，因为它使用了太多的堆栈内存。 太多多少依赖于你的程序。 可以使用分析工具来确定数组是否太大。

## <a name="heap-declarations"></a>堆声明

可能需要的数组太大，无法在堆栈上分配，或者其大小在编译时是未知的。 通过使用表达式，可以在堆上分配此数组 [`new[]`](new-operator-cpp.md) 。 运算符返回指向第一个元素的指针。 下标运算符在指针变量上的工作方式与它在基于堆栈的数组中的工作方式相同。 还可以使用[指针算法](../c-language/pointer-arithmetic.md)将指针移动到数组中的任意元素。 你有责任确保：

- 始终保留原始指针地址的副本，以便在不再需要数组时可以删除内存。
- 不会递增或递减超出数组界限的指针地址。

下面的示例演示如何在运行时在堆上定义一个数组。 它演示了如何使用下标运算符和使用指针算法访问数组元素：

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

当数组传递到函数时，它将作为指向第一个元素的指针传递，无论它是基于堆栈还是基于堆的数组。 指针不包含其他大小或类型信息。 此行为称为*指针衰减*。 将数组传递给函数时，必须始终在单独的参数中指定元素数。 此行为还意味着数组元素传递到函数时不会复制。 若要防止函数修改元素，请将参数指定为指向元素的指针 **`const`** 。

下面的示例演示了一个函数，该函数接受一个数组和一个长度。 指针指向原始数组，而不是副本。 由于参数不为 **`const`** ，因此函数可以修改数组元素。

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
void process(const double p[], const size_t len);

// Fixed-size array. Length must still be specified explicitly.
void process(const double p[1000], const size_t len);
```

## <a name="multidimensional-arrays"></a>多维数组

从其他数组构造的数组是多维数组。 通过按顺序放置多个括起来的常数表达式来指定这些多维数组。 例如，考虑此声明：

```cpp
int i2[5][7];
```

它指定类型为的数组 **`int`** ，在概念上按五行和七列的二维矩阵排列，如下图所示：

![&#45;多维数组的概念性布局](../cpp/media/vc38rc1.gif "&#45;多维数组的概念性布局") <br/>
多维数组的概念布局

可以声明具有初始值设定项列表 (的 initializers 数组，如) [初始值设定](../cpp/initializers.md)项中所述。 在这些声明中，可以省略指定第一个维度边界的常量表达式。 例如：

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

在 n 维数组类型上使用间接寻址运算符 ( * ) 会生成一维数组。 如果 n 为 1，则将生成标量（或数组元素）。

C++ 数组按行优先顺序存储。 行优先顺序意味着最后一个下标变化最快。

## <a name="example"></a>示例

您还可以在函数声明中省略多维数组的第一个维度的边界规范，如下所示：

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

编写函数， `FindMinToMkt` 以便添加新的工厂不需要进行任何代码更改，而只需进行重新编译。

## <a name="initializing-arrays"></a>初始化数组

具有类构造函数的对象数组由构造函数进行初始化。 当初始值设定项列表中的项少于数组中的元素时，默认构造函数将用于其余元素。 如果没有为类定义默认构造函数，则初始值设定项列表必须是*完整*的，也就是说，数组中的每个元素必须有一个初始值设定项。

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

静态成员数组 (**`const`** 在类声明) 外 (的定义中是否可以初始化) 。 例如：

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

您可以使用数组下标运算符 (`[ ]`) 访问数组的各个元素。 如果使用不带下标的一维数组的名称，则会将其计算为指向数组的第一个元素的指针。

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

在上面的代码中， `multi` 是类型的三维数组 **`double`** 。 `p2multi`指针指向大小为3的类型的数组 **`double`** 。 在此示例中，该数组与一个、两个和三个下标一起使用。 尽管更常见的方法是指定所有下标，如语句中所示 `cout` ，有时选择数组元素的特定子集，如以下语句中所示 `cout` 。

## <a name="overloading-subscript-operator"></a>重载下标运算符

与其他运算符一样，下标运算符 (`[]`) 可以由用户重新定义。 如果没有重载下标运算符，下标运算符的默认行为是使用以下方法组合数组名称和下标：

`*((array_name) + (subscript))`

与涉及指针类型的所有加法一样，缩放会自动进行以调整类型大小。 结果值不是从的源中的*n*个字节 `array_name` ; 相反，它是数组的第*n*个元素。 有关此转换的详细信息，请参阅[加法运算符](additive-operators-plus-and.md)。

同样，对于多维数组，将使用以下方法获取地址：

`((array_name) + (subscript1 * max2 * max3 * ... * maxn) + (subscript2 * max3 * ... * maxn) + ... + subscriptn))`

## <a name="arrays-in-expressions"></a>表达式中的数组

如果数组类型的标识符出现在不是的表达式中 **`sizeof`** ，则 (`&`) 或初始化引用的，则将转换为指向第一个数组元素的指针。 例如：

```cpp
char szError1[] = "Error: Disk drive not ready.";
char *psz = szError1;
```

指针 `psz` 指向数组 `szError1` 的第一个元素。 与指针不同，数组不可修改的左值。 这就是为什么下面的赋值是非法的：

```cpp
szError1 = psz;
```

## <a name="see-also"></a>请参阅

[std：： array](../standard-library/array-class-stl.md)
