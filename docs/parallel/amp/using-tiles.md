---
title: "使用平铺 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: acb86a86-2b7f-43f1-8fcf-bcc79b21d9a8
caps.latest.revision: 18
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用平铺
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您可以使用平铺来最大化应用程序加速。  平铺将线程划分为相等的矩形子集或*图块*。  如果您使用合适的平铺大小和平铺的算法，则可以通过 C\+\+ AMP 代码获得更多加速。  平铺的基本组件是：  
  
-   `tile_static` 变量。  平铺的主要好处是从 `tile_static` 访问获得的性能。  访问 `tile_static` 内存数据要比访问全局聊天室中的数据快得多（`array` 或 `array_view` 对象）。  `tile_static` 变量的实例为每个平铺而创建，且平铺中的所有线程都可以访问该变量。  在典型的平铺算法中，将数据从全局内存一次复制到 `tile_static` 内存中，然后就可以从 `tile_static` 内存进行多次访问。  
  
-   [tile\_barrier::wait 方法](../Topic/tile_barrier::wait%20Method.md).  调用 `tile_barrier::wait` 将挂起当前线程，直到同一平铺中的所有线程都达到 `tile_barrier::wait` 的调用。  您无法确保线程的运行顺序，只能确保平铺中的线程不会执行到对 `tile_barrier::wait` 的调用后，直到所有线程都运行到该调用。  这意味着通过使用 `tile_barrier::wait` 方法，你可以基于图块而非线程来执行任务。  典型的平铺算法有代码可初始化整个平铺的 `tile_static` 内存，然后再调用 `tile_barrer::wait`。  遵循 `tile_barrier::wait` 的代码包含需要访问所有 `tile_static` 值的计算。  
  
-   本地和全局索引。  您可以访问相对于整个 `array_view` 或 `array` 对象的线程索引以及相对于平铺的索引。  使用局部索引可使代码更易阅读和调试。  通常情况下，你使用本地索引访问 `tile_static` 变量，使用全局索引访问 `array` 和 `array_view` 变量。  
  
-   [tiled\_extent 类](../../parallel/amp/reference/tiled-extent-class.md) 和 [tiled\_index 类](../../parallel/amp/reference/tiled-index-class.md)。  在 `parallel_for_each` 调用中使用 `tiled_extent` 对象而不是 `extent` 对象。  在 `parallel_for_each` 调用中使用 `tiled_index` 对象而非 `index` 对象。  
  
 要利用平铺，你的算法必须将计算域划分为图块，然后将图块数据复制到 `tile_static` 变量，从而加快访问速度。  
  
## 全局、图块和本地索引示例  
 下面的关系图表示以 2x3 图块排列的数据的 8x9 矩阵。  
  
 ![已划分为 2x3 图块的 8x9 矩阵](../../parallel/amp/media/usingtilesmatrix.png "UsingTilesMatrix")  
  
 下面的示例显示此平铺矩阵的全局、平铺和本地索引。  `array_view` 对象使用 `Description` 类型的元素进行创建。  `Description` 保留矩阵中元素的全局、平铺和本地索引。  对 `parallel_for_each` 的调用中的代码设置每个元素的全局、平铺和本地索引的值。  输出在 `Description` 结构中显示值。  
  
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
    int colorValue = (color == 0) ? 4 : 2;  
    SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), colorValue);  
}  
  
// A helper function for formatting the output.  
void SetConsoleSize(int height, int width) {  
    COORD coord; coord.X = width; coord.Y = height;  
    SetConsoleScreenBufferSize(GetStdHandle(STD_OUTPUT_HANDLE), coord);  
    SMALL_RECT* rect = new SMALL_RECT();  
    rect->Left = 0; rect->Top = 0; rect->Right = width; rect->Bottom = height;  
    SetConsoleWindowInfo(GetStdHandle(STD_OUTPUT_HANDLE), true, rect);  
}  
  
// This method creates an 8x9 matrix of Description structures. In the call to parallel_for_each, the structure is updated   
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
  
 该示例的主要任务在 `array_view` 对象的定义和对 `parallel_for_each` 的调用中。  
  
1.  `Description` 结构向量被复制到 8x9 `array_view` 对象。  
  
2.  当 `tiled_extent` 对象作为计算域时调用 `parallel_for_each` 方法。  `tiled_extent`对象通过调用 `descriptions` 变量的 `extent::tile()` 方法创建。  `extent::tile()` 的调用的参数类型，`<2,3>`，指定创建 2x3 个图块。  因此，该 8x9 矩阵平铺为四行三列的 12 个图块。  
  
3.  将 `tiled_index<2,3>` 对象 \(`t_idx`\) 用作索引来调用 `parallel_for_each` 方法。  索引 \(`t_idx`\) 的类型参数必须与计算域 \(`descriptions.extent.tile< 2, 3>()`\) 的类型参数匹配。  
  
4.  执行每个线程时，索引 `t_idx` 都会返回有关线程位于哪个平铺的信息（`tiled_index::tile` 属性）以及平铺中线程的位置信息（`tiled_index::local` 属性）。  
  
