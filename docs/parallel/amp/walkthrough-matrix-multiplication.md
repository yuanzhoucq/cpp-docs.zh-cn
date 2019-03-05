---
title: 演练：矩阵乘法
ms.date: 11/19/2018
ms.assetid: 61172e8b-da71-4200-a462-ff3a908ab0cf
ms.openlocfilehash: 597ba0f47c7b081f62c82bf8e1ca01c286d35140
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57300968"
---
# <a name="walkthrough-matrix-multiplication"></a>演练：矩阵乘法

此分步演练演示如何使用 c + + AMP 加快执行矩阵乘法。 显示这两种算法，另一个不包含平铺，另一个使用平铺。

## <a name="prerequisites"></a>系统必备

开始之前：

- 读取[c + + AMP 概述](../../parallel/amp/cpp-amp-overview.md)。

- 读取[使用平铺](../../parallel/amp/using-tiles.md)。

- 请确保在计算机上安装的 Windows 7、 Windows 8、 Windows Server 2008 R2 或 Windows Server 2012。

### <a name="to-create-the-project"></a>要创建项目

1. 在 Visual Studio 中菜单栏上依次选择**文件** > **新建** > **项目**。

1. 下**已安装**在模板窗格中选择**Visual c + +**。

1. 选择**空项目**，输入*MatrixMultiply*中**名称**，然后再选择**确定**按钮。

1. 选择“下一步”按钮。

1. 在中**解决方案资源管理器**，打开快捷菜单**源文件**，然后选择**添加** > **新项**。

1. 在中**添加新项**对话框中，选择**c + + 文件 (.cpp)**，输入*MatrixMultiply.cpp*中**名称**框中，，然后选择**添加**按钮。

## <a name="multiplication-without-tiling"></a>而无需平铺的乘法

在本部分中，请考虑两个矩阵，A 和 B，按以下方式定义的乘法运算：

