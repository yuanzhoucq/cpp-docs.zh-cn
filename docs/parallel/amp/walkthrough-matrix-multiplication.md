---
title: 演练：矩阵乘法
ms.date: 04/23/2019
ms.assetid: 61172e8b-da71-4200-a462-ff3a908ab0cf
ms.openlocfilehash: f30f8dc235bf0e76c342bea26a35bcbb36cfa237
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366800"
---
# <a name="walkthrough-matrix-multiplication"></a>演练：矩阵乘法

此分步演练演示了如何使用C++ AMP 加速执行矩阵乘法。 提出了两种算法，一种不平铺，一种不平铺。

## <a name="prerequisites"></a>先决条件

开始之前：

- 阅读[C++ AMP 概述](../../parallel/amp/cpp-amp-overview.md)。

- [使用磁贴](../../parallel/amp/using-tiles.md)读取 。

- 请确保您至少运行的是 Windows 7 或 Windows 服务器 2008 R2。

### <a name="to-create-the-project"></a>创建项目

创建新项目的说明因已安装的 Visual Studio 版本而异。 要查看您首选版本的 Visual Studio 的文档，请使用**版本**选择器控件。 它位于此页面的目录顶部。

::: moniker range="vs-2019"

### <a name="to-create-the-project-in-visual-studio-2019"></a>在视觉工作室 2019 中创建项目

1. 在菜单栏上，选择“文件”“新建”“项目”，打开“创建新项目”对话框**** > **** > ********。

1. 在对话框顶部，将“语言”**** 设置为“C++”****，将“平台”**** 设置为“Windows”****，并将“项目类型”**** 设置为“控制台”****。

1. 从筛选的项目类型列表中，选择 **"空项目"，** 然后选择 **"下一步**"。 在下一页中，在 **"名称"** 框中输入*MatrixMultiply*以指定项目的名称，并根据需要指定项目位置。

   ![新的控制台应用程序](../../build/media/mathclient-project-name-2019.png "新的控制台应用程序")

1. 选择“创建”**** 按钮创建客户端项目。

1. 在**解决方案资源管理器**中，打开**源文件的**快捷方式菜单，然后选择"**Add**>**添加新项**"。

1. 在"**添加新项目"** 对话框中，选择**C++文件 （.cpp）**，在 **"名称"** 框中输入*Matrixmultiply.cpp，* 然后选择"**添加**"按钮。

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-project-in-visual-studio-2017-or-2015"></a>在 Visual Studio 2017 或 2015 中创建项目

1. 在 Visual Studio 的菜单栏上，选择 **"文件**>**新项目**>**"。**

1. 在模板窗格中 **"安装"** 下，选择 **"可视C++**"。

1. 选择 **"空项目**"，在 **"名称"** 框中输入*矩阵乘法*，然后选择 **"确定**"按钮。

1. 选择“下一步”按钮****。

1. 在**解决方案资源管理器**中，打开**源文件的**快捷方式菜单，然后选择"**Add**>**添加新项**"。

1. 在"**添加新项目"** 对话框中，选择**C++文件 （.cpp）**，在 **"名称"** 框中输入*Matrixmultiply.cpp，* 然后选择"**添加**"按钮。

::: moniker-end

## <a name="multiplication-without-tiling"></a>不平铺的乘法

在本节中，请考虑两个矩阵 A 和 B 的乘法，它们的定义如下：

