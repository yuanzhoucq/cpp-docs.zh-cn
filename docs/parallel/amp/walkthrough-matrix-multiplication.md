---
title: 演练：矩阵乘法
ms.date: 04/23/2019
ms.assetid: 61172e8b-da71-4200-a462-ff3a908ab0cf
ms.openlocfilehash: 341800e258f89db340d206ebe04bc20d4763ad1a
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518486"
---
# <a name="walkthrough-matrix-multiplication"></a>演练：矩阵乘法

此分步演练演示如何使用C++ AMP 加速矩阵相乘的执行。 将显示两个算法，一个不平铺，另一个用于平铺。

## <a name="prerequisites"></a>先决条件

开始之前：

- 阅读[ C++ AMP 概述](../../parallel/amp/cpp-amp-overview.md)。

- [使用磁贴](../../parallel/amp/using-tiles.md)读取。

- 请确保至少运行 Windows 7 或 Windows Server 2008 R2。

### <a name="to-create-the-project"></a>创建项目

根据你安装的 Visual Studio 版本，创建新项目的说明有所不同。 请确保将左上方的版本选择器设置为正确的版本。

::: moniker range="vs-2019"

### <a name="to-create-the-project-in-visual-studio-2019"></a>在 Visual Studio 2019 中创建项目

1. 在菜单栏上，选择 "**文件**" ">**新建**>**项目**" 打开 "新建**项目**" 对话框。

1. 在对话框顶部，将“语言”设置为“C++”，将“平台”设置为“Windows”，并将“项目类型”设置为“控制台”。 

1. 从筛选的项目类型列表中，选择 "**空项目**"，然后选择 "**下一步**"。 在下一页中，在 "**名称**" 框中输入*MatrixMultiply*以指定项目的名称，并指定项目位置（如果需要）。

   ![新建控制台应用](../../build/media/mathclient-project-name-2019.png "新建控制台应用")

1. 选择“创建”按钮创建客户端项目。

1. 在**解决方案资源管理器**中，打开 "**源文件**" 的快捷菜单，然后选择 "**添加**>**新项**"。

1. 在 "**添加新项**" 对话框中，选择 **C++ "文件（.cpp）** "，在 "**名称**" 框中输入*MatrixMultiply* ，然后选择 "**添加**" 按钮。

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-project-in-visual-studio-2017-or-2015"></a>在 Visual Studio 2017 或2015中创建项目

1. 在 Visual Studio 的菜单栏上，选择 "**文件**>**新建**>**项目**"。

1. 在 "模板" 窗格中的 "**已安装**" 下，选择**视觉对象C++** 。

1. 选择 "**空项目**"，在 "**名称**" 框中输入*MatrixMultiply* ，然后选择 **"确定"** 按钮。

1. 选择“下一步”按钮。

1. 在**解决方案资源管理器**中，打开 "**源文件**" 的快捷菜单，然后选择 "**添加**>**新项**"。

1. 在 "**添加新项**" 对话框中，选择 **C++ "文件（.cpp）** "，在 "**名称**" 框中输入*MatrixMultiply* ，然后选择 "**添加**" 按钮。

::: moniker-end

## <a name="multiplication-without-tiling"></a>不平铺的乘法

在本部分中，考虑两个矩阵 A 和 B 的乘法，定义如下：