## 图块 Synchronization\-tile\_static 和 tile\_barrier::wait  
 上一个示例说明了平铺布局和索引，但是，本身不是非常有用的。当图块对算法必不可少并利用 `tile_static` 变量时，平铺变得非常有用。  由于平铺中的所有线程都可以访问 `tile_static` 变量，所以 `tile_barrier::wait` 的调用用于同步对 `tile_static` 变量的访问。  虽然平铺中的所有线程都可以访问 `tile_static` 变量，但平铺中线程的执行顺序并未保证。  下面的示例显示如何使用 `tile_static` 变量和 `tile_barrier::wait` 方法计算每个平铺的平均值。  以下是理解此示例的关键：  
  
1.  rawData 存储在 8x8 矩阵中。  
  
2.  平铺大小是 2x2。  这将创建一个 4x4 图块网格，并且通过使用 `array` 对象可以将平均值存储在一个 4x4 矩阵中。  通过引用 AMP 限制的函数，你仅能捕获有限数目的类型。  `array` 类是其中之一。  
  
3.  因为 `array`、`array_view`、`extent` 和 `tiled_index` 的类型参数必须是常数值，所以通过使用 `#define` 语句可定义矩阵大小和样本大小。  也可以使用`const int static`声明。  另一个优点如下：更改示例尺寸以计算 4x4 平铺的平均值是不重要的。  
  
4.  `tile_static` 2x2 浮点值数组针对每个平铺进行声明。  尽管该声明存在于每个线程的代码路径中，但只有一个数组为矩阵中的每个平铺而创建。  
  
5.  有一行代码可将每个图块中的值复制到 `tile_static` 数组。  对于每个线程，在将该值复制到数组后，由于对 `tile_barrier::wait` 进行调用，因此线程上的执行停止。  
  
6.  如果所有平铺线程都已达到屏障，就可以计算平均值。  由于代码为每个线程执行，因此 `if` 语句仅在一个线程上计算平均值。  该平均值存储在平均值变量中。  关卡实质上是通过平铺控制计算的构造，尽可能使用 `for` 循环。  
  
7.  因为 `averages` 变量中的数据是 `array` 对象，因此，它必须复制回主机。  此示例使用向量转换运算符。  
  
8.  在完整的示例中，您可以将 SAMPLESIZE 更改为 4，然后代码无需任何更改就可正确执行。  
  
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
  
## 争用条件  
 它可能尝试创建名为 `total` 的 `tile_static` 变量并增加每个线程的该变量，如下所示：  
  
```cpp  
  
// Do not do this.  
tile_static float total;  
total += matrix[t_idx];  
t_idx.barrier.wait();  
averages(t_idx.tile[0],t_idx.tile[1]) /= (float) (SAMPLESIZE * SAMPLESIZE);  
  
```  
  
 此方法的第一个问题是 `tile_static` 变量不具有初始值设定项。  第二个问题是对 `total` 的分配上存在争用条件，因为平铺中的所有线程都可以访问该变量（无特殊顺序）。  您可以对算法进行编程以便在每个关卡处只允许一个线程进行总的访问，如下所示。  但是，此解决方案不可扩展。  
  
```cpp  
  
// Do not do this.  
tile_static float total;  
if (t_idx.local[0] == 0 && t_idx.local[1] == 0) {  
    total = matrix[t_idx];  
}  
t_idx.barrier.wait();  
  
if (t_idx.local[0] == 0 && t_idx.local[1] == 1) {  
    total += matrix[t_idx];  
}  
t_idx.barrier.wait();  
  
// etc.  
  
```  
  
## 内存屏障  
 有两种必须同步的内存访问，即全局内存访问和 `tile_static` 内存访问。  `concurrency::array` 对象仅分配全局内存。  `concurrency::array_view` 可引用全局内存和\/或`tile_static` 内存，具体取决于其结构。有两种必须同步的内存：  
  
-   全局内存  
  
-   `tile_static`  
  
 “内存界定”确保内存访问对线程平铺中的其他线程可用，并且内存访问根据程序排序执行。  为确保这一点，编译器和处理器不对界定中的读取和编写重新排序。  在 C\+\+ AMP 中，调用这些方法中的其中一个会产生内存界定。  
  
-   [tile\_barrier::wait 方法](../Topic/tile_barrier::wait%20Method.md)：创建全局和 `tile_static` 内存界定。  
  
-   [tile\_barrier::wait\_with\_all\_memory\_fence 方法](../Topic/tile_barrier::wait_with_all_memory_fence%20Method.md)：创建全局和 `tile_static` 内存界定。  
  
-   [tile\_barrier::wait\_with\_global\_memory\_fence 方法](../Topic/tile_barrier::wait_with_global_memory_fence%20Method.md)：仅创建全局内存界定。  
  
-   [tile\_barrier::wait\_with\_tile\_static\_memory\_fence 方法](../Topic/tile_barrier::wait_with_tile_static_memory_fence%20Method.md)：仅创建 `tile_static` 内存界定。  
  
 调用您需要的特定限制可提高应用程序的性能。  关卡类型影响编译器和硬件如何重新排列语句。  例如，如果使用全局内存界定（仅适用于全局内存存取），因此编译器和硬件可能会在界定两侧重新排序读取和写入 `tile_static` 变量。  
  
 在下一个示例中，关卡将写入与 `tileValues`（一个 `tile_static` 变量）同步。  在此示例中，调用 `tile_barrier::wait_with_tile_static_memory_fence`，而非 `tile_barrier::wait`。  
  
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
  
```  
  
## 请参阅  
 [C\+\+ AMP \(C\+\+ Accelerated Massive Parallelism\)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)   
 [tile\_static 关键字](../../cpp/tile-static-keyword.md)