---
title: 使用平铺
ms.date: 11/19/2018
ms.assetid: acb86a86-2b7f-43f1-8fcf-bcc79b21d9a8
ms.openlocfilehash: 6c935134e033d12fc140c8d377ef59d0b47265fc
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518252"
---
# <a name="using-tiles"></a>使用平铺

您可以使用平铺来最大化应用程序的加速。 平铺将线程划分为相等的矩形子集或*图块*。 如果使用合适的磁贴大小和平铺算法，则可以从C++ AMP 代码获取更多加速。 平铺的基本组件是：

- `tile_static` 变量。 平铺的主要优点是 `tile_static` 访问的性能增益。 访问 `tile_static` 内存中的数据比访问全局空间（`array` 或 `array_view` 对象）中的数据的速度要快得多。 为每个图块创建 `tile_static` 变量的实例，并且该图块中的所有线程都可以访问该变量。 在典型的平铺算法中，将数据从全局内存复制到 `tile_static` 内存一次，然后从 `tile_static` 内存进行多次访问。

- [tile_barrier：： Wait 方法](reference/tile-barrier-class.md#wait)。 对 `tile_barrier::wait` 的调用会挂起当前线程的执行，直到同一磁贴中的所有线程都达到对 `tile_barrier::wait`的调用为止。 你不能保证线程将在中运行的顺序，只有磁贴中的线程不会在调用 `tile_barrier::wait` 之后执行，直到所有线程均已到达调用。 这意味着，通过使用 `tile_barrier::wait` 方法，你可以按平铺方式（而不是按线程）来执行任务。 典型的平铺算法有代码来初始化整个磁贴的 `tile_static` 内存，然后调用 `tile_barrer::wait`。 后面 `tile_barrier::wait` 的代码包含需要访问所有 `tile_static` 值的计算。

- 本地和全局索引。 您可以访问相对于整个 `array_view` 或 `array` 对象的线程索引和与磁贴相关的索引。 使用本地索引可以使代码更易于读取和调试。 通常，使用本地索引访问 `tile_static` 变量，使用全局索引访问 `array` 和 `array_view` 变量。

- [Tiled_extent 类](../../parallel/amp/reference/tiled-extent-class.md)和[tiled_index 类](../../parallel/amp/reference/tiled-index-class.md)。 在 `parallel_for_each` 调用中使用 `tiled_extent` 对象，而不是 `extent` 对象。 在 `parallel_for_each` 调用中使用 `tiled_index` 对象，而不是 `index` 对象。

若要利用磁贴，你的算法必须将计算域分区为磁贴，然后将磁贴数据复制到 `tile_static` 变量中，以加快访问速度。

## <a name="example-of-global-tile-and-local-indices"></a>全局、磁贴和本地索引示例

下图表示在2x3 图块中排列的数据的8x9 矩阵。

![8&#45;x&#45;9 矩阵分成 2&#45;x&#45;3 个磁贴](../../parallel/amp/media/usingtilesmatrix.png "8&#45;x&#45;9 矩阵分成 2&#45;x&#45;3 个磁贴")

下面的示例显示此平铺矩阵的全局、平铺和本地索引。 `array_view` 对象是通过使用 `Description`类型的元素创建的。 `Description` 包含矩阵中元素的全局、平铺和本地索引。 调用中的代码 `parallel_for_each` 设置每个元素的全局、平铺和本地索引的值。 输出显示 `Description` 结构中的值。

```cpp
#include <iostream>
#include <iomanip>
#include <Windows.h>
#include <amp.h>
using namespace concurrency;

const int ROWS = 8;
const int COLS = 9;

// tileRow and tileColumn specify the tile that each thread is in.
// globalRow and globalColumn specify the location of the thread in the array_view.
// localRow and localColumn specify the location of the thread relative to the tile.
struct Description {
    int value;
    int tileRow;
    int tileColumn;
    int globalRow;
    int globalColumn;
    int localRow;
    int localColumn;
};

// A helper function for formatting the output.
void SetConsoleColor(int color) {
    int colorValue = (color == 0)  4 : 2;
    SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), colorValue);
}

// A helper function for formatting the output.
void SetConsoleSize(int height, int width) {
    COORD coord;

    coord.X = width;
    coord.Y = height;
    SetConsoleScreenBufferSize(GetStdHandle(STD_OUTPUT_HANDLE), coord);

    SMALL_RECT* rect = new SMALL_RECT();
    rect->Left = 0;
    rect->Top = 0;
    rect->Right = width;
    rect->Bottom = height;
    SetConsoleWindowInfo(GetStdHandle(STD_OUTPUT_HANDLE), true, rect);
}

// This method creates an 8x9 matrix of Description structures.
// In the call to parallel_for_each, the structure is updated
// with tile, global, and local indices.
void TilingDescription() {
    // Create 72 (8x9) Description structures.
    std::vector<Description> descs;
    for (int i = 0; i < ROWS * COLS; i++) {
        Description d = {i, 0, 0, 0, 0, 0, 0};
        descs.push_back(d);
    }

    // Create an array_view from the Description structures.
    extent<2> matrix(ROWS, COLS);
    array_view<Description, 2> descriptions(matrix, descs);

    // Update each Description with the tile, global, and local indices.
    parallel_for_each(descriptions.extent.tile< 2, 3>(),
        [=] (tiled_index< 2, 3> t_idx) restrict(amp)
    {
        descriptions[t_idx].globalRow = t_idx.global[0];
        descriptions[t_idx].globalColumn = t_idx.global[1];
        descriptions[t_idx].tileRow = t_idx.tile[0];
        descriptions[t_idx].tileColumn = t_idx.tile[1];
        descriptions[t_idx].localRow = t_idx.local[0];
        descriptions[t_idx].localColumn= t_idx.local[1];
    });

    // Print out the Description structure for each element in the matrix.
    // Tiles are displayed in red and green to distinguish them from each other.
    SetConsoleSize(100, 150);
    for (int row = 0; row < ROWS; row++) {
        for (int column = 0; column < COLS; column++) {
            SetConsoleColor((descriptions(row, column).tileRow + descriptions(row, column).tileColumn) % 2);
            std::cout << "Value: " << std::setw(2) << descriptions(row, column).value << "      ";
        }
        std::cout << "\n";

        for (int column = 0; column < COLS; column++) {
            SetConsoleColor((descriptions(row, column).tileRow + descriptions(row, column).tileColumn) % 2);
            std::cout << "Tile:   " << "(" << descriptions(row, column).tileRow << "," << descriptions(row, column).tileColumn << ")  ";
        }
        std::cout << "\n";

        for (int column = 0; column < COLS; column++) {
            SetConsoleColor((descriptions(row, column).tileRow + descriptions(row, column).tileColumn) % 2);
            std::cout << "Global: " << "(" << descriptions(row, column).globalRow << "," << descriptions(row, column).globalColumn << ")  ";
        }
        std::cout << "\n";

        for (int column = 0; column < COLS; column++) {
            SetConsoleColor((descriptions(row, column).tileRow + descriptions(row, column).tileColumn) % 2);
            std::cout << "Local:  " << "(" << descriptions(row, column).localRow << "," << descriptions(row, column).localColumn << ")  ";
        }
        std::cout << "\n";
        std::cout << "\n";
    }
}

int main() {
    TilingDescription();
    char wait;
    std::cin >> wait;
}
```

该示例的主要工作是 `array_view` 对象的定义和对 `parallel_for_each`的调用。

1. `Description` 结构的矢量将复制到 8x9 `array_view` 对象中。

2. 使用 `tiled_extent` 对象作为计算域调用 `parallel_for_each` 方法。 `tiled_extent` 对象是通过调用 `descriptions` 变量的 `extent::tile()` 方法创建的。 对 `extent::tile()`（`<2,3>`）调用的类型参数指定已创建2x3 磁贴。 因此，8x9 矩阵平铺为12个图块、四行和三列。

3. 使用 `tiled_index<2,3>` 对象（`t_idx`）作为索引来调用 `parallel_for_each` 方法。 索引的类型参数（`t_idx`）必须与计算域（`descriptions.extent.tile< 2, 3>()`）的类型参数匹配。

4. 执行每个线程时，索引 `t_idx` 将返回有关线程所在的图块（`tiled_index::tile` 属性）和图块中的线程位置（`tiled_index::local` 属性）的信息。

## <a name="tile-synchronizationtile_static-and-tile_barrierwait"></a>磁贴同步-tile_static 和 tile_barrier：： wait

前面的示例演示了磁贴布局和索引，但本身并没有什么用处。  磁贴在磁贴是算法的一部分并利用 `tile_static` 变量时变得非常有用。 因为磁贴中的所有线程都可以访问 `tile_static` 变量，所以对 `tile_barrier::wait` 的调用用于同步对 `tile_static` 变量的访问。 尽管磁贴中的所有线程都可以访问 `tile_static` 变量，但没有保证在磁贴中执行线程的顺序。 下面的示例演示如何使用 `tile_static` 变量和 `tile_barrier::wait` 方法来计算每个图块的平均值。 下面是了解该示例的关键：

1. RawData 存储在8x8 矩阵中。

2. 磁贴大小为2x2。 这将创建图块的4x4 网格，并使用 `array` 对象将平均值存储在4x4 矩阵中。 在 AMP 限制的函数中，只能通过引用来捕获有限数量的类型。 `array` 类是其中之一。

3. 矩阵大小和样本大小是使用 `#define` 语句定义的，因为 `array`、`array_view`、`extent`和 `tiled_index` 的类型参数必须是常数值。 你还可以使用 `const int static` 声明。 另一种方法是，更改样本大小以计算4x4 磁贴的平均值是很简单的。

4. 为每个图块声明一个 `tile_static` 2x2 数组的 float 值。 尽管声明位于每个线程的代码路径中，但对于矩阵中的每个图块，只会创建一个数组。

5. 有一行代码将每个磁贴中的值复制到 `tile_static` 数组。 对于每个线程，将值复制到数组后，由于调用 `tile_barrier::wait`，线程上的执行将停止。

6. 当磁贴中的所有线程都达到屏障时，就可以计算平均值。 因为代码针对每个线程执行，所以有一个 `if` 语句只计算一个线程上的平均值。 平均值存储在平均变量中。 关卡实质上是按平铺控制计算的构造，与使用 `for` 循环非常相似。

7. `averages` 变量中的数据，因为它是一个 `array` 对象，因此必须将其复制回主机。 此示例使用向量转换运算符。

8. 在完整的示例中，可以将 SAMPLESIZE 更改为4，并正确执行代码而无需进行任何其他更改。

```cpp
#include <iostream>
#include <amp.h>
using namespace concurrency;

#define SAMPLESIZE 2
#define MATRIXSIZE 8
void SamplingExample() {

    // Create data and array_view for the matrix.
    std::vector<float> rawData;
    for (int i = 0; i < MATRIXSIZE * MATRIXSIZE; i++) {
        rawData.push_back((float)i);
    }
    extent<2> dataExtent(MATRIXSIZE, MATRIXSIZE);
    array_view<float, 2> matrix(dataExtent, rawData);

    // Create the array for the averages.
    // There is one element in the output for each tile in the data.
    std::vector<float> outputData;
    int outputSize = MATRIXSIZE / SAMPLESIZE;
    for (int j = 0; j < outputSize * outputSize; j++) {
        outputData.push_back((float)0);
    }
    extent<2> outputExtent(MATRIXSIZE / SAMPLESIZE, MATRIXSIZE / SAMPLESIZE);
    array<float, 2> averages(outputExtent, outputData.begin(), outputData.end());

    // Use tiles that are SAMPLESIZE x SAMPLESIZE.
    // Find the average of the values in each tile.
    // The only reference-type variable you can pass into the parallel_for_each call
    // is a concurrency::array.
    parallel_for_each(matrix.extent.tile<SAMPLESIZE, SAMPLESIZE>(),
        [=, &averages] (tiled_index<SAMPLESIZE, SAMPLESIZE> t_idx) restrict(amp)
    {
        // Copy the values of the tile into a tile-sized array.
        tile_static float tileValues[SAMPLESIZE][SAMPLESIZE];
        tileValues[t_idx.local[0]][t_idx.local[1]] = matrix[t_idx];

        // Wait for the tile-sized array to load before you calculate the average.
        t_idx.barrier.wait();

        // If you remove the if statement, then the calculation executes for every
        // thread in the tile, and makes the same assignment to averages each time.
        if (t_idx.local[0] == 0 && t_idx.local[1] == 0) {
            for (int trow = 0; trow < SAMPLESIZE; trow++) {
                for (int tcol = 0; tcol < SAMPLESIZE; tcol++) {
                    averages(t_idx.tile[0],t_idx.tile[1]) += tileValues[trow][tcol];
                }
            }
            averages(t_idx.tile[0],t_idx.tile[1]) /= (float) (SAMPLESIZE * SAMPLESIZE);
        }
    });

    // Print out the results.
    // You cannot access the values in averages directly. You must copy them
    // back to a CPU variable.
    outputData = averages;
    for (int row = 0; row < outputSize; row++) {
        for (int col = 0; col < outputSize; col++) {
            std::cout << outputData[row*outputSize + col] << " ";
        }
        std::cout << "\n";
    }
    // Output for SAMPLESSIZE = 2 is:
    //  4.5  6.5  8.5 10.5
    // 20.5 22.5 24.5 26.5
    // 36.5 38.5 40.5 42.5
    // 52.5 54.5 56.5 58.5

    // Output for SAMPLESIZE = 4 is:
    // 13.5 17.5
    // 45.5 49.5
}

int main() {
    SamplingExample();
}
```

## <a name="race-conditions"></a>争用条件

创建一个名为 `total` 的 `tile_static` 变量并为每个线程递增该变量可能是很有吸引力的，如下所示：

```cpp
// Do not do this.
tile_static float total;
total += matrix[t_idx];
t_idx.barrier.wait();

averages(t_idx.tile[0],t_idx.tile[1]) /= (float) (SAMPLESIZE* SAMPLESIZE);
```

此方法的第一个问题是 `tile_static` 变量不能有初始值设定项。 第二个问题是对 `total`的赋值存在争用条件，因为磁贴中的所有线程都可以访问变量，而不是特定的顺序。 您可以计划一种算法，使其仅允许一个线程访问每个屏障的总数，如下所示。 但是，此解决方案是不可扩展的。

```cpp
// Do not do this.
tile_static float total;
if (t_idx.local[0] == 0&& t_idx.local[1] == 0) {
    total = matrix[t_idx];
}
t_idx.barrier.wait();

if (t_idx.local[0] == 0&& t_idx.local[1] == 1) {
    total += matrix[t_idx];
}
t_idx.barrier.wait();

// etc.
```

## <a name="memory-fences"></a>内存时限

必须同步两种类型的内存访问，即全局内存访问和 `tile_static` 内存访问。 `concurrency::array` 对象只分配全局内存。 `concurrency::array_view` 可以引用全局内存和/或 `tile_static` 内存，具体取决于它的构造方式。  必须同步两种类型的内存：

- 全局内存

- `tile_static`

*内存隔离*确保内存访问可用于线程磁贴中的其他线程，并且根据程序顺序执行内存访问。 为了确保这一点，编译器和处理器不会将读取和写入操作重新排序到整个防护。 在C++ AMP 中，通过调用以下方法之一来创建内存隔离：

- [tile_barrier：： Wait 方法](reference/tile-barrier-class.md#wait)：在全局内存和 `tile_static` 内存周围创建一个防护。

- [tile_barrier：： Wait_with_all_memory_fence 方法](reference/tile-barrier-class.md#wait_with_all_memory_fence)：在全局内存和 `tile_static` 内存周围创建一个防护。

- [tile_barrier：： Wait_with_global_memory_fence 方法](reference/tile-barrier-class.md#wait_with_global_memory_fence)：只围绕全局内存创建一个防护。

- [tile_barrier：： Wait_with_tile_static_memory_fence 方法](reference/tile-barrier-class.md#wait_with_tile_static_memory_fence)：仅围绕 `tile_static` 内存创建一个防护。

调用所需的特定防护可以提高应用程序的性能。 关卡类型影响编译器和硬件重新排序语句的方式。 例如，如果你使用全局内存隔离，则它仅适用于全局内存访问，因此，编译器和硬件可能会将读取和写入操作重新排列到隔离的双方 `tile_static` 变量。

在下一个示例中，屏障将写入操作同步到 `tileValues`，即 `tile_static` 变量。 在此示例中，调用了 `tile_barrier::wait_with_tile_static_memory_fence` 而不是 `tile_barrier::wait`。

```cpp
// Using a tile_static memory fence.
parallel_for_each(matrix.extent.tile<SAMPLESIZE, SAMPLESIZE>(),
    [=, &averages] (tiled_index<SAMPLESIZE, SAMPLESIZE> t_idx) restrict(amp)
{
    // Copy the values of the tile into a tile-sized array.
    tile_static float tileValues[SAMPLESIZE][SAMPLESIZE];
    tileValues[t_idx.local[0]][t_idx.local[1]] = matrix[t_idx];

    // Wait for the tile-sized array to load before calculating the average.
    t_idx.barrier.wait_with_tile_static_memory_fence();

    // If you remove the if statement, then the calculation executes
    // for every thread in the tile, and makes the same assignment to
    // averages each time.
    if (t_idx.local[0] == 0&& t_idx.local[1] == 0) {
        for (int trow = 0; trow <SAMPLESIZE; trow++) {
            for (int tcol = 0; tcol <SAMPLESIZE; tcol++) {
                averages(t_idx.tile[0],t_idx.tile[1]) += tileValues[trow][tcol];
            }
        }
    averages(t_idx.tile[0],t_idx.tile[1]) /= (float) (SAMPLESIZE* SAMPLESIZE);
    }
});
```

## <a name="see-also"></a>另请参阅

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[tile_static 关键字](../../cpp/tile-static-keyword.md)
