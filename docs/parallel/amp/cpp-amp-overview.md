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
ms.openlocfilehash: 5c9819c1d9167bea9a9bedeef2ac44798d5a121f
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404842"
---
# <a name="c-amp-overview"></a>C++ AMP 概述

C++ Accelerated Massive Parallelism （C++ AMP）通过利用数据并行硬件（如图形处理单元（GPU））来加速 c + + 代码的执行。 通过使用 C++ AMP，你可以为多维数据算法编写代码，以便可以通过在异类硬件上使用并行来加速执行。 C++ AMP 编程模型包括多维数组、索引、内存传输、平铺和数学函数库。 你可以使用 C++ AMP 语言扩展来控制数据在 CPU 和 GPU 之间的移动方式，从而提高性能。

## <a name="system-requirements"></a>系统要求

- Windows 7 或更高版本

- Windows Server 2008 R2 或更高版本

- DirectX 11 功能级别11.0 或更高版本的硬件

- 对于在软件模拟器上进行调试，需要 Windows 8 或 Windows Server 2012。 对于在硬件上进行的调试，您必须为图形卡安装驱动程序。 有关详细信息，请参阅[调试 GPU 代码](/visualstudio/debugger/debugging-gpu-code)。

- 注意： ARM64 目前不支持 AMP。

## <a name="introduction"></a>简介

以下两个示例演示了 C++ AMP 的主要组件。 假设要添加 2 1 维数组的对应元素。 例如，你可能想要添加 `{1, 2, 3, 4, 5}` 和 `{6, 7, 8, 9, 10}` 以获取 `{7, 9, 11, 13, 15}` 。 如果不使用 C++ AMP，则可以编写以下代码来添加数字并显示结果。

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

- 数据：数据由三个数组组成。 全部具有相同的秩（一）和长度（5）。

- 迭代：第一 `for` 循环提供一种机制来循环访问数组中的元素。 要执行以计算总和的代码包含在第一个 `for` 块中。

- Index： `idx` 变量访问数组的各个元素。

使用 C++ AMP，可以改为编写以下代码。

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

存在相同的基本元素，但使用 C++ AMP 构造：

- 数据：使用 c + + 数组构造三个 C++ AMP [array_view](../../parallel/amp/reference/array-view-class.md)对象。 提供四个值来构造 `array_view` 对象：数据值、级别、元素类型以及 `array_view` 每个维度中的对象的长度。 秩和类型作为类型参数进行传递。 数据和长度作为构造函数参数传递。 在此示例中，传递给构造函数的 c + + 数组是一维的。 秩和长度用于构造对象中数据的矩形形状 `array_view` ，数据值用于填充数组，而这些数据值用于填充数组。 运行时库还包括[数组类，该类](../../parallel/amp/reference/array-class.md)具有一个类似于类的接口， `array_view` 本文稍后将对此进行讨论。

