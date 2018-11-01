---
title: 演练：调试 C++ AMP 应用程序
ms.date: 11/04/2016
helpviewer_keywords:
- debugging, C++ Accelerated Massive Parallelism
- C++ AMP, debugging
- C++ Accelerated Massive Parallelism, debugging
- debugging, C++ AMP
ms.assetid: 40e92ecc-f6ba-411c-960c-b3047b854fb5
ms.openlocfilehash: 4f8cdc315b561b5cbb4538e8486208d6278af9df
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579890"
---
# <a name="walkthrough-debugging-a-c-amp-application"></a>演练：调试 C++ AMP 应用程序

本主题演示如何调试使用 C++ Accelerated Massive Parallelism (C++ AMP) 应用程序以便利用图形处理单元 (GPU)。 它使用总结大整数数组的并行缩减程序。 本演练阐释了以下任务：

- 启动 GPU 调试器。

- 在“GPU 线程”窗口中检查 GPU 线程。

- 使用**并行堆栈**窗口同时查看多个 GPU 线程的调用堆栈。

- 使用**并行监视**窗口来同时跨多个线程检查单个表达式的值。

- 标记、冻结、解冻和组合 GPU 线程。

- 将 Tile 的所有线程执行到代码中的特定位置。

## <a name="prerequisites"></a>系统必备

在开始本演练之前：

- 读取[c + + AMP 概述](../../parallel/amp/cpp-amp-overview.md)。

- 确保文本编辑器中显示行号。 有关详细信息，请参阅[如何： 在编辑器中显示行号](/visualstudio/ide/reference/how-to-display-line-numbers-in-the-editor)。

- 请确保正在运行 Windows 8 或 Windows Server 2012，以支持在软件模拟器上进行调试。

[!INCLUDE[note_settings_general](../../mfc/includes/note_settings_general_md.md)]

### <a name="to-create-the-sample-project"></a>创建示例项目

1. 启动 Visual Studio。

2. 在菜单栏上，依次选择“文件” > “新建” > “项目”。

3. 下**已安装**在模板窗格中，选择**Visual c + +**。

4. 选择**Win32 控制台应用程序**，类型`AMPMapReduce`中**名称**框中，，然后选择**确定**按钮。

5. 选择“下一步”按钮。

6. 清除**预编译标头**复选框，，然后选择**完成**按钮。

7. 在中**解决方案资源管理器**，删除从项目的 stdafx.h、 targetver.h 和 stdafx.cpp。

8. 打开 AMPMapReduce.cpp 并用下面的代码替换其中的内容。