![3&#45;由&#45;2 矩阵 A](../../parallel/amp/media/campmatrixanontiled.png "3&#45;由&#45;2 矩阵 A")

![2&#45;矩阵 B&#45;](../../parallel/amp/media/campmatrixbnontiled.png "2&#45;矩阵 B&#45;")

A 是 3×2 矩阵，B 为 2×3 矩阵。 将 A 乘以 B 的乘积为以下 3×3 矩阵。 通过乘以 A 元素的列来计算产品。

![3&#45;3 个产品矩阵&#45;](../../parallel/amp/media/campmatrixproductnontiled.png "3&#45;3 个产品矩阵&#45;")

### <a name="to-multiply-without-using-c-amp"></a>不使用C++ AMP 相乘

1. 打开矩阵乘法.cpp 并使用以下代码替换现有代码。

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

   该算法是矩阵乘法定义的一个直接实现。 它不使用任何并行或线程算法来减少计算时间。

1. 在菜单栏上，选择 **"全部保存文件** > **Save All**"。

1. 选择**F5**键盘快捷键以开始调试并验证输出是否正确。

1. 选择 **"输入"** 以退出应用程序。

### <a name="to-multiply-by-using-c-amp"></a>使用C++ AMP 相乘

1. 在 Matrixmultiply.cpp 中，在`main`方法之前添加以下代码。

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

   AMP 代码类似于非 AMP 代码。 调用 为`parallel_for_each`中`product.extent`的每个元素启动一个线程，并替换行`for`和列的循环。 行和列中的单元格的值在 中`idx`可用。 可以使用`[]`运算符和索引变量或`()`运算符`array_view`以及行和列变量访问对象的元素。 该示例演示了这两种方法。 该方法`array_view::synchronize`将`product`变量的值复制回变量`productMatrix`。

1. 在 Matrixmultiply.cpp 的顶部添加以下内容`include`和`using`语句。

   ```cpp
   #include <amp.h>
   using namespace concurrency;
   ```

1. 修改方法`main`以调用 方法`MultiplyWithAMP`。

   ```cpp
   int main() {
       MultiplyWithOutAMP();
       MultiplyWithAMP();
       getchar();
   }
   ```

1. 按**Ctrl**+**F5**键盘快捷键开始调试并验证输出是否正确。

1. 按**空格键**退出应用程序。

## <a name="multiplication-with-tiling"></a>平铺乘法

平铺是一种将数据划分为大小相等的子集（称为切片）的技术。 使用平铺时，有三件事会改变。

- 您可以创建`tile_static`变量。 在空间中`tile_static`访问数据的速度可能比访问全局空间中的数据快很多倍。 为每个磁贴创建`tile_static`变量的实例，并且磁贴中的所有线程都有权访问该变量。 平铺的主要好处是由于访问而`tile_static`获得性能。

- 您可以调用[tile_barrier：：wait](reference/tile-barrier-class.md#wait)方法，以在指定的代码行上停止一个磁贴中的所有线程。 您无法保证线程将运行的顺序，只有一个磁贴中的所有线程在继续执行之前在调用`tile_barrier::wait`时停止。

- 您可以访问线程相对于整个`array_view`对象的索引和相对于磁贴的索引。 通过使用本地索引，可以使代码更易于读取和调试。

为了利用矩阵乘法中的平铺，算法必须将矩阵分区到切片中，然后将切片数据复制到变量中`tile_static`，以便更快地访问。 在此示例中，矩阵被划分为大小相等的子矩阵。 通过乘以子矩阵找到产品。 此示例中的两个矩阵及其产品是：

![4&#45;由&#45;4 矩阵 A](../../parallel/amp/media/campmatrixatiled.png "4&#45;由&#45;4 矩阵 A")

![4&#45;由&#45;4 矩阵 B](../../parallel/amp/media/campmatrixbtiled.png "4&#45;由&#45;4 矩阵 B")

![4&#45;由&#45;4 个产品矩阵](../../parallel/amp/media/campmatrixproducttiled.png "4&#45;由&#45;4 个产品矩阵")

矩阵被划分为四个 2x2 矩阵，定义如下：

![4&#45;由&#45;4 矩阵 A 分区为 2&#45;由&#45;子&#45;矩阵](../../parallel/amp/media/campmatrixapartitioned.png "4&#45;由&#45;4 矩阵 A 分区为 2&#45;由&#45;子&#45;矩阵")

![4&#45;由&#45;4 矩阵 B 分区为 2&#45;，由&#45;2 子&#45;矩阵](../../parallel/amp/media/campmatrixbpartitioned.png "4&#45;由&#45;4 矩阵 B 分区为 2&#45;，由&#45;2 子&#45;矩阵")

A 和 B 的积数现在可以编写和计算如下：

![4&#45;由&#45;4 矩阵 A B 分区为 2&#45;由&#45;2 子&#45;矩阵](../../parallel/amp/media/campmatrixproductpartitioned.png "4&#45;由&#45;4 矩阵 A B 分区为 2&#45;由&#45;2 子&#45;矩阵")

由于矩阵`a`为`h`2x2 矩阵，因此所有产品和总和也是 2x2 矩阵。 因此，A 和 B 的乘积是 4x4 矩阵，正如预期的那样。 要快速检查算法，请计算第一行中元素的值，在产品中的第一列。 在此示例中，这将是 元素在 的第一行和第一列中`ae + bg`的元素的值。 您只需要计算每个术语的第一列、第一行`ae`和`bg`。 值 为`ae``(1 * 1) + (2 * 5) = 11`。 `bg` 的值为 `(3 * 1) + (4 * 5) = 23`。 最终值为`11 + 23 = 34`，这是正确的。

要实现此算法，代码：

- 使用`tiled_extent`对象而不是调用中`extent``parallel_for_each`的对象。

- 使用`tiled_index`对象而不是调用中`index``parallel_for_each`的对象。

- 创建`tile_static`变量以保存子矩阵。

- 使用`tile_barrier::wait`方法停止用于计算子矩阵的产品的线程。

### <a name="to-multiply-by-using-amp-and-tiling"></a>使用 AMP 和平铺进行乘以

1. 在 Matrixmultiply.cpp 中，在`main`方法之前添加以下代码。

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

   此示例与不平铺的示例明显不同。 代码使用以下概念步骤：
   1. 将 的磁贴 [0，0]`a`的元素`locA`复制到 中。 将 的磁贴 [0，0]`b`的元素`locB`复制到 中。 请注意，`product`该请注意已平铺`a`，`b`而不是 和 。 因此，您可以使用全局索引来访问`a, b`和`product`。 调用`tile_barrier::wait`至关重要。 它停止磁贴中的所有线程，直到填充`locA`和`locB`填充。

   1. 乘`locA`以`locB`并将结果放入`product`中。

   1. 将 的磁贴[0，1] 的元素`a`复制到`locA`中。 将 的磁贴 [1，0]`b`的元素`locB`复制到 中。

   1. 相`locA`乘`locB`并添加它们到 中已有的结果`product`。

   1. 切片[0，0] 的乘法已完成。

   1. 对其他四个磁贴重复上述步骤。 没有专门针对切片的索引，线程可以按任何顺序执行。 当每个线程执行时，`tile_static`将为每个磁贴适当地创建变量，并相应地调用控制`tile_barrier::wait`程序流。

   1. 仔细检查算法时，请注意每个子矩阵都加载到内存中`tile_static`两次。 数据传输确实需要时间。 但是，一旦数据进入内存`tile_static`中，对数据的访问就会更快。 由于计算产品需要重复访问子矩阵中的值，因此性能会提高。 对于每个算法，需要实验才能找到最佳算法和切片大小。

   在非 AMP 和非切片示例中，A 和 B 的每个元素从全局内存中访问四次以计算产品。 在磁贴示例中，每个元素从全局内存访问两次，从`tile_static`内存访问四次。 这不是显著的性能提升。 但是，如果 A 和 B 是 1024x1024 矩阵，并且切片大小为 16，则性能会显著提高。 在这种情况下，每个元素将只复制到`tile_static`内存 16 次，并从`tile_static`内存访问 1024 次。

1. 修改主方法以调用`MultiplyWithTiling`方法，如图所示。

   ```cpp
   int main() {
       MultiplyWithOutAMP();
       MultiplyWithAMP();
       MultiplyWithTiling();
       getchar();
   }
   ```

1. 按**Ctrl**+**F5**键盘快捷键开始调试并验证输出是否正确。

1. 按**空格**键退出应用程序。

## <a name="see-also"></a>另请参阅

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[演练：调试 C++ AMP 应用程序](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)