- 迭代： [Parallel_for_each 函数（C++ AMP）](reference/concurrency-namespace-functions-amp.md#parallel_for_each)提供了一种机制来循环访问数据元素或*计算域*。 在此示例中，计算域由指定 `sum.extent` 。 要执行的代码包含在 lambda 表达式或*核心函数*中。 `restrict(amp)`指示只使用 C++ AMP 的 c + + 语言的子集。

- Index：[索引类](../../parallel/amp/reference/index-class.md)变量（ `idx` ）被声明为与对象的排名相匹配的一个级别 `array_view` 。 使用索引可以访问对象的各个元素 `array_view` 。

## <a name="shaping-and-indexing-data-index-and-extent"></a>形成和索引数据: index 和 extent

在运行内核代码之前，必须定义数据值并声明数据的形状。 所有数据都被定义为数组（矩形），您可以定义该数组的秩（维数）。 数据可以是任何维度中的任何大小。

### <a name="index-class"></a>index 类

[Index 类](../../parallel/amp/reference/index-class.md) `array` `array_view` 通过将每个维度中原点的偏移量封装到一个对象中，在或对象中指定一个位置。 访问数组中的位置时，会将 `index` 对象传递给索引运算符， `[]` 而不是整数索引的列表。 您可以通过使用[array：： operator （）运算符](reference/array-class.md#operator_call)或[array_view：： Operator （）运算符](reference/array-view-class.md#operator_call)来访问每个维度中的元素。

下面的示例创建一个指定一维对象中第三个元素的一维索引 `array_view` 。 索引用于打印对象中的第三个元素 `array_view` 。 输出为3。

```cpp
int aCPP[] = {1, 2, 3, 4, 5};
array_view<int, 1> a(5, aCPP);

index<1> idx(2);

std::cout << a[idx] << "\n";
// Output: 3
```

下面的示例创建一个二维索引，该索引指定二维对象中第1行、第列 = 第2行的元素 `array_view` 。 构造函数中的第一个参数 `index` 是行组件，第二个参数是列组件。 输出为6。

```cpp
int aCPP[] = {1, 2, 3, 4, 5, 6};
array_view<int, 2> a(2, 3, aCPP);

index<2> idx(1, 2);

std::cout <<a[idx] << "\n";
// Output: 6
```

下面的示例创建一个三维索引，用于指定三维对象中深度 = 0、行 = 1 和列 = 3 的元素 `array_view` 。 请注意，第一个参数是深度组件，第二个参数是行组件，第三个参数是列组件。 输出为8。

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

[区类](../../parallel/amp/reference/extent-class.md)指定或对象的每个维度中的数据长度 `array` `array_view` 。 你可以创建一个范围，并使用它来创建 `array` 或 `array_view` 对象。 您还可以检索现有或对象的范围 `array` `array_view` 。 下面的示例输出对象的每个维度中区的长度 `array_view` 。

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

下面的示例创建一个 `array_view` 对象，该对象与上一示例中的对象具有相同的维度，但此示例使用 `extent` 对象，而不是在构造函数中使用显式参数 `array_view` 。

```cpp
int aCPP[] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24};
extent<3> e(2, 3, 4);

array_view<int, 3> a(e, aCPP);

std::cout << "The number of columns is " << a.extent[2] << "\n";
std::cout << "The number of rows is " << a.extent[1] << "\n";
std::cout << "The depth is " << a.extent[0] << "\n";
```

## <a name="moving-data-to-the-accelerator-array-and-array_view"></a>将数据移动到快捷键: array 和 array_view

用于将数据移动到快捷键的两个数据容器在运行库中定义。 它们是[数组类](../../parallel/amp/reference/array-class.md)和[array_view 类](../../parallel/amp/reference/array-view-class.md)。 `array`类是一个容器类，它在构造对象时创建数据的深层副本。 `array_view`类是一个包装类，它在内核函数访问数据时复制数据。 在源设备上需要数据时，会将数据复制回。

### <a name="array-class"></a>array 类

`array`构造对象时，如果使用包含指向数据集的指针的构造函数，则将在快捷键上创建数据的深层副本。 内核函数修改加速器上的副本。 核心函数的执行完成后，您必须将数据复制回源数据结构。 下面的示例将矢量中的每个元素乘以10。 内核函数完成后， `vector conversion operator` 使用将数据复制回矢量对象。

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

### <a name="array_view-class"></a>array_view 类

与 `array_view` 类的成员几乎相同 `array` ，但基础行为并不相同。 传递给 `array_view` 构造函数的数据不会复制到 GPU 上，因为它与 `array` 构造函数相同。 相反，在执行内核函数时，数据会复制到快捷键。 因此，如果您创建两个 `array_view` 使用相同数据的对象，则两个 `array_view` 对象都引用相同的内存空间。 执行此操作时，必须同步任意多线程访问。 使用类的主要优点 `array_view` 是仅在必要时才移动数据。

### <a name="comparison-of-array-and-array_view"></a>array 和 array_view 的比较

下表总结了和类之间的相似性和 `array` 差异 `array_view` 。

|说明|array 类|array_view 类|
|-----------------|-----------------|-----------------------|
|确定名次的时间|在编译时。|在编译时。|
|确定范围时|在运行时。|在运行时。|
|形状|进.|进.|
|数据存储|是一个数据容器。|为数据包装。|
|复制|定义中的显式副本和深层副本。|当核心函数访问时，隐式复制。|
|数据检索|将数组数据复制回 CPU 线程上的对象。|通过直接访问 `array_view` 对象或通过调用[array_view：： synchronize 方法](reference/array-view-class.md#synchronize)来继续访问原始容器上的数据。|

### <a name="shared-memory-with-array-and-array_view"></a>数组和 array_view 的共享内存

共享内存是可以由 CPU 和加速器访问的内存。 使用共享内存可消除或大大降低在 CPU 和加速器之间复制数据的开销。 尽管内存是共享的，但它不能同时由 CPU 和加速器进行访问，这样做会导致未定义的行为。

`array`如果关联的快捷键支持共享内存，则可以使用对象来指定对其使用的精细控制。 加速器是否支持共享内存取决于加速器的[supports_cpu_shared_memory](reference/accelerator-class.md#supports_cpu_shared_memory)属性，如果支持共享内存，该属性将返回**true** 。 如果支持共享内存，则加速器上内存分配的默认[Access_type 枚举](reference/concurrency-namespace-enums-amp.md#access_type)由 `default_cpu_access_type` 属性确定。 默认情况下， `array` 和 `array_view` 对象采用与 `access_type` 主关联的相同的 `accelerator` 。

通过显式设置[array：： Cpu_access_type 数据成员](reference/array-class.md#cpu_access_type)属性 `array` ，可以对使用共享内存的方式进行精细的控制，以便可以根据其计算内核的内存访问模式优化应用程序的性能特征。 的 `array_view` 反射与其 `cpu_access_type` 关联的相同 `array` ; 或者，如果 array_view 是在没有数据源的情况下构造的，则其 `access_type` 反映的是第一个导致其分配存储的环境。 也就是说，如果第一次被主机（CPU）访问，则其行为方式就像是通过 CPU 数据源创建的，并共享的是 `access_type` `accelerator_view` 通过捕获关联的; 但是，如果首次访问，则它的 `accelerator_view` 行为就像是在创建的上创建的， `array` `accelerator_view` 并且共享的 `array` `access_type` 。

下面的代码示例演示如何确定默认快捷键是否支持共享内存，然后创建多个具有不同 cpu_access_type 配置的数组。

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

## <a name="executing-code-over-data-parallel_for_each"></a>对数据执行代码: parallel_for_each

[Parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each)函数定义要在快捷键上针对或对象中的数据运行的代码 `array` `array_view` 。 请考虑本主题中的以下代码。

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

`parallel_for_each`方法采用两个参数：一个计算域和一个 lambda 表达式。

*计算域*是一个 `extent` 对象或 `tiled_extent` 对象，用于定义要为并行执行创建的一组线程。 为计算域中的每个元素生成一个线程。 在这种情况下，该 `extent` 对象为一维，并具有五个元素。 因此，启动了五个线程。

*Lambda 表达式*定义要在每个线程上运行的代码。 捕获子句 `[=]` 指定 lambda 表达式的主体通过值访问所有捕获的变量，在本例中为 `a` 、 `b` 和 `sum` 。 在此示例中，参数列表创建一个名为的一维 `index` 变量 `idx` 。 的值在 `idx[0]` 第一个线程中为0，并在每个后续线程中增加1。 `restrict(amp)`指示只使用 C++ AMP 的 c + + 语言的子集。  限制[（C++ AMP）](../../cpp/restrict-cpp-amp.md)中描述了具有限制修饰符的函数的限制。 有关详细信息，请参阅[Lambda 表达式语法](../../cpp/lambda-expression-syntax.md)。

Lambda 表达式可以包含要执行的代码，也可以调用单独的内核函数。 内核函数必须包含 `restrict(amp)` 修饰符。 下面的示例与前面的示例等效，但它调用单独的内核函数。

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

## <a name="accelerating-code-tiles-and-barriers"></a>加速代码: 平铺和屏障

您可以使用平铺获取更多加速。 平铺将线程划分为相等的矩形子集或*图块*。 根据数据集和要编码的算法，确定相应的磁贴大小。 对于每个线程，你可以访问相对于整个或的数据元素*全局*位置，并可访问与 `array` `array_view` 磁贴相关的*本地*位置。 使用本地索引值可以简化代码，因为无需编写代码来将索引值从 global 转换为本地。 若要使用平铺，请在方法中调用计算域上的[区：：磁贴方法](reference/extent-class.md#tile) `parallel_for_each` ，并使用 lambda 表达式中的[tiled_index](../../parallel/amp/reference/tiled-index-class.md)对象。

在典型的应用程序中，磁贴中的元素在某种程度上是相关的，代码必须访问和跟踪磁贴中的值。 使用[Tile_static 关键字](../../cpp/tile-static-keyword.md)关键字和[tile_barrier：： wait 方法](reference/tile-barrier-class.md#wait)完成此操作。 具有**tile_static**关键字的变量在整个磁贴中具有范围，并为每个图块创建变量实例。 必须处理对变量的平铺线程访问的同步。 [Tile_barrier：： Wait 方法](reference/tile-barrier-class.md#wait)将停止当前线程的执行，直到磁贴中的所有线程都已达到对的调用 `tile_barrier::wait` 。 因此，您可以使用**tile_static**变量在磁贴范围内累计值。 然后，可以完成任何需要访问所有值的计算。

下图表示一个二维数组，它在图块中进行排列。

![平铺范围中的索引值](../../parallel/amp/media/camptiledgridexample.png "平铺范围中的索引值")

下面的代码示例使用上图中的采样数据。 该代码会将磁贴中的每个值替换为磁贴中的值的平均值。

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

C++ AMP 包括两个数学库。 [Concurrency：:p Recise_math 命名空间](../../parallel/amp/reference/concurrency-precise-math-namespace.md)中的双精度库为双精度函数提供支持。 它还提供对单精度函数的支持，但仍需要对硬件进行双精度支持。 它符合[C99 规范（ISO/IEC 9899）](https://go.microsoft.com/fwlink/p/?linkid=225887)。 加速器必须支持完全双精度。 您可以通过检查 "[快捷键：： supports_double_precision" 数据成员](reference/accelerator-class.md#supports_double_precision)的值来确定它是否执行此操作。 [Concurrency：： Fast_math 命名空间](../../parallel/amp/reference/concurrency-fast-math-namespace.md)中的快速数学库包含另一组数学函数。 这些函数仅支持 `float` 操作数，执行速度更快，但不会精确到双精度数学库中的函数。 函数包含在 \<amp_math.h> 标头文件中，所有都是用进行声明的 `restrict(amp)` 。 \<cmath>标头文件中的函数将导入 `fast_math` 和 `precise_math` 命名空间。 **Restrict**关键字用于区分 \<cmath> 版本和 C++ AMP 版本。 下面的代码使用 fast 方法计算计算域中每个值的以10为底的对数。

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

C++ AMP 包含为加速图形编程而设计的图形库。 此库仅在支持本机图形功能的设备上使用。 方法位于[Concurrency：： Graphics 命名空间](../../parallel/amp/reference/concurrency-graphics-namespace.md)中，并包含在 \<amp_graphics.h> 标头文件中。 图形库的关键组件如下：

- [纹理类](../../parallel/amp/reference/texture-class.md)：可以使用纹理类从内存或文件创建纹理。 纹理类似于数组，因为它们包含数据，它们类似于 c + + 标准库中与赋值和复制构造有关的容器。 有关详细信息，请参阅 [C++ 标准库容器](../../standard-library/stl-containers.md)。 类的模板参数 `texture` 是元素类型和排名。 秩可以是1、2或3。 元素类型可以是在本文后面部分中描述的一种简短矢量类型。

- [Writeonly_texture_view 类](../../parallel/amp/reference/writeonly-texture-view-class.md)：提供对任何纹理的只写访问权限。

- Short 矢量库：定义一组基于**int**、 `uint` 、 **float**、 **double**、int64 或[unorm](../../parallel/amp/reference/unorm-class.md)的长度为2、3和4的短矢量类型[norm](../../parallel/amp/reference/norm-class.md)。

## <a name="universal-windows-platform-uwp-apps"></a>通用 Windows 平台 (UWP) 应用

与其他 c + + 库一样，你可以在 UWP 应用中使用 C++ AMP。 这些文章介绍了如何在使用 c + +、c #、Visual Basic 或 JavaScript 创建的应用中加入 C++ AMP 代码：

- [在 UWP 应用中使用 C++ AMP](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)

- [演练：使用 c + + 创建基本 Windows 运行时组件并从 JavaScript 中调用它](https://go.microsoft.com/fwlink/p/?linkid=249077)

- [必应地图行程优化器（JavaScript 和 c + + 中的 Windows 应用商店应用）](https://go.microsoft.com/fwlink/p/?linkid=249078)

- [如何使用 Windows 运行时从 c # 使用 C++ AMP](https://devblogs.microsoft.com/pfxteam/how-to-use-c-amp-from-c-using-winrt/)

- [如何使用 C C++ AMP#](https://devblogs.microsoft.com/pfxteam/how-to-use-c-amp-from-c/)

- [从托管代码调用本机函数](../../dotnet/calling-native-functions-from-managed-code.md)

## <a name="c-amp-and-concurrency-visualizer"></a>C++ AMP 和并发可视化工具

并发可视化工具支持分析 C++ AMP 代码的性能。 这些文章介绍了这些功能：

- [GPU 活动关系图](/visualstudio/profiling/gpu-activity-graph)

- [GPU 活动(分页)](/visualstudio/profiling/gpu-activity-paging)

- [GPU 活动(此进程)](/visualstudio/profiling/gpu-activity-this-process)

- [GPU 活动(其他进程)](/visualstudio/profiling/gpu-activity-other-processes)

- [通道（线程视图）](/visualstudio/profiling/channels-threads-view)

- [利用并发可视化工具分析 C++ AMP 代码](/archive/blogs/nativeconcurrency/analyzing-c-amp-code-with-the-concurrency-visualizer)

## <a name="performance-recommendations"></a>性能建议

无符号整数的模数和除法具有比带符号整数的模数和除法更好的性能。 建议尽可能使用无符号整数。

## <a name="see-also"></a>另请参阅

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[Lambda 表达式语法](../../cpp/lambda-expression-syntax.md)<br/>
[参考 (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)<br/>
[本机代码中的并行编程博客](https://go.microsoft.com/fwlink/p/?linkid=238472)
