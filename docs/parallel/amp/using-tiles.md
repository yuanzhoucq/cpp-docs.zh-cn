---
title: "使用磁贴 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: acb86a86-2b7f-43f1-8fcf-bcc79b21d9a8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aed7ed0ed32f73927f3755c0ba3733aaef084818
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="using-tiles"></a>使用平铺
可用平铺来最大化你的应用程序加速。 平铺将线程划分为相等的矩形子集或*磁贴*。 如果你使用相应的磁贴大小和平铺的算法，你可以在 c + + AMP 代码中获取更多的加速。 平铺的基本组件包括：  
  
- `tile_static`变量。 平铺的主要优点是带来的性能提升`tile_static`访问。 访问中的数据`tile_static`内存可能很有权访问在全局空间中的数据比快很多 (`array`或`array_view`对象)。 实例`tile_static`为每个图块，创建变量并将磁贴中的所有线程都有权访问该变量。 在典型的平铺算法中的数据复制到`tile_static`一次从全局内存的内存，并且从然后访问次数多`tile_static`内存。  
  
- [tile_barrier:: wait 方法](reference/tile-barrier-class.md#wait)。 调用`tile_barrier::wait`挂起当前线程的执行，直到所有相同的磁贴中的线程到达调用`tile_barrier::wait`。 你不能保证线程将在中运行，仅该磁贴中的无线程将执行之后调用的顺序`tile_barrier::wait`之前的所有线程都已达到调用。 这意味着，通过使用`tile_barrier::wait`方法，你可以在磁贴的磁贴基础，而不是线程的线程的基础上执行任务。 典型的平铺算法具有代码以初始化`tile_static`整个磁贴的内存跟调用`tile_barrer::wait`。 下面的代码`tile_barrier::wait`包含需要访问所有的计算`tile_static`值。  

  
-   本地和全局索引。 您有权访问的相对于整个线程索引`array_view`或`array`对象和相对于该磁贴的索引。 使用本地索引可以使你的代码易于阅读和调试。 通常，您可以使用本地索引访问`tile_static`变量和访问的全局索引`array`和`array_view`变量。  
  
- [tiled_extent 类](../../parallel/amp/reference/tiled-extent-class.md)和[tiled_index 类](../../parallel/amp/reference/tiled-index-class.md)。 你使用`tiled_extent`对象而不是`extent`对象在`parallel_for_each`调用。 你使用`tiled_index`对象而不是`index`对象在`parallel_for_each`调用。  
  
 若要充分利用平铺的您的算法必须计算域划分为磁贴，然后磁贴将数据复制到`tile_static`更快地访问的变量。  
  
## <a name="example-of-global-tile-and-local-indices"></a>示例的全局、 磁贴和本地索引  
 下图表示数据，排列在 2 x 3 磁贴 8 x 9 的矩阵。  
  
 ![8 &#45; 通过 &#45; 9 矩阵划分到 2 &#45; &#45; 3 磁贴](../../parallel/amp/media/usingtilesmatrix.png "usingtilesmatrix")  
  
 下面的示例显示全局、 磁贴，并此本地索引平铺的矩阵。 `array_view`对象创建的使用类型的元素`Description`。 `Description`包含全局，磁贴和矩阵中的元素的本地索引。 在调用代码`parallel_for_each`设置的全局值、 磁贴和每个元素的本地索引。 该输出显示中的值`Description`结构。  
  
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
  
 该示例的主要工作是中的定义`array_view`对象和对`parallel_for_each`。  
  
1.  向量的`Description`结构复制到 8 x 9`array_view`对象。  
  
2.  `parallel_for_each`方法调用与`tiled_extent`对象作为计算域。 `tiled_extent`对象通过调用创建`extent::tile()`方法`descriptions`变量。 类型参数的调用`extent::tile()`， `<2,3>`，指定创建 2 x 3 磁贴。 因此，8 x 9 矩阵平铺到 12 的磁贴、 四个行和三个列。  
  
3.  `parallel_for_each`方法调用通过使用`tiled_index<2,3>`对象 (`t_idx`) 作为索引。 类型参数的索引 (`t_idx`) 必须与匹配的类型参数的计算域 (`descriptions.extent.tile< 2, 3>()`)。  
  
4.  当执行每个线程时，索引`t_idx`返回信息有关的磁贴线程处于 (`tiled_index::tile`属性) 和在磁贴中线程的位置 (`tiled_index::local`属性)。  
  
## <a name="tile-synchronizationtilestatic-and-tilebarrierwait"></a>磁贴同步-tile_static 和 tile_barrier:: wait  
 前面的示例演示的磁贴布局和索引，但不是本身非常有用。  平铺将显得十分有用磁贴是不可或缺的一部分的算法和攻击`tile_static`变量。 由于将磁贴中的所有线程访问的`tile_static`变量，对调用`tile_barrier::wait`使用对访问进行同步`tile_static`变量。 尽管所有磁贴中的线程都可以访问`tile_static`变量，没有任何有保证的磁贴中的线程的执行顺序。 下面的示例演示如何使用`tile_static`变量和`tile_barrier::wait`方法来计算每个图块的平均值。 以下是了解该示例的密钥：  
  
1.  RawData 存储在 8x8 矩阵。  
  
2.  磁贴大小为 2 x 2。 这将创建的磁贴的 4 x 4 网格和平均值可以通过使用存储在 4 x 4 矩阵`array`对象。 有有限的数量的你可以通过 AMP 限制的函数中引用捕获的类型。 `array`类是其中之一。  
  
3.  通过使用定义的矩阵大小和样本大小`#define`语句，因为的类型参数`array`， `array_view`， `extent`，和`tiled_index`必须是常量值。 你还可以使用`const int static`声明。 作为一项额外权益，十分常见更改的样本大小来计算平均超过 4 x 4 磁贴。  
  
4.  A `tile_static` 2 x 2 浮点值的数组声明每个磁贴。 尽管该声明是在每个线程的代码路径，为矩阵中每个磁贴创建只有一个数组。  
  
5.  没有要将值复制到每个磁贴中的代码行`tile_static`数组。 为每个线程，该值被复制到数组中后, 线程执行将停止对的调用由于`tile_barrier::wait`。  
  
6.  在所有磁贴中的线程都已达到屏障，可以计算平均值。 针对每个线程执行的代码，因为没有`if`语句仅计算在一个线程上的平均值。 平均存储在平均值变量。 屏障是实质上是构造，用于通过在磁贴，来控制计算可能使用一样使用`for`循环。  
  
7.  中的数据`averages`变量，因为它是`array`对象，必须复制回主机。 此示例使用向量转换运算符。  
  
8.  在完整的示例中，您可以更改 SAMPLESIZE 为 4，并执行正确的代码而无需任何其他更改。  
  
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
 它可能是创建容易让人想到`tile_static`变量名为`total`和递增该变量为每个线程，如下：  
  
```cpp  
// Do not do this.  
tile_static float total;  
total += matrix[t_idx];  
t_idx.barrier.wait();

averages(t_idx.tile[0],t_idx.tile[1]) /= (float) (SAMPLESIZE* SAMPLESIZE);

 
```  
  
 使用此方法的第一个问题在于`tile_static`变量不能有初始值设定项。 第二个问题是分配给的上是一个争用条件`total`，因为所有磁贴中的线程有权访问该变量顺序不分先后。 你无法编程一种算法以仅允许一个线程访问的总金额在每个屏障，如下所示。 但是，此解决方案不是可扩展的。  
  
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
  
## <a name="memory-fences"></a>内存界定  
 有两种类型的内存存取，必须同步-全局内存访问和`tile_static`内存访问。 A`concurrency::array`对象分配仅全局内存。 A`concurrency::array_view`可以引用全局内存`tile_static`内存，或两者，具体取决于它的构造方式。  有两种类型的内存必须同步：  
  
-   全局内存  
  
- `tile_static`  
  
 A*内存界定*可确保访问可供其他线程中的线程磁贴，该内存，并且根据程序顺序执行访问该内存。 若要确保这一点，编译器和处理器不重新排列读取和写入围墙。 在 c + + AMP 内存界定创建通过调用这些方法之一：  
  

- [tile_barrier:: wait 方法](reference/tile-barrier-class.md#wait)： 创建这两围墙全局和`tile_static`内存。  
  
- [tile_barrier:: wait_with_all_memory_fence 方法](reference/tile-barrier-class.md#wait_with_all_memory_fence)： 创建这两围墙全局和`tile_static`内存。  
  
- [tile_barrier:: wait_with_global_memory_fence 方法](reference/tile-barrier-class.md#wait_with_global_memory_fence)： 创建围墙围绕仅全局内存。  
  
- [tile_barrier:: wait_with_tile_static_memory_fence 方法](reference/tile-barrier-class.md#wait_with_tile_static_memory_fence)： 创建解决唯一围墙`tile_static`内存。  

  
 调用特定围墙需要可以提高你的应用程序的性能。 屏障类型会影响编译器和硬件重新语句的排序。 例如，如果你使用全局内存围墙应用仅为全局内存访问，因此，编译器和硬件可能重新排序读取和写入到`tile_static`上围墙两条边的变量。  
  
 在下一步的示例中，屏障同步写入`tileValues`、`tile_static`变量。 在此示例中，`tile_barrier::wait_with_tile_static_memory_fence`而不是调用`tile_barrier::wait`。  
  
```cpp  
// Using a tile_static memory fence.  
parallel_for_each(matrix.extent.tile<SAMPLESIZE, SAMPLESIZE>(),  
 [=, &averages] (tiled_index<SAMPLESIZE, SAMPLESIZE> t_idx) restrict(amp)   
{ *// Copy the values of the tile into a tile-sized array.  
    tile_static float tileValues[SAMPLESIZE][SAMPLESIZE];  
    tileValues[t_idx.local[0]][t_idx.local[1]] = matrix[t_idx];  
 *// Wait for the tile-sized array to load before calculating the average.  
    t_idx.barrier.wait_with_tile_static_memory_fence();

 *// If you remove the if statement, then the calculation executes for every *// thread in the tile, and makes the same assignment to averages each time.  
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
 [C + + AMP (c + + Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)   
 [tile_static 关键字](../../cpp/tile-static-keyword.md)