```cpp
    // AMPMapReduce.cpp defines the entry point for the program.
    // The program performs a parallel-sum reduction that computes the sum of an array of integers.

    #include <stdio.h>
    #include <tchar.h>
    #include <amp.h>

    const int BLOCK_DIM = 32;

    using namespace concurrency;

    void sum_kernel_tiled(tiled_index<BLOCK_DIM> t_idx, array<int, 1> &A, int stride_size) restrict(amp)
    {
        tile_static int localA[BLOCK_DIM];

        index<1> globalIdx = t_idx.global * stride_size;
        index<1> localIdx = t_idx.local;

        localA[localIdx[0]] =  A[globalIdx];

        t_idx.barrier.wait();

        // Aggregate all elements in one tile into the first element.
        for (int i = BLOCK_DIM / 2; i > 0; i /= 2)
        {
            if (localIdx[0] < i)
            {

                localA[localIdx[0]] += localA[localIdx[0] + i];
            }

            t_idx.barrier.wait();
        }

        if (localIdx[0] == 0)
        {
            A[globalIdx] = localA[0];
        }
    }

    int size_after_padding(int n)
    {
        // The extent might have to be slightly bigger than num_stride to
        // be evenly divisible by BLOCK_DIM. You can do this by padding with zeros.
        // The calculation to do this is BLOCK_DIM * ceil(n / BLOCK_DIM)
        return ((n - 1) / BLOCK_DIM + 1) * BLOCK_DIM;
    }

    int reduction_sum_gpu_kernel(array<int, 1> input)
    {
        int len = input.extent[0];

        //Tree-based reduction control that uses the CPU.
        for (int stride_size = 1; stride_size < len; stride_size *= BLOCK_DIM)
        {
            // Number of useful values in the array, given the current
            // stride size.
            int num_strides = len / stride_size;

            extent<1> e(size_after_padding(num_strides));

            // The sum kernel that uses the GPU.
            parallel_for_each(extent<1>(e).tile<BLOCK_DIM>(), [&input, stride_size] (tiled_index<BLOCK_DIM> idx) restrict(amp)
            {
                sum_kernel_tiled(idx, input, stride_size);
            });
        }

        array_view<int, 1> output = input.section(extent<1>(1));
        return output[0];
    }

    int cpu_sum(const std::vector<int> &arr) {
        int sum = 0;
        for (size_t i = 0; i < arr.size(); i++) {
            sum += arr[i];
        }
        return sum;
    }

    std::vector<int> rand_vector(unsigned int size) {
        srand(2011);

        std::vector<int> vec(size);
        for (size_t i = 0; i < size; i++) {
            vec[i] = rand();
        }
        return vec;
    }

    array<int, 1> vector_to_array(const std::vector<int> &vec) {
        array<int, 1> arr(vec.size());
        copy(vec.begin(), vec.end(), arr);
        return arr;
    }

    int _tmain(int argc, _TCHAR* argv[])
    {
        std::vector<int> vec = rand_vector(10000);
        array<int, 1> arr = vector_to_array(vec);

        int expected = cpu_sum(vec);
        int actual = reduction_sum_gpu_kernel(arr);

        bool passed = (expected == actual);
        if (!passed) {
            printf("Actual (GPU): %d, Expected (CPU): %d", actual, expected);
        }
        printf("sum: %s\n", passed  "Passed!" : "Failed!");

        getchar();

        return 0;
    }
```

9. 在菜单栏上，依次选择“文件” > “全部保存”。

10. 在中**解决方案资源管理器**，打开快捷菜单**AMPMapReduce**，然后选择**属性**。

11. 在中**属性页**对话框中的**配置属性**，选择**C/c + +** > **预编译标头**。

12. 有关**预编译标头**属性中，选择**不使用预编译头**，然后选择**确定**按钮。

13. 在菜单栏上，依次选择“生成” > “生成解决方案”。

## <a name="debugging-the-cpu-code"></a>调试 CPU 代码

在此过程中，您将使用本地 Windows 调试器，以确保此应用程序中的 CPU 代码是正确的。 在此应用程序中，特别值得关注的 CPU 代码段是 `for` 函数中的 `reduction_sum_gpu_kernel` 循环。 它控制运行在 GPU 上的基于树的并行缩减。

### <a name="to-debug-the-cpu-code"></a>调试 CPU 代码

1. 在中**解决方案资源管理器**，打开快捷菜单**AMPMapReduce**，然后选择**属性**。

2. 在中**属性页**对话框中的**配置属性**，选择**调试**。 确认**本地 Windows 调试器**中选择**要启动的调试器**列表。

3. 返回到**代码编辑器**。

4. 在下图所示的代码行上设置断点（大约第 67 和 70 行）。

     ![CPU 断点](../../parallel/amp/media/campcpubreakpoints.png "campcpubreakpoints") CPU 断点

5. 在菜单栏上，依次选择“调试” > “开始调试”。

6. 在**局部变量**窗口中，观察的值为`stride_size`直到第 70 行断点。

7. 在菜单栏上，依次选择“调试” > “停止调试”。

## <a name="debugging-the-gpu-code"></a>调试 GPU 代码

本部分说明如何调试 GPU 代码，即 `sum_kernel_tiled` 函数包含的代码。 GPU 代码为每个“块”并行计算整数和。

