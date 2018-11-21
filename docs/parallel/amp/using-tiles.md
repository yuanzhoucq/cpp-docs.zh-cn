---
title: 使用平铺
ms.date: 11/19/2018
ms.assetid: acb86a86-2b7f-43f1-8fcf-bcc79b21d9a8
ms.openlocfilehash: ede62c80a83b5f5fc1d691bf52dde67140e68246
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2018
ms.locfileid: "52176089"
---
# <a name="using-tiles"></a>使用平铺

可以使用平铺来最大化应用程序加速。 平铺将线程划分为相等的矩形子集或*磁贴*。 如果您使用合适的平铺大小和平铺的算法，您可以在 c + + AMP 代码中获取更多加速。 平铺的基本组件包括：

- `tile_static` 变量。 平铺的主要优点是从性能提升`tile_static`访问。 中的数据的访问权限`tile_static`内存可以明显快于访问全局空间中的数据 (`array`或`array_view`对象)。 实例`tile_static`变量，将创建的每个磁贴和磁贴中的所有线程都都可以访问该变量。 在典型的平铺算法中，数据复制到`tile_static`一次从全局内存的内存，然后从访问很多时候`tile_static`内存。

- [tile_barrier:: wait 方法](reference/tile-barrier-class.md#wait)。 调用`tile_barrier::wait`挂起当前线程的执行，直到同一平铺中线程的所有调用`tile_barrier::wait`。 不能保证线程将在中运行，只能确保平铺中的任何线程将执行之后调用的顺序`tile_barrier::wait`之前的所有线程都达到调用。 这意味着，通过使用`tile_barrier::wait`方法中，你可以在磁贴的磁贴的基础，而不是在线程的线程的基础上执行任务。 典型的平铺算法有代码来初始化`tile_static`将整个磁贴的内存后跟调用`tile_barrer::wait`。 下面的代码`tile_barrier::wait`包含需要访问所有的计算`tile_static`值。

- 本地和全局索引。 您可以访问相对于整个线程的索引`array_view`或`array`对象和平铺的索引。 使用本地索引可以使代码更易阅读和调试。 通常情况下，使用本地索引访问`tile_static`变量和全局索引访问`array`和`array_view`变量。

- [tiled_extent 类](../../parallel/amp/reference/tiled-extent-class.md)并[tiled_index 类](../../parallel/amp/reference/tiled-index-class.md)。 您使用`tiled_extent`对象而不是`extent`对象中`parallel_for_each`调用。 您使用`tiled_index`对象而不是`index`对象中`parallel_for_each`调用。

若要利用平铺的您的算法必须计算域划分为磁贴，然后复制到磁贴数据`tile_static`变量以提高访问速度。

## <a name="example-of-global-tile-and-local-indices"></a>示例中的全局、 平铺和本地索引

下图表示排列在 2x3 平铺中的数据的 8x9 矩阵。

![8&#45;通过&#45;9 矩阵划分为 2&#45;的&#45;3 个磁贴](../../parallel/amp/media/usingtilesmatrix.png "8&#45;的&#45;9 矩阵划分为 2&#45;的&#45;3 个磁贴")

下面的示例显示全局、 平铺和本地索引此平铺矩阵。 `array_view`通过使用类型的元素创建对象`Description`。 `Description`持有的全局、 平铺和本地索引矩阵中的元素。 在调用代码`parallel_for_each`设置的全局值、 磁贴和本地索引的每个元素。 该输出显示中的值`Description`结构。

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

void main() {
    TilingDescription();
    char wait;
    std::cin >> wait;
}
```

该示例的主要工作是在定义中的`array_view`对象，并向调用`parallel_for_each`。

1. 向量`Description`结构复制到 8x9`array_view`对象。

2. `parallel_for_each`方法调用与`tiled_extent`对象作为计算域。 `tiled_extent`对象创建通过调用`extent::tile()`方法的`descriptions`变量。 对调用的类型参数`extent::tile()`， `<2,3>`，指定创建 2x3 平铺。 因此，8x9 矩阵平铺为 12 个图块、 四个行和三个列。

3. `parallel_for_each`方法通过使用调用`tiled_index<2,3>`对象 (`t_idx`) 作为索引。 索引的类型参数 (`t_idx`) 必须与匹配的类型参数的计算域 (`descriptions.extent.tile< 2, 3>()`)。

4. 每个线程执行时，索引`t_idx`返回有关哪个磁贴的线程是中的信息 (`tiled_index::tile`属性) 以及平铺中线程的位置 (`tiled_index::local`属性)。

## <a name="tile-synchronizationtilestatic-and-tilebarrierwait"></a>磁贴同步 — tile_static 和 tile_barrier:: wait

前面的示例说明了平铺布局和索引，但不是本身非常有用。  磁贴是必不可少的算法和利用漏洞攻击的一部分时，平铺变得有用`tile_static`变量。 因为磁贴中的所有线程都有权`tile_static`变量，调用`tile_barrier::wait`用于同步对`tile_static`变量。 虽然平铺中线程的所有有权访问`tile_static`变量，没有平铺中线程的执行顺序并未保证。 下面的示例演示如何使用`tile_static`变量和`tile_barrier::wait`方法来计算每个平铺的平均值。 以下是理解此示例的密钥：

1. RawData 存储在 8x8 矩阵中。

2. 平铺大小是 2x2。 这将创建的磁贴的 4x4 网格和平均值可以通过使用存储在 4 x 4 矩阵`array`对象。 有只有有限的数量的可以捕获由 AMP 限制的函数中引用的类型。 `array`类是其中之一。

3. 通过使用定义矩阵大小和样本大小`#define`语句，因为的类型参数`array`， `array_view`， `extent`，和`tiled_index`必须是常数值。 此外可以使用`const int static`声明。 作为另一个好处，很容易更改示例尺寸以计算平均超过 4 × 4 磁贴。

4. 一个`tile_static`2x2 浮点值的数组声明每个磁贴。 尽管该声明是为每个线程的代码路径中，只有一个数组为矩阵中每个磁贴创建。

5. 没有要将值复制到每个磁贴中的代码行`tile_static`数组。 为每个线程的值复制到的数组后的线程上, 将停止执行的调用由于`tile_barrier::wait`。

6. 如果所有平铺中线程已达到屏障，可以计算平均值。 由于针对每个线程执行的代码，没有`if`语句，即仅计算一个线程上的平均值。 该平均值存储在平均值变量。 屏障是实质上是通过磁贴中，控制计算的构造，可能会使用一样使用`for`循环。

7. 中的数据`averages`变量，因为它是`array`对象，必须复制回主机。 此示例使用向量转换运算符。

8. 在完整的示例中，可以将 SAMPLESIZE 更改为 4，并执行正确的代码而无需任何其他更改。

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

可能尝试创建`tile_static`名为变量`total`并递增该变量为每个线程，像这样：

```cpp
// Do not do this.
tile_static float total;
total += matrix[t_idx];
t_idx.barrier.wait();

averages(t_idx.tile[0],t_idx.tile[1]) /= (float) (SAMPLESIZE* SAMPLESIZE);
```

这种方法的第一个问题是`tile_static`变量不能有初始值设定项。 第二个问题是分配给上是一个争用条件`total`，因为所有平铺中线程顺序不分先后有权访问该变量。 可以编写为只允许一个线程访问每个关卡处总数，按如下所示的算法。 但是，此解决方案不是可扩展的。

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

## <a name="memory-fences"></a>内存屏障

有两种类型的内存访问都必须同步，全局内存访问和`tile_static`内存访问。 一个`concurrency::array`对象仅分配全局内存。 一个`concurrency::array_view`可以引用全局内存`tile_static`内存，或两者，具体取决于构造方式。  有两种必须同步的内存：

- 全局内存

- `tile_static`

一个*内存界定*可确保内存访问可用于其他线程在线程平铺，并且内存访问根据程序顺序执行。 若要确保这一点，编译器和处理器重新排序读取和写入界定。 在 c + + AMP 中内存界定创建调用这些方法之一：

- [tile_barrier:: wait 方法](reference/tile-barrier-class.md#wait)： 创建界定全局和`tile_static`内存。

- [tile_barrier:: wait_with_all_memory_fence 方法](reference/tile-barrier-class.md#wait_with_all_memory_fence)： 创建界定全局和`tile_static`内存。

- [tile_barrier:: wait_with_global_memory_fence 方法](reference/tile-barrier-class.md#wait_with_global_memory_fence)： 创建仅全局内存界定。

- [tile_barrier:: wait_with_tile_static_memory_fence 方法](reference/tile-barrier-class.md#wait_with_tile_static_memory_fence)： 创建唯一界定`tile_static`内存。

调用需要可以提高您的应用程序性能的特定限制。 关卡类型影响如何编译器和硬件重新排列语句。 例如，如果你使用全局内存界定，它将应用仅为是全局内存访问并因此，编译器和硬件可能重新排序读取和写入到`tile_static`上隔离的两个方面的变量。

在下一步的示例中，屏障同步写入`tileValues`、`tile_static`变量。 在此示例中，`tile_barrier::wait_with_tile_static_memory_fence`而不是调用`tile_barrier::wait`。

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

## <a name="see-also"></a>请参阅

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[tile_static 关键字](../../cpp/tile-static-keyword.md)