![3&#45;的&#45;2 矩阵 A](../../parallel/amp/media/campmatrixanontiled.png "3&#45;的&#45;2 矩阵 A")

![2&#45;的&#45;3 矩阵 B](../../parallel/amp/media/campmatrixbnontiled.png "2&#45;的&#45;3 矩阵 B")

一个是 3-2 矩阵，B 是 2-3 矩阵。 乘法 B 由一个产品是以下 3 x 3 矩阵。 该产品是相乘计算得出的一个按 B 元素通过元素的列的行。

![3&#45;的&#45;3 个产品矩阵](../../parallel/amp/media/campmatrixproductnontiled.png "3&#45;的&#45;3 个产品矩阵")

### <a name="to-multiply-without-using-c-amp"></a>要相乘而无需使用 c + + AMP

1. 打开 MatrixMultiply.cpp 并使用下面的代码替换现有代码。

```cpp
#include <iostream>

void MultiplyWithOutAMP() {
    int aMatrix[3][2] = {{1, 4}, {2, 5}, {3, 6}};
    int bMatrix[2][3] = {{7, 8, 9}, {10, 11, 12}};
    int product[3][3] = {{0, 0, 0}, {0, 0, 0}, {0, 0, 0}};

    for (int row = 0; row < 3; row++) {
        for (int col = 0; col < 3; col++) {
            // Multiply the row of A by the column of B to get the row, column of product.
            for (int inner = 0; inner < 2; inner++) {
                product[row][col] += aMatrix[row][inner] * bMatrix[inner][col];
            }
            std::cout << product[row][col] << "  ";
        }
        std::cout << "\n";
    }
}

void main() {
    MultiplyWithOutAMP();
    getchar();
}
```

   该算法是一个简单的实现定义的矩阵乘法。 它不使用任何并行或线程算法以缩短计算时间。

1. 在菜单栏上，依次选择“文件” > “全部保存”。

1. 选择**F5**键盘快捷方式，以便开始调试并验证输出是否正确。

1. 选择**Enter**退出该应用程序。

### <a name="to-multiply-by-using-c-amp"></a>要通过使用 c + + AMP 相乘

1. 在 MatrixMultiply.cpp，添加以下代码之前`main`方法。

```cpp
void MultiplyWithAMP() {
    int aMatrix[] = { 1, 4, 2, 5, 3, 6 };
    int bMatrix[] = { 7, 8, 9, 10, 11, 12 };
    int productMatrix[] = { 0, 0, 0, 0, 0, 0, 0, 0, 0 };

    array_view<int, 2> a(3, 2, aMatrix);

    array_view<int, 2> b(2, 3, bMatrix);

    array_view<int, 2> product(3, 3, productMatrix);

    parallel_for_each(product.extent,
        [=] (index<2> idx) restrict(amp) {
            int row = idx[0];
            int col = idx[1];
            for (int inner = 0; inner <2; inner++) {
                product[idx] += a(row, inner)* b(inner, col);
            }
        });

    product.synchronize();

    for (int row = 0; row <3; row++) {
        for (int col = 0; col <3; col++) {
            //std::cout << productMatrix[row*3 + col] << "  ";
            std::cout << product(row, col) << "  ";
        }
        std::cout << "\n";
    }
}
```

   AMP 代码类似于非 AMP 代码。 在调用`parallel_for_each`启动一个线程中每个元素`product.extent`，并替换`for`循环，分别针对行和列。 在行和列单元格的值现已推出`idx`。 您可以访问的元素`array_view`通过使用对象`[]`运算符和索引变量，或`()`运算符和行和列的变量。 该示例演示了这两种方法。 `array_view::synchronize`方法复制的值`product`返回到变量`productMatrix`变量。

1. 添加以下`include`和`using`MatrixMultiply.cpp 顶部的语句。

```cpp
#include <amp.h>
using namespace concurrency;
```

1. 修改`main`方法来调用`MultiplyWithAMP`方法。

```cpp
void main() {
    MultiplyWithOutAMP();
    MultiplyWithAMP();
    getchar();
}
```

1. 选择**Ctrl**+**F5**键盘快捷方式，以便开始调试并验证输出是否正确。

1. 选择**空格键**退出该应用程序。

## <a name="multiplication-with-tiling"></a>使用平铺的乘法

平铺是为大小相等的子集，作为磁贴，这些分区数据的技术。 以下三项更改时使用平铺。

- 您可以创建`tile_static`变量。 中的数据访问`tile_static`空间可以是比访问全局空间中的数据要快好几倍。 实例`tile_static`变量，将创建的每个磁贴和磁贴中的所有线程都都可以访问该变量。 平铺的主要优点是性能提高`tile_static`访问。

- 您可以调用[tile_barrier:: wait](reference/tile-barrier-class.md#wait)方法来停止所有线程在一个磁贴中在指定的代码行。 不能保证线程将在中，仅运行的顺序所有一个平铺中线程将停止于调用`tile_barrier::wait`它们继续执行之前。

- 有权访问的线程相对于整个索引`array_view`对象和平铺的索引。 通过使用本地索引，可以使更易阅读和调试代码。

若要充分利用平铺的矩阵乘法中，该算法必须矩阵划分为磁贴，然后复制到磁贴数据`tile_static`变量以提高访问速度。 在此示例中，矩阵划分为大小相等的 submatrices。 乘以 submatrices 找到产品。 两个矩阵和其产品在此示例中为：

![4&#45;的&#45;4 矩阵 A](../../parallel/amp/media/campmatrixatiled.png "4&#45;的&#45;4 矩阵 A")

![4&#45;的&#45;4 矩阵 B](../../parallel/amp/media/campmatrixbtiled.png "4&#45;的&#45;4 矩阵 B")

![4&#45;的&#45;4 产品矩阵](../../parallel/amp/media/campmatrixproducttiled.png "4&#45;的&#45;4 产品矩阵")

矩阵划分为四个 2 x 2 矩阵，定义如下：

![4&#45;通过&#45;4 矩阵一个分区为 2&#45;的&#45;2 子&#45;矩阵](../../parallel/amp/media/campmatrixapartitioned.png "4&#45;通过&#45;4 矩阵 A 到第 2 分区&#45;的&#45;2 子&#45;矩阵")

![4&#45;通过&#45;4 矩阵 B 到第 2 分区&#45;通过&#45;2 子&#45;矩阵](../../parallel/amp/media/campmatrixbpartitioned.png "4&#45;通过&#45;到第 2 分区 4 矩阵 B&#45;的&#45;2 子&#45;矩阵")

产品 A 和 B 现在可以编写和计算，如下所示：

![4&#45;通过&#45;4 矩阵 B 到第 2 分区&#45;的&#45;2 子&#45;矩阵](../../parallel/amp/media/campmatrixproductpartitioned.png "4&#45;的&#45;4 矩阵 B 到第 2 分区&#45;的&#45;2 子&#45;矩阵")

因为矩阵`a`通过`h`2 x 2 矩阵的所有产品，它们的总和还 2 x 2 矩阵。 它还遵循的一个产品，而 B 是 4 × 4 矩阵按预期方式。 若要快速检查算法，计算的第一行中的元素，在产品中的第一列的值。 在示例中，这个位置是元素的值在第一行、 第一列`ae + bg`。 只需计算的第一列、 第一行`ae`和`bg`对于每个术语。 该值用于`ae`是`(1 * 1) + (2 * 5) = 11`。 值`bg`是`(3 * 1) + (4 * 5) = 23`。 最终值是`11 + 23 = 34`，这是正确。

若要实现此算法，该代码：

- 使用`tiled_extent`对象而不是`extent`对象中`parallel_for_each`调用。

- 使用`tiled_index`对象而不是`index`对象中`parallel_for_each`调用。

- 创建`tile_static`变量以保存 submatrices。

- 使用`tile_barrier::wait`方法来停止 submatrices 的产品的计算线程。

### <a name="to-multiply-by-using-amp-and-tiling"></a>若要将乘以使用 AMP 和平铺

1. 在 MatrixMultiply.cpp，添加以下代码之前`main`方法。

```cpp
void MultiplyWithTiling() {
    // The tile size is 2.
    static const int TS = 2;

    // The raw data.
    int aMatrix[] = { 1, 2, 3, 4, 5, 6, 7, 8, 1, 2, 3, 4, 5, 6, 7, 8 };
    int bMatrix[] = { 1, 2, 3, 4, 5, 6, 7, 8, 1, 2, 3, 4, 5, 6, 7, 8 };
    int productMatrix[] = { 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 };

    // Create the array_view objects.
    array_view<int, 2> a(4, 4, aMatrix);
    array_view<int, 2> b(4, 4, bMatrix);
    array_view<int, 2> product(4, 4, productMatrix);

    // Call parallel_for_each by using 2x2 tiles.
    parallel_for_each(product.extent.tile<TS, TS>(),
        [=] (tiled_index<TS, TS> t_idx) restrict(amp)
        {
            // Get the location of the thread relative to the tile (row, col)
            // and the entire array_view (rowGlobal, colGlobal).
            int row = t_idx.local[0];
            int col = t_idx.local[1];
            int rowGlobal = t_idx.global[0];
            int colGlobal = t_idx.global[1];
            int sum = 0;

            // Given a 4x4 matrix and a 2x2 tile size, this loop executes twice for each thread.
            // For the first tile and the first loop, it copies a into locA and e into locB.
            // For the first tile and the second loop, it copies b into locA and g into locB.
            for (int i = 0; i < 4; i += TS) {
                tile_static int locA[TS][TS];
                tile_static int locB[TS][TS];
                locA[row][col] = a(rowGlobal, col + i);
                locB[row][col] = b(row + i, colGlobal);
                // The threads in the tile all wait here until locA and locB are filled.
                t_idx.barrier.wait();

                // Return the product for the thread. The sum is retained across
                // both iterations of the loop, in effect adding the two products
                // together, for example, a*e.
                for (int k = 0; k < TS; k++) {
                    sum += locA[row][k] * locB[k][col];
                }

                // All threads must wait until the sums are calculated. If any threads
                // moved ahead, the values in locA and locB would change.
                t_idx.barrier.wait();
                // Now go on to the next iteration of the loop.
            }

            // After both iterations of the loop, copy the sum to the product variable by using the global location.
            product[t_idx.global] = sum;
        });

    // Copy the contents of product back to the productMatrix variable.
    product.synchronize();

    for (int row = 0; row <4; row++) {
        for (int col = 0; col <4; col++) {
            // The results are available from both the product and productMatrix variables.
            //std::cout << productMatrix[row*3 + col] << "  ";
            std::cout << product(row, col) << "  ";
        }
        std::cout << "\n";
    }
}
```

    This example is significantly different than the example without tiling. The code uses these conceptual steps:

    1. 将磁贴 [0，0] 的元素复制`a`到`locA`。 将磁贴 [0，0] 的元素复制`b`到`locB`。 请注意，`product`平铺，不`a`和`b`。 因此，使用全局索引访问`a, b`，和`product`。 对调用`tile_barrier::wait`至关重要。 停止所有平铺中线程之前`locA`和`locB`填充。

    2. 乘`locA`并`locB`并将结果放入`product`。

    3. 将磁贴 [0，1] 的元素复制`a`到`locA`。 将磁贴 [1，0] 的元素复制`b`到`locB`。

    4. 乘`locA`并`locB`并将其添加到已在结果`product`。

    5. 磁贴 [0，0] 的乘法操作已完成。

    6. 重复的其他四个磁贴。 没有专门为磁贴没有编制索引，线程可以按任意顺序执行。 每个线程执行时，`tile_static`适当地为每个磁贴创建变量，是对的调用和`tile_barrier::wait`控制在程序流。

    7. 如您仔细检查该算法，请注意，每个 submatrix 加载到`tile_static`内存两次。 该数据传输需要时间。 但是，当数据在后`tile_static`内存中，对数据的访问是要快得多。 因为计算产品需要重复的访问 submatrices 中的值，则整体性能提升。 为每个算法，需要通过试验来找到最佳算法和磁贴大小。

         在非 AMP 和非磁贴示例中，每个元素 A 和 B 从计算乘积的全局内存访问四次。 在磁贴的示例中，每个元素进行访问两次从全局内存和四次`tile_static`内存。 这不是显著的性能提升。 但是，如果 A 和 B 是 1024 x 1024 矩阵和图块大小是 16，会有显著的性能提升。 在这种情况下，每个元素将复制到`tile_static`内存仅 16 次，从访问`tile_static`内存 1024年时间。

2. 修改 main 方法来调用`MultiplyWithTiling`方法，如下所示。

```cpp
void main() {
    MultiplyWithOutAMP();
    MultiplyWithAMP();
    MultiplyWithTiling();
    getchar();
}
```

3. 选择**Ctrl**+**F5**键盘快捷方式，以便开始调试并验证输出是否正确。

4. 选择**空间**栏退出该应用程序。

## <a name="see-also"></a>请参阅

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[演练：调试 c + + AMP 应用程序](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)