![3&#45;x&#45;2 矩阵 A](../../parallel/amp/media/campmatrixanontiled.png "3&#45;x&#45;2 矩阵 A")

![2&#45;x&#45;3 矩阵 B](../../parallel/amp/media/campmatrixbnontiled.png "2&#45;x&#45;3 矩阵 B")

是一个 3 x 2 的矩阵，而 B 是一个 2 x 3 的矩阵。 与 B 相乘的乘积是以下 3 x 3 矩阵。 该产品的计算方法是将的行与 B 元素的列相乘。

![3&#45;x&#45;3 产品矩阵](../../parallel/amp/media/campmatrixproductnontiled.png "3&#45;x&#45;3 产品矩阵")

### <a name="to-multiply-without-using-c-amp"></a>在不使用C++ AMP 的情况下进行相乘

1. 打开 MatrixMultiply 并使用下面的代码替换现有代码。

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

   int main() {
       MultiplyWithOutAMP();
       getchar();
   }
   ```

   算法是矩阵乘法定义的简单实现。 它不使用任何并行或线程算法来减少计算时间。

1. 在菜单栏上，依次选择“文件” > “全部保存”。

1. 选择**F5**键盘快捷方式开始调试，并验证输出是否正确。

1. 选择**Enter**以退出应用程序。

### <a name="to-multiply-by-using-c-amp"></a>使用C++ AMP 进行相乘

1. 在 MatrixMultiply 中，将以下代码添加到 `main` 方法前面。

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

   AMP 代码类似于非 AMP 代码。 对的调用 `parallel_for_each` 为 `product.extent`中的每个元素启动一个线程，并替换行和列的 `for` 循环。 `idx`中提供了行和列中的单元格的值。 您可以通过使用 `[]` 运算符和索引变量或 `()` 运算符以及行和列变量来访问 `array_view` 对象的元素。 该示例演示了这两种方法。 `array_view::synchronize` 方法将 `product` 变量的值复制回 `productMatrix` 变量。

1. 将以下 `include` 和 `using` 语句添加到 MatrixMultiply 的顶部。

   ```cpp
   #include <amp.h>
   using namespace concurrency;
   ```

1. 修改 `main` 方法以调用 `MultiplyWithAMP` 方法。

   ```cpp
   int main() {
       MultiplyWithOutAMP();
       MultiplyWithAMP();
       getchar();
   }
   ```

1. 按**Ctrl**+**F5**键盘快捷方式开始调试，并验证输出是否正确。

1. 按**空格键**退出应用程序。

## <a name="multiplication-with-tiling"></a>乘法 with 平铺

平铺是一种方法，用于将数据分区成大小相等的子集（称为磁贴）。 使用平铺时，有三种情况会发生变化。

- 您可以创建 `tile_static` 变量。 访问 `tile_static` 空间中的数据比访问全局空间中的数据更快。 为每个图块创建 `tile_static` 变量的实例，并且该图块中的所有线程都可以访问该变量。 平铺的主要优点是 `tile_static` 访问导致性能提升。

- 可以调用[tile_barrier：： wait](reference/tile-barrier-class.md#wait)方法，停止一个磁贴中指定代码行处的所有线程。 不能保证线程将在其中运行的顺序，仅一个磁贴中的所有线程将在调用 `tile_barrier::wait` 时停止，然后再继续执行。

- 您可以访问相对于整个 `array_view` 对象的线程索引和与磁贴相关的索引。 使用本地索引可以使代码更易于读取和调试。

若要利用矩阵相乘的平铺，该算法必须将矩阵分区为磁贴，然后将磁贴数据复制到 `tile_static` 变量中，以加快访问速度。 在此示例中，矩阵分区为大小相等的 submatrices。 此产品可通过将 submatrices 相乘。 本示例中的两个矩阵及其产品是：

![4&#45;x&#45;4 矩阵 A](../../parallel/amp/media/campmatrixatiled.png "4&#45;x&#45;4 矩阵 A")

![4&#45;x&#45;4 矩阵 B](../../parallel/amp/media/campmatrixbtiled.png "4&#45;x&#45;4 矩阵 B")

![4&#45;x&#45;4 产品矩阵](../../parallel/amp/media/campmatrixproducttiled.png "4&#45;x&#45;4 产品矩阵")

矩阵分区为四个2x2 矩阵，定义如下：

![4&#45;x&#45;4 矩阵分区为 2&#45;x&#45;2 子矩阵&#45;](../../parallel/amp/media/campmatrixapartitioned.png "4&#45;x&#45;4 矩阵分区为 2&#45;x&#45;2 子矩阵&#45;")

![4&#45;个&#45;，分为2个&#45;，&#45;分为2个子&#45;矩阵](../../parallel/amp/media/campmatrixbpartitioned.png "4&#45;个&#45;，分为2个&#45;，&#45;分为2个子&#45;矩阵")

现在可以按如下方式编写和计算 A 和 B 的产品：

![4&#45;x&#45;4 个矩阵 a，分为 2&#45;&#45;个子&#45;矩阵](../../parallel/amp/media/campmatrixproductpartitioned.png "4&#45;x&#45;4 个矩阵 a，分为 2&#45;&#45;个子&#45;矩阵")

由于矩阵 `a` 到 `h` 是2x2 矩阵，因此它们的所有产品和总和也是2x2 矩阵。 它还遵循： A 和 B 的产品是按预期方式进行的4x4 矩阵。 若要快速检查算法，请计算产品中第一行、第一列中的元素的值。 在本示例中，这将是 `ae + bg`第一行和第一列中的元素的值。 只需计算每个字词的第一列 `ae` 和 `bg`。 `(1 * 1) + (2 * 5) = 11``ae` 的值。 `bg` 的值为 `(3 * 1) + (4 * 5) = 23`。 最终值为 `11 + 23 = 34`，这是正确的。

若要实现此算法，代码：

- 在 `parallel_for_each` 调用中使用 `tiled_extent` 对象，而不是 `extent` 对象。

- 在 `parallel_for_each` 调用中使用 `tiled_index` 对象，而不是 `index` 对象。

- 创建用于保存 submatrices 的 `tile_static` 变量。

- 使用 `tile_barrier::wait` 方法来停止计算 submatrices 的产品。

### <a name="to-multiply-by-using-amp-and-tiling"></a>使用 AMP 和平铺进行相乘

1. 在 MatrixMultiply 中，将以下代码添加到 `main` 方法前面。

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

   此示例与不带平铺的示例大不相同。 此代码使用以下概念步骤：
   1. 将 `a` 的磁贴 [0，0] 的元素复制到 `locA`中。 将 `b` 的磁贴 [0，0] 的元素复制到 `locB`中。 请注意，`product` 是平铺的，而不是 `a` 和 `b`。 因此，您可以使用全局索引来访问 `a, b`和 `product`。 对 `tile_barrier::wait` 的调用非常重要。 它将停止磁贴中的所有线程，直至 `locA` 和 `locB` 都已填充。

   1. 将 `locA` 和 `locB` 相乘并将结果置于 `product`中。

   1. 将 `a` 的磁贴 [0，1] 的元素复制到 `locA`中。 将 `b` 的磁贴 [1，0] 的元素复制到 `locB`中。

   1. 将 `locA` 和 `locB` 相乘，然后将它们添加到已在 `product`中的结果。

   1. 磁贴 [0，0] 的乘法已完成。

   1. 对其他四个磁贴重复此操作。 没有专门针对磁贴的索引，线程可以按任意顺序执行。 每个线程执行时，会为每个图块正确地创建 `tile_static` 变量，并对 `tile_barrier::wait` 的调用控制程序流。

   1. 仔细检查算法时，请注意，每个 submatrix 都将加载到 `tile_static` 内存两次。 这种数据传输确实会花费一些时间。 但是，一旦数据 `tile_static` 内存中，对数据的访问速度要快得多。 因为计算产品需要对 submatrices 中的值进行重复访问，所以存在总体性能提升。 对于每种算法，都需要试验才能找到最佳算法和磁贴大小。

   在非磁贴和非磁贴示例中，A 和 B 的每个元素都从全局内存访问四次，以计算该产品。 在该磁贴示例中，每个元素都从全局内存访问两次，从 `tile_static` 内存访问四次。 这并不是显著的性能提升。 但是，如果 A 和 B 是1024x1024 矩阵，磁贴大小为16，则会显著提高性能。 在这种情况下，每个元素仅复制到 `tile_static` 内存16次，并从 `tile_static` 内存1024次访问。

1. 修改 main 方法以调用 `MultiplyWithTiling` 方法，如下所示。

   ```cpp
   int main() {
       MultiplyWithOutAMP();
       MultiplyWithAMP();
       MultiplyWithTiling();
       getchar();
   }
   ```

1. 按**Ctrl**+**F5**键盘快捷方式开始调试，并验证输出是否正确。

1. 按**空格键**退出应用程序。

## <a name="see-also"></a>另请参阅

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[演练：调试 C++ AMP 应用程序](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)
