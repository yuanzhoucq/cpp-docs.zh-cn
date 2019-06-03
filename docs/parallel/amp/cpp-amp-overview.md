---
title: C++ AMP 概述
ms.date: 11/19/2018
helpviewer_keywords:
- C++ Accelerated Massive Parallelism, requirements
- C++ Accelerated Massive Parallelism, architecture
- C++ AMP
- C++ Accelerated Massive Parallelism, overview
- C++ Accelerated Massive Parallelism
ms.assetid: 9e593b06-6e3c-43e9-8bae-6d89efdd39fc
ms.openlocfilehash: 4098a1467b0f81b5f66a2e45a4bb2138e8c1c262
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/31/2019
ms.locfileid: "66449951"
---
# <a name="c-amp-overview"></a>C++ AMP 概述

C++Accelerated Massive Parallelism (C++ AMP) 加速执行的C++通过利用数据并行硬件图形处理单元 (GPU) 例如离散图像卡上的代码。 通过使用C++AMP 中，您可以编写代码多维数据算法，以便执行进行加速异类硬件上使用并行度。 C++ AMP 编程模型包括多维数组、索引、内存传输、平铺和数学函数库。 可以使用C++AMP 语言扩展控制数据移动的方式在 CPU 和 GPU 之间相互后，以便您可以提高性能。

## <a name="system-requirements"></a>系统要求

- Windows 7 或更高版本

- Windows Server 2008 R2 或更高版本

- DirectX 11 功能级别 11.0 或更高的硬件

- 对于在软件模拟器上进行调试，Windows 8 或 Windows Server 2012 是必需的。 对于在硬件上进行的调试，您必须为图形卡安装驱动程序。 有关详细信息，请参阅[调试 GPU 代码](/visualstudio/debugger/debugging-gpu-code)。

- 注意:在 ARM64 上目前不支持 a m P。

## <a name="introduction"></a>介绍

以下两个示例说明了的主要组件C++a m P。 假设你想要添加两个一维数组的相应元素。 例如，你可能想要添加`{1, 2, 3, 4, 5}`并`{6, 7, 8, 9, 10}`若要获取`{7, 9, 11, 13, 15}`。 而无需使用C++AMP 中，您可以编写以下代码以添加数字并显示结果。

```cpp
#include <iostream>

void StandardMethod() {

    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5];

    for (int idx = 0; idx < 5; idx++)
    {
        sumCPP[idx] = aCPP[idx] + bCPP[idx];
    }

    for (int idx = 0; idx < 5; idx++)
    {
        std::cout << sumCPP[idx] << "\n";
    }
}
```

代码的重要部分如下所示：

- 数据：数据包括三个数组。 所有具有相同的秩 (1) 和长度 (5)。

- 迭代:第一个`for`循环提供了用于循环访问数组中元素的机制。 你想要执行以计算总和的代码包含在第一个`for`块。

- 索引：`idx`变量访问数组的各个元素。

使用C++AMP 中，您可以编写以下代码改为。

```cpp
#include <amp.h>
#include <iostream>
using namespace concurrency;

const int size = 5;

void CppAmpMethod() {
    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[size];

    // Create C++ AMP objects.
    array_view<const int, 1> a(size, aCPP);
    array_view<const int, 1> b(size, bCPP);
    array_view<int, 1> sum(size, sumCPP);
    sum.discard_data();

    parallel_for_each(
        // Define the compute domain, which is the set of threads that are created.
        sum.extent,
        // Define the code to run on each thread on the accelerator.
        [=](index<1> idx) restrict(amp) {
            sum[idx] = a[idx] + b[idx];
        }
    );

    // Print the results. The expected output is "7, 9, 11, 13, 15".
    for (int i = 0; i < size; i++) {
        std::cout << sum[i] << "\n";
    }
}
```

相同的基本元素不存在，但C++使用 AMP 构造：

- 数据：使用C++数组构造三个C++a m P [array_view](../../parallel/amp/reference/array-view-class.md)对象。 提供四个值来构造`array_view`对象： 数据值、 秩、 元素类型和长度的`array_view`每个维度中的对象。 等级和类型作为类型参数传递。 数据和长度作为构造函数参数传递。 在此示例中，C++是一维数组传递给构造函数。 等级和长度用于构造中的数据的矩形形状`array_view`对象和值用于填充数组的数据。 运行时库还包括[array 类](../../parallel/amp/reference/array-class.md)，其中包含类似于一个接口`array_view`类和更高版本在本文中讨论。