### <a name="to-debug-the-gpu-code"></a>调试 GPU 代码

1. 在中**解决方案资源管理器**，打开快捷菜单**AMPMapReduce**，然后选择**属性**。

2. 在中**属性页**对话框中的**配置属性**，选择**调试**。

3. 在中**要启动的调试器**列表中，选择**本地 Windows 调试器**。

4. 在中**调试器类型**列表中，验证**自动**处于选中状态。

    **自动**是默认值。 在 Windows 10 之前**仅限 GPU**是必需的值而不是**自动**。

5. 选择“确定”  按钮。

6. 如下图所示，在第 30 行处设置一个断点。

     ![GPU 断点](../../parallel/amp/media/campgpubreakpoints.png "campgpubreakpoints") GPU 断点

7. 在菜单栏上，依次选择“调试” > “开始调试”。 由于第 67 和 70 行代码在 CPU 上执行，因此 GPU 调试期间将不执行这些行中的 CPU 代码断点。

### <a name="to-use-the-gpu-threads-window"></a>使用“GPU 线程”窗口

1. 若要打开**GPU 线程**窗口，请在菜单栏上，选择**调试** > **Windows** > **GPU 线程**。

   可以检查 GPU 线程中的状态**GPU 线程**出现的窗口。

2. 停靠**GPU 线程**窗口底部的 Visual Studio。 选择**展开线程切换**按钮以显示 tile 和线程文本框。 **GPU 线程**窗口显示活动和受阻的 GPU 线程的总数，如下图中所示。

     ![具有 4 个活动线程的 GPU 线程窗口](../../parallel/amp/media/campc.png "campc") GPU 线程窗口

   系统为此计算分配了 313 个 Tile。 每个 Tile 包含 32 个线程。 由于本地 GPU 调试在软件模拟器中进行，因此有四个活动的 GPU 线程。 四个线程同时执行指令，然后一起移动到下一条指令。

   在中**GPU 线程**窗口中，有四个 GPU 线程处于活动状态和 28 个 GPU 线程会被阻止[tile_barrier:: wait](reference/tile-barrier-class.md#wait)大约第 21 行处定义的语句 (`t_idx.barrier.wait();`)。 所有这 32 个GPU 线程都属于第一个 Tile `tile[0]`。 当前线程所在的行由箭头指示。 若要切换到其他线程，请使用下列方法之一：

    - 在线程中切换行**GPU 线程**窗口中，打开快捷菜单，然后选择**切换到线程**。 如果该行代表多个线程，将按线程坐标切换到第一个线程。

    - 在对应的文本框中输入该线程的平铺和线程值，然后选择**切换线程**按钮。

   **调用堆栈**窗口显示当前 GPU 线程的调用堆栈。

### <a name="to-use-the-parallel-stacks-window"></a>使用“并行堆栈”窗口

1. 若要打开**并行堆栈**窗口，请在菜单栏上，选择**调试** > **Windows** > **并行堆栈**.

   可以使用**并行堆栈**窗口同时检查多个 GPU 线程的堆栈帧。

2. 停靠**并行堆栈**窗口底部的 Visual Studio。

3. 请确保**线程**中左上角的列表中选择。 在下图中，**并行堆栈**窗口将显示在中看到的 GPU 线程的调用堆栈集中视图**GPU 线程**窗口。

     ![具有 4 个活动线程的并行堆栈窗口](../../parallel/amp/media/campd.png "campd")并行堆栈窗口

   32 个线程从 `_kernel_stub` 执行到 `parallel_for_each` 函数调用中的 lambda 语句，随后执行到 `sum_kernel_tiled` 函数，再从这里进行并行缩减。 28 超出 32 个线程前进到[tile_barrier:: wait](reference/tile-barrier-class.md#wait)语句和保持阻止状态，在行 22，而其他 4 个线程中保持活动状态`sum_kernel_tiled`第 30 行处的函数。

   您可以检查 GPU 线程中可用的属性**GPU 线程**中的丰富数据提示窗口**并行堆栈**窗口。 若要执行此操作，请将鼠标指针停留在堆栈帧**sum_kernel_tiled**。 下图显示了数据提示。

     ![并行堆栈窗口的数据提示](../../parallel/amp/media/campe.png "campe") GPU 线程数据提示

   有关详细信息**并行堆栈**窗口中，请参阅[使用并行堆栈窗口](/visualstudio/debugger/using-the-parallel-stacks-window)。

### <a name="to-use-the-parallel-watch-window"></a>使用“并行监视”窗口

1. 若要打开**并行监视**窗口，请在菜单栏上，选择**调试** > **Windows** > **并行监视**  > **并行监视 1**。

   可以使用**并行监视**窗口来跨多个线程检查表达式的值。

2. 停靠**并行监视 1**窗口到 Visual Studio 底部。 中的表有 32 行**并行监视**窗口。 每个对应于在这两个 GPU 线程窗口中出现过的 GPU 线程并**并行堆栈**窗口。 现在，可以输入所需的表达式，以检查其在所有这 32 个 GPU 线程中的值。

3. 选择**添加监视**列标题中，输入`localIdx`，然后选择**Enter**密钥。

4. 选择**添加监视**再次列标题，键入`globalIdx`，然后选择**Enter**密钥。

5. 选择**添加监视**再次列标题，键入`localA[localIdx[0]]`，然后选择**Enter**密钥。

   您可以通过选择相应的列标题来按指定表达式排序。

   选择**localA [localIdx [0]]** 列标题对列进行排序。 下图显示了排序的结果**localA [localIdx [0]]**。

     ![包含分类结果的并行监视窗口](../../parallel/amp/media/campf.png "campf")排序结果

   您可以导出中的内容**并行监视**到 Excel 窗口中的通过选择**Excel**按钮，然后选择**在 Excel 中打开**。 如果开发计算机上安装有 Excel，这将打开包含该内容的 Excel 工作表。

6. 在右上角的**并行监视**窗口中，没有可用于通过使用布尔表达式筛选内容的筛选器控件。 Enter`localA[localIdx[0]] > 20000`筛选器控件文本框框，然后选择**Enter**密钥。

   该窗口现在只包含 `localA[localIdx[0]]` 值大于 20000 的线程。 内容仍按 `localA[localIdx[0]]` 列排序，这是之前执行的排序操作。

## <a name="flagging-gpu-threads"></a>标记 GPU 线程

您可以将特定的 GPU 线程标记中进行标记**GPU 线程**窗口中，**并行监视**窗口中或在数据提示**并行堆栈**窗口。 如果“GPU 线程”窗口中的某一行包含多个线程，则通过标记该行，可标记该行中包含的所有线程。

### <a name="to-flag-gpu-threads"></a>标记 GPU 线程

1. 选择 **[线程]** 中的列标头**并行监视 1**窗口以按 tile 索引和线程索引进行排序。

2. 在菜单栏上依次选择**调试** > **继续**，这将导致的四个线程的处于活动状态前进到下一个屏障 （在 AMPMapReduce.cpp 的第 32 行处定义）。

3. 在当前处于活动状态的四个线程所在行的左侧，选择标志符号。

   下图显示了在四个活动已标记的线程**GPU 线程**窗口。

     ![使用标记的线程的 GPU 线程窗口](../../parallel/amp/media/campg.png "campg") GPU 线程窗口中的活动线程

   **并行监视**窗口和的数据提示**并行堆栈**这两个窗口指示标记的线程。

4. 如果你想要重点关注所标记的四个线程，您可以选择显示，请在**GPU 线程**，**并行监视**，并**并行堆栈**windows，仅标记线程数。

   选择**仅显示标记**任何按钮的 windows 或在**调试位置**工具栏。 如下图所示**仅显示标记**按钮**调试位置**工具栏。

     ![调试位置工具栏上仅显示已标记项图标](../../parallel/amp/media/camph.png "camph")
**仅显示标记**按钮

   现在**GPU 线程**，**并行监视**，并**并行堆栈**windows 显示标记的线程。

## <a name="freezing-and-thawing-gpu-threads"></a>冻结和解冻 GPU 线程

您可以冻结 （挂起） 和解冻 （恢复） GPU 线程眖**GPU 线程**窗口或**并行监视**窗口。 您可以冻结和解冻 CPU 线程相同的方式;有关信息，请参阅[如何： 使用线程窗口](/visualstudio/debugger/how-to-use-the-threads-window)。

### <a name="to-freeze-and-thaw-gpu-threads"></a>冻结和解冻 GPU 线程

1. 选择**仅显示标记**按钮以显示所有线程。

2. 在菜单栏上依次选择**调试** > **继续**。

3. 打开活动行的快捷菜单，然后选择**冻结**。

   下图中的**GPU 线程**窗口显示所有四个线程均已冻结。

     ![显示已冻结的线程的 GPU 线程窗口](../../parallel/amp/media/campk.png "campk")冻结线程**GPU 线程**窗口

   同样，**并行监视**窗口显示所有四个线程均已冻结。

4. 在菜单栏上依次选择**调试** > **继续**以便接下来的四个 GPU 线程的屏障第 22 行处并到达第 30 行处的断点。 **GPU 线程**窗口会显示四个以前已冻结的线程仍被冻结并处于活动状态。

5. 在菜单栏上依次选择**调试**，**继续**。

6. 从**并行监视**窗口中，您还可以解冻单个或多个 GPU 线程。

### <a name="to-group-gpu-threads"></a>对 GPU 线程分组

1. 上一个中的线程的快捷菜单**GPU 线程**窗口中，选择**Group By**，**地址**。

   中的线程**GPU 线程**窗口按地址进行分组。 该地址对应于每组线程所在的反汇编指令。 24 个线程位于第 22 行处其中[tile_barrier:: wait 方法](reference/tile-barrier-class.md#wait)执行。 12 个线程位于第 32 行屏障的指令处。 其中 4 个线程经过标记。 8 个线程位于第 30 行的断点处。 其中 4 个线程已冻结。 下图显示了在经过分组的线程**GPU 线程**窗口。

     ![按地址分组的线程的 GPU 线程窗口](../../parallel/amp/media/campl.png "campl")分组中的线程**GPU 线程**窗口

2. 此外可以执行**Group By**操作方法是打开的数据网格的快捷菜单**并行监视**窗口中，选择**Group By**，然后选择菜单对应于你想要的线程分组的项。

## <a name="running-all-threads-to-a-specific-location-in-code"></a>将所有线程运行到代码中的特定位置

将给定 tile 中的所有线程都运行到通过使用包含光标的行**都运行当前磁贴到光标处**。

### <a name="to-run-all-threads-to-the-location-marked-by-the-cursor"></a>将所有线程运行到光标指示的位置

1. 在已冻结线程的快捷菜单，选择**解冻**。

2. 在中**代码编辑器**，将光标放在第 30 行中。

3. 上的快捷菜单**代码编辑器**，选择**当前 Tile 运行到光标处**。

   之前在第 21 行处受阻的 24 个线程将继续运行到第 32 行。 如下所示**GPU 线程**窗口。

## <a name="see-also"></a>请参阅

[C++ AMP 概述](../../parallel/amp/cpp-amp-overview.md)<br/>
[调试 GPU 代码](/visualstudio/debugger/debugging-gpu-code)<br/>
[如何：使用“GPU 线程”窗口](/visualstudio/debugger/how-to-use-the-gpu-threads-window)<br/>
[如何：使用“并行监视”窗口](/visualstudio/debugger/how-to-use-the-parallel-watch-window)<br/>
[使用并发可视化工具分析 c + + AMP 代码](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/03/09/analyzing-c-amp-code-with-the-concurrency-visualizer/)