- 迭代:[Parallel_for_each 函数 (C++ AMP)](reference/concurrency-namespace-functions-amp.md#parallel_for_each)提供了一种机制，用于循环访问的数据元素，或*计算域*。 在此示例中，计算域由`sum.extent`。 你想要执行的代码包含在 lambda 表达式，或*内核函数*。 `restrict(amp)`指示，只有的子集C++语言的C++AMP 可以加快使用。

- 索引：[Index 类](../../parallel/amp/reference/index-class.md)变量`idx`，声明了一个要匹配的秩的一个级别`array_view`对象。 通过使用索引，您可以访问的各个元素`array_view`对象。

## <a name="shaping-and-indexing-data-index-and-extent"></a>形成和索引数据: index 和 extent

必须定义数据值和声明的数据的形状，然后才能运行内核代码。 所有数据都被都定义为数组 （矩形），并可以定义要具有任何的秩 （维数） 的数组。 数据可以是任何维度任何大小。

### <a name="index-class"></a>index 类

[Index 类](../../parallel/amp/reference/index-class.md)中指定一个位置`array`或`array_view`通过将从每个维度原点的偏移量封装到一个对象的对象。 当访问数组中的位置时，您传递`index`对象的索引运算符，与`[]`，而不是整数索引列表。 可以通过访问每个维度中的元素[数组:: operator （) 运算符](reference/array-class.md#operator_call)或[array_view::operator() 运算符](reference/array-view-class.md#operator_call)。

下面的示例创建一个一维的索引，它指定第三个元素中的一维`array_view`对象。 索引用于打印中的第三个元素`array_view`对象。 输出为 3。

```cpp
int aCPP[] = {1, 2, 3, 4, 5};
array_view<int, 1> a(5, aCPP);

index<1> idx(2);

std::cout << a[idx] << "\n";
// Output: 3
```

下面的示例创建一个二维索引，它指定的元素，行 = 1 和列数为 2 的二维`array_view`对象。 中的第一个参数`index`构造函数是行组件，并且第二个参数是列组件。 输出为 6。

```cpp
int aCPP[] = {1, 2, 3, 4, 5, 6};
array_view<int, 2> a(2, 3, aCPP);

index<2> idx(1, 2);

std::cout <<a[idx] << "\n";
// Output: 6
```

下面的示例创建一个三维索引，它指定的元素位置深度 = 0，行 = 1 和列数为 3 的三维`array_view`对象。 请注意，第一个参数是深度组件，第二个参数是行组件，第三个参数是列组件。 输出是 8。

```cpp
int aCPP[] = {
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12,
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12};

array_view<int, 3> a(2, 3, 4, aCPP);

// Specifies the element at 3, 1, 0.
index<3> idx(0, 1, 3);

std::cout << a[idx] << "\n";
// Output: 8
```

### <a name="extent-class"></a>extent 类

[Extent 类](../../parallel/amp/reference/extent-class.md)指定的每个维度中的数据的长度`array`或`array_view`对象。 可以创建扩展盘区，并使用它来创建`array`或`array_view`对象。 您还可以检索的现有程度`array`或`array_view`对象。 下面的示例输出中的每个维度的范围的长度`array_view`对象。

```cpp
int aCPP[] = {
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12,
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12};
// There are 3 rows and 4 columns, and the depth is two.
array_view<int, 3> a(2, 3, 4, aCPP);

std::cout << "The number of columns is " << a.extent[2] << "\n";
std::cout << "The number of rows is " << a.extent[1] << "\n";
std::cout << "The depth is " << a.extent[0] << "\n";
std::cout << "Length in most significant dimension is " << a.extent[0] << "\n";
```

下面的示例创建`array_view`对象具有相同的维度中的上一示例中，但此示例中的对象使用`extent`对象而不是使用显式参数`array_view`构造函数。

```cpp
int aCPP[] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24};
extent<3> e(2, 3, 4);

array_view<int, 3> a(e, aCPP);

std::cout << "The number of columns is " << a.extent[2] << "\n";
std::cout << "The number of rows is " << a.extent[1] << "\n";
std::cout << "The depth is " << a.extent[0] << "\n";
```

## <a name="moving-data-to-the-accelerator-array-and-arrayview"></a>将数据移动到快捷键: array 和 array_view

用于将数据移动到加速器的两个数据容器运行时库中定义。 它们是[array 类](../../parallel/amp/reference/array-class.md)并[array_view 类](../../parallel/amp/reference/array-view-class.md)。 `array`类是一个容器类的构造对象时创建的数据的深层副本。 `array_view`类是一个包装类，当内核函数访问数据时，复制数据。 当源设备上需要的数据时将数据复制回。

### <a name="array-class"></a>array 类

当`array`构造对象，如果使用的构造函数，包括指向数据集数据的深层副本在快捷键上创建。 核函数修改快捷键上的副本。 内核函数的执行完成后，必须将数据复制回源数据结构。 下面的示例将一个向量中的每个元素乘以 10。 内核函数完成后，`vector conversion operator`用于将数据复制回矢量对象。

```cpp
std::vector<int> data(5);

for (int count = 0; count <5; count++)
{
    data[count] = count;
}

array<int, 1> a(5, data.begin(), data.end());

parallel_for_each(
    a.extent,
    [=, &a](index<1> idx) restrict(amp) {
        a[idx] = a[idx]* 10;
    });

data = a;
for (int i = 0; i < 5; i++)
{
    std::cout << data[i] << "\n";
}
```

### <a name="arrayview-class"></a>array_view 类

`array_view`具有几乎相同的成员`array`类，但基础行为不同时。 数据传递给`array_view`构造函数不复制在 GPU 上，这一点与`array`构造函数。 相反，数据复制到加速器内核函数执行时。 因此，如果创建两个`array_view`对象使用相同的数据，同时`array_view`对象引用同一内存空间。 当执行此操作时，必须同步任何多线程的访问。 使用的主要优点`array_view`类是移动数据时才有必要。

### <a name="comparison-of-array-and-arrayview"></a>array 和 array_view 的比较

下表总结了相似之处和之间的差异`array`和`array_view`类。

|描述|array 类|array_view 类|
|-----------------|-----------------|-----------------------|
|什么时候确定级别|在编译时。|在编译时。|
|什么时候确定范围|在运行时。|在运行时。|
|形状|矩形。|矩形。|
|数据存储|是数据容器。|是数据包装器。|
|复制|在定义的显式和深层复制。|当内核函数访问时进行隐式复制。|
|数据检索|通过将数组数据复制回 CPU 线程上的对象。|通过直接访问`array_view`对象或调用[array_view:: synchronize 方法](reference/array-view-class.md#synchronize)才能继续访问原始容器上的数据。|

### <a name="shared-memory-with-array-and-arrayview"></a>对数组和 array_view 共享的内存

共享的内存是在 CPU 和加速器可以访问的内存。 使用共享内存消除或显著降低 CPU 和快捷键之间复制数据的开销。 尽管共享内存，但不能由 CPU 和加速器同时访问，这样会导致未定义的行为。

`array` 对象可以用于指定对使用共享内存进行精细控制，如果关联的加速器支持。 快捷键是否支持共享的内存由 accelerator [supports_cpu_shared_memory](reference/accelerator-class.md#supports_cpu_shared_memory)属性，它返回**true**支持共享的内存时。 如果支持共享的内存，则默认值[access_type 枚举](reference/concurrency-namespace-enums-amp.md#access_type)对于内存分配快捷键由`default_cpu_access_type`属性。 默认情况下`array`并`array_view`对象采用相同`access_type`相关联的主数据库`accelerator`。

通过设置[array:: cpu_access_type 数据成员](reference/array-class.md#cpu_access_type)属性的`array`显式，您可以细化的控制如何共享内存使用，以便您可以优化适用于硬件的性能的应用特征，基于其计算内核的内存访问模式。 `array_view`反映了相同`cpu_access_type`作为`array`是与其相关联; 或者，如果 array_view 时没有使用数据源，其`access_type`反映首次导致其分配存储的环境。 也就是说，如果主机 (CPU) 首先访问它，然后其行为就像它创建通过 CPU 数据源和共享`access_type`的`accelerator_view`通过捕获关联; 但是，如果首次访问`accelerator_view`，则它的行为，就好像通过创建`array`上，创建`accelerator_view`，并共享`array`的`access_type`。

下面的代码示例演示如何确定默认快捷键是否支持共享的内存，并创建具有不同 cpu_access_type 配置的多个数组。

```cpp
#include <amp.h>
#include <iostream>

using namespace Concurrency;

int main()
{
    accelerator acc = accelerator(accelerator::default_accelerator);

    // Early out if the default accelerator doesn’t support shared memory.
    if (!acc.supports_cpu_shared_memory)
    {
        std::cout << "The default accelerator does not support shared memory" << std::endl;
        return 1;
    }

    // Override the default CPU access type.
    acc.default_cpu_access_type = access_type_read_write

    // Create an accelerator_view from the default accelerator. The
    // accelerator_view inherits its default_cpu_access_type from acc.
    accelerator_view acc_v = acc.default_view;

    // Create an extent object to size the arrays.
    extent<1> ex(10);

    // Input array that can be written on the CPU.
    array<int, 1> arr_w(ex, acc_v, access_type_write);

    // Output array that can be read on the CPU.
    array<int, 1> arr_r(ex, acc_v, access_type_read);

    // Read-write array that can be both written to and read from on the CPU.
    array<int, 1> arr_rw(ex, acc_v, access_type_read_write);
}
```

## <a name="executing-code-over-data-parallelforeach"></a>对数据执行代码: parallel_for_each

[Parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each)函数定义你想要针对中的数据在快捷键上运行的代码`array`或`array_view`对象。 请考虑本主题的简介中的以下代码。

```cpp
#include <amp.h>
#include <iostream>
using namespace concurrency;

void AddArrays() {
    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5] = {0, 0, 0, 0, 0};

    array_view<int, 1> a(5, aCPP);
    array_view<int, 1> b(5, bCPP);
    array_view<int, 1> sum(5, sumCPP);

    parallel_for_each(
        sum.extent,
        [=](index<1> idx) restrict(amp)
        {
            sum[idx] = a[idx] + b[idx];
        }
    );

    for (int i = 0; i < 5; i++) {
        std::cout << sum[i] << "\n";
    }
}
```

`parallel_for_each`方法采用两个参数，计算域和 lambda 表达式。

*计算域*是`extent`对象或`tiled_extent`定义要创建并行执行的线程组的对象。 计算域中每个元素生成一个线程。 在这种情况下，`extent`对象是一维的并具有五个元素。 因此，启动了五个线程。

*Lambda 表达式*定义每个线程上运行的代码。 Capture 子句`[=]`，指定 lambda 表达式的主体通过值，在这种情况下访问所有捕获的变量`a`， `b`，和`sum`。 在此示例中，参数列表创建一维`index`名为变量`idx`。 值`idx[0]`是中的第一个线程为 0，将会增加一个在每个后续线程中。 `restrict(amp)`指示，只有的子集C++语言的C++AMP 可以加快使用。  对有限制修饰符的函数的限制中所述[限制 (C++ AMP)](../../cpp/restrict-cpp-amp.md)。 有关详细信息，请参阅， [Lambda 表达式语法](../../cpp/lambda-expression-syntax.md)。

Lambda 表达式可以包括要执行的代码也可以调用单独的核函数。 核函数必须包含`restrict(amp)`修饰符。 下面的示例等效于上述示例中，但它会调用单独的核函数。

```cpp
#include <amp.h>
#include <iostream>
using namespace concurrency;

void AddElements(
    index<1> idx,
    array_view<int, 1> sum,
    array_view<int, 1> a,
    array_view<int, 1> b) restrict(amp) {
    sum[idx] = a[idx] + b[idx];
}

void AddArraysWithFunction() {

    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5] = {0, 0, 0, 0, 0};

    array_view<int, 1> a(5, aCPP);
    array_view<int, 1> b(5, bCPP);
    array_view<int, 1> sum(5, sumCPP);

    parallel_for_each(
        sum.extent,
        [=](index<1> idx) restrict(amp) {
            AddElements(idx, sum, a, b);
        }
    );

    for (int i = 0; i < 5; i++) {
        std::cout << sum[i] << "\n";
    }
}
```

## <a name="accelerating-code-tiles-and-barriers"></a>加速代码：平铺和屏障

可以通过使用平铺来获取额外的加速。 平铺将线程划分为相等的矩形子集或*磁贴*。 确定合适的平铺大小根据您的数据集和您编码的算法。 对于每个线程，您可以访问*全局*相对于整个数据元素的位置`array`或`array_view`并访问*本地*平铺的位置。 使用本地索引值可以简化你的代码，因为无需编写代码，以便转换到本地的索引值从全局。 若要使用平铺，调用[extent:: tile 方法](reference/extent-class.md#tile)中的计算域上`parallel_for_each`方法，并使用[tiled_index](../../parallel/amp/reference/tiled-index-class.md) lambda 表达式中的对象。

在典型的应用程序，以某种方式相关的磁贴中的元素和代码必须访问和跟踪在平铺之间的值。 使用[tile_static 关键字](../../cpp/tile-static-keyword.md)关键字和[tile_barrier:: wait 方法](reference/tile-barrier-class.md#wait)来实现此目的。 具有的变量**tile_static**关键字具有作用域是整个平铺，并为每个磁贴创建变量的实例。 必须处理的平铺线程访问该变量的同步。 [Tile_barrier:: wait 方法](reference/tile-barrier-class.md#wait)停止执行当前线程，直到平铺中的所有线程都达到到调用`tile_barrier::wait`。 因此可以通过使用平铺间累积值**tile_static**变量。 然后可以完成任何需要访问所有值的计算。

下图表示排列磁贴中的数据采样的二维数组。

![平铺范围中的值](../../parallel/amp/media/camptiledgridexample.png "平铺范围中的值")

下面的代码示例使用上面的关系图中的采样数据。 这段代码通过平铺中值的平均值替换平铺中的每个值。

```cpp
// Sample data:
int sampledata[] = {
    2, 2, 9, 7, 1, 4,
    4, 4, 8, 8, 3, 4,
    1, 5, 1, 2, 5, 2,
    6, 8, 3, 2, 7, 2};

// The tiles:
// 2 2    9 7    1 4
// 4 4    8 8    3 4
//
// 1 5    1 2    5 2
// 6 8    3 2    7 2

// Averages:
int averagedata[] = {
    0, 0, 0, 0, 0, 0,
    0, 0, 0, 0, 0, 0,
    0, 0, 0, 0, 0, 0,
    0, 0, 0, 0, 0, 0,
};

array_view<int, 2> sample(4, 6, sampledata);

array_view<int, 2> average(4, 6, averagedata);

parallel_for_each(
    // Create threads for sample.extent and divide the extent into 2 x 2 tiles.
    sample.extent.tile<2,2>(),
        [=](tiled_index<2,2> idx) restrict(amp) {
        // Create a 2 x 2 array to hold the values in this tile.
        tile_static int nums[2][2];

        // Copy the values for the tile into the 2 x 2 array.
        nums[idx.local[1]][idx.local[0]] = sample[idx.global];

        // When all the threads have executed and the 2 x 2 array is complete, find the average.
        idx.barrier.wait();
        int sum = nums[0][0] + nums[0][1] + nums[1][0] + nums[1][1];

        // Copy the average into the array_view.
        average[idx.global] = sum / 4;
    });

for (int i = 0; i <4; i++) {
    for (int j = 0; j <6; j++) {
        std::cout << average(i,j) << " ";
    }
    std::cout << "\n";
}

// Output:
// 3 3 8 8 3 3
// 3 3 8 8 3 3
// 5 5 2 2 4 4
// 5 5 2 2 4 4
```

## <a name="math-libraries"></a>数学库

C++AMP 包括两个数学库。 中的双精度库[concurrency:: precise_math Namespace](../../parallel/amp/reference/concurrency-precise-math-namespace.md)为双精度函数提供支持。 它还支持单精度功能，尽管仍需要的硬件上的双精度支持。 其遵守[C99 规范 (ISO/IEC 9899)](https://go.microsoft.com/fwlink/p/?linkid=225887)。 快捷键必须支持完全双精度。 您可以确定它是否是通过检查的值[accelerator:: supports_double_precision 数据成员](reference/accelerator-class.md#supports_double_precision)。 快速数学库，请在[concurrency:: fast_math Namespace](../../parallel/amp/reference/concurrency-fast-math-namespace.md)，包含另一组数学函数。 这些函数，仅支持`float`操作数，更快地执行，但精确度不如双精度数学库中。 函数包含在\<amp_math.h > 标头文件和所有声明与`restrict(amp)`。 中的函数\<cmath > 标头文件导入这两`fast_math`和`precise_math`命名空间。 **限制**关键字用于区分\<cmath > 版本和C++AMP 版本。 以下代码计算使用快速方法，每个值的计算域中的以 10 为基数的对数。

```cpp
#include <amp.h>
#include <amp_math.h>
#include <iostream>
using namespace concurrency;

void MathExample() {

    double numbers[] = { 1.0, 10.0, 60.0, 100.0, 600.0, 1000.0 };
    array_view<double, 1> logs(6, numbers);

    parallel_for_each(
        logs.extent,
        [=] (index<1> idx) restrict(amp) {
            logs[idx] = concurrency::fast_math::log10(numbers[idx]);
        }
    );

    for (int i = 0; i < 6; i++) {
        std::cout << logs[i] << "\n";
    }
}
```

## <a name="graphics-library"></a>图形库

C++AMP 包括为加速的图形编程设计的图形库。 仅在支持本地图形功能的设备上使用此库。 方法是在[concurrency:: graphics Namespace](../../parallel/amp/reference/concurrency-graphics-namespace.md)和包含在\<amp_graphics.h > 标头文件。 图形库的关键组件包括：

- [texture 类](../../parallel/amp/reference/texture-class.md):纹理类可用于从内存或从文件创建纹理。 纹理类似于数组，因为它们包含的数据，并且它们类似于中的容器C++分配和复制构造方面的标准库。 有关详细信息，请参阅 [C++ 标准库容器](../../standard-library/stl-containers.md)。 有关模板参数`texture`类是元素类型和秩。 秩可以是 1、 2 或 3。 元素类型可以是本文稍后介绍的短矢量类型之一。

- [writeonly_texture_view 类](../../parallel/amp/reference/writeonly-texture-view-class.md):提供对任何纹理的只写访问。

- 短矢量库：定义一组的短矢量类型的长度 2、 3 和 4 上，基于**int**， `uint`， **float**， **double**， [norm](../../parallel/amp/reference/norm-class.md)，或[unorm](../../parallel/amp/reference/unorm-class.md)。

## <a name="universal-windows-platform-uwp-apps"></a>通用 Windows 平台 (UWP) 应用

像其他C++库，可以使用C++a m P UWP 应用程序中的。 这些文章介绍了如何包括C++在应用中使用创建的 AMP 代码C++， C#，Visual Basic 或 JavaScript:

- [在 UWP 应用中使用 C++ AMP](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)

- [演练：创建基本 Windows 运行时组件中的C++并从 JavaScript 调用它](https://go.microsoft.com/fwlink/p/?linkid=249077)

- [必应地图行程优化器，在 JavaScript 中的 Windows 应用商店应用和C++](https://go.microsoft.com/fwlink/p/?linkid=249078)

- [如何使用C++中的 AMPC#使用 Windows 运行时](https://go.microsoft.com/fwlink/p/?linkid=249080)

- [如何使用C++中的 AMPC#](https://go.microsoft.com/fwlink/p/?linkid=249081)

- [从托管代码调用本机函数](../../dotnet/calling-native-functions-from-managed-code.md)

## <a name="c-amp-and-concurrency-visualizer"></a>C++ AMP 和并发可视化工具

并发可视化工具包括用于分析的性能的支持C++AMP 代码。 这些文章介绍了这些功能：

- [GPU 活动关系图](/visualstudio/profiling/gpu-activity-graph)

- [GPU 活动（分页）](/visualstudio/profiling/gpu-activity-paging)

- [GPU 活动（此进程）](/visualstudio/profiling/gpu-activity-this-process)

- [GPU 活动（其他进程）](/visualstudio/profiling/gpu-activity-other-processes)

- [通道（线程视图）](/visualstudio/profiling/channels-threads-view)

- [分析C++使用并发可视化工具的 AMP 代码](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/03/09/analyzing-c-amp-code-with-the-concurrency-visualizer/)

## <a name="performance-recommendations"></a>性能建议

模数和除法的无符号整数具有性能明显优于模数和除法的有符号整数。 我们建议使用尽可能的无符号的整数。

## <a name="see-also"></a>请参阅

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[Lambda 表达式语法](../../cpp/lambda-expression-syntax.md)<br/>
[参考 (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)<br/>
[本机代码博客中的并行编程](https://go.microsoft.com/fwlink/p/?linkid=238472)
