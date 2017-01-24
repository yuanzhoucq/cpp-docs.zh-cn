---
title: "演练：调试 C++ AMP 应用程序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "调试, C++ Accelerated Massive Parallelism"
  - "C++ AMP, 调试"
  - "C++ Accelerated Massive Parallelism, 调试"
  - "调试, C++ AMP"
ms.assetid: 40e92ecc-f6ba-411c-960c-b3047b854fb5
caps.latest.revision: 35
caps.handback.revision: 34
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 演练：调试 C++ AMP 应用程序
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题演示如何使用 C\+\+ Accelerated Massive Parallelism \(C\+\+ AMP\) 调试应用程序以便可以利用图形处理器 \(GPU\)。  它使用总结大整数数组的并行降低程序。  本演练阐释了以下任务：  
  
-   启动GPU调试器  
  
-   检查GPU 线程窗口中的GPU线程  
  
-   使用"并行堆栈窗口同时查看多个GPU 线程调用堆栈。  
  
-   使用"并行同时检查单个表达式的值"监视"窗口在多个线程中。  
  
-   标志，冻结和解冻，组合 GPU 线程。  
  
-   执行标题的所有线程到代码中指定位置。  
  
## 系统必备  
 在开始本演练之前：  
  
-   读取 [C\+\+ AMP 概述](../../parallel/amp/cpp-amp-overview.md)。  
  
-   确保行号在文本编辑器中显示。  有关详细信息，请参阅[如何：显示编辑器中的行数](../Topic/How%20to:%20Display%20Line%20Numbers%20in%20the%20Editor.md)。  
  
-   确保在软件模拟器中运行 [!INCLUDE[win8](../../build/includes/win8_md.md)] 或 [!INCLUDE[winserver8](../../build/includes/winserver8_md.md)] 来支持调试。  
  
 [!INCLUDE[note_settings_general](../../mfc/includes/note_settings_general_md.md)]  
  
### 创建示例项目  
  
1.  启动 Visual Studio。  
  
2.  在菜单栏上，依次选择**“文件”**、**“新建”**、**“项目”**。  
  
3.  在**“已安装”**的模板窗格下，选择**“Visual C\+\+”**。  
  
4.  选择 **Win32 控制台应用程序**中，键入在 **名称** 框中键入 `AMPMapReduce`，再选择 **确定** 按钮。  
  
5.  选择**“下一步”**按钮。  
  
6.  清除 **预编译头 \(P\)** 复选框，然后选择 **完成** 按钮。  
  
7.  在 **解决方案资源管理器**中，从项目中删除targetver.h stdafx.cpp stdafx.h 。  
  
8.  打开 AMPMapReduce.cpp 并用下面的代码的内容替换它。  
  
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
        printf("sum: %s\n", passed ? "Passed!" : "Failed!");   
  
        getchar();  
  
        return 0;  
    }  
  
    ```  
  
9. 在菜单栏上，依次选择**“文件”**、**“全部保存”**。  
  
10. 在**“解决方案资源管理器”**中，打开 **AMPMapReduce**的快捷菜单，然后选择**“属性”**。  
  
11. 在 **属性页** 对话框中，在 **配置属性**下，选择 **C\/C\+\+**，单击 **预编译头**。  
  
12. 对于 **预编译头** 属性中，选择 **不使用预编译头**，然后选择 **确定** 按钮。  
  
13. 在菜单栏上，依次选择**“生成”**、**“生成解决方案”**。  
  
## 调试 CPU 代码。  
 在此过程中，您将使用本地 Windows 调试器，以确保此应用程序 CPU 的代码是正确的。  特别值得关注的此应用程序中CPU 代码段是`reduction_sum_gpu_kernel` 函数的 `for` 循环。  它控制 运行在GPU 的基于树的并行降低。  
  
### 为了调试 CPU  
  
1.  在**“解决方案资源管理器”**中，打开 **AMPMapReduce**的快捷菜单，然后选择**“属性”**。  
  
2.  在**“属性页”**对话框中的**“配置属性”**下选择**“调试”**。  在**“要启动的调试器”**列表中，修正**“本地 Windows 调试器”**。  
  
3.  返回代码编辑器。  
  
4.  将在下图所示的代码行上断点 \(大约行 67 行 70\)。  
  
     ![CPU 断点](../../parallel/amp/media/campcpubreakpoints.png "CampCpuBreakpoints")  
CPU 断点  
  
5.  在菜单栏上，依次选择**“调试”**、**“启动调试”**。  
  
6.  在 **局部变量** 窗口，观察`stride_size` 值，直至在行 70 的断点。  
  
7.  在菜单栏上，依次选择**“调试”**、**“停止调试”**。  
  
## 调试 GPU 代码。  
 本节说明如何调试 GPU 代码，在 `sum_kernel_tiled` 函数包含的代码。  GPU 代码为并行中每一块计算整数和。  
  
### 为了调试 GPU  
  
1.  在**“解决方案资源管理器”**中，打开 **AMPMapReduce**的快捷菜单，然后选择**“属性”**。  
  
2.  在**“属性页”**对话框中的**“配置属性”**下选择**“调试”**。  
  
3.  在**“要启动的调试器”**列表中，选择**“本地 Windows 调试器”**。  
  
4.  在**“调试器类型”**列表中，选择**“仅 GPU”**。  
  
5.  选择**“确定”**按钮。  
  
6.  如下图所示，在30行处设置一个断点。  
  
     ![GPU 断点](../../parallel/amp/media/campgpubreakpoints.png "CampGpuBreakpoints")  
GPU断点  
  
7.  在菜单栏上，依次选择**“调试”**、**“启动调试”**。  因为这些代码行在CPU执行，在 CPU 代码67 和 70 行的断点在GPU调试期间不被执行。  
  
### 为了使用GPU线程窗口  
  
1.  若要打开 GPU 线程窗口，请在菜单栏上，依次选择 **调试**，**窗口**，**GPU 线程**。  
  
     可以在出现的GPU线程窗口中检查 GPU 线程的状态。  
  
2.  将GPU窗口停靠在 Visual Studio 底部。  选择 **展开某个线程切换** 按钮显示平铺和线程文本框。  如下图所示，GPU 线程窗口显示一段时间内活动和阻塞的 GPU 的线程总数。  
  
     ![包含 4 个活动线程的 GPU 线程窗口](../../parallel/amp/media/campc.png "CampC")  
GPU 线程窗口  
  
     为此计算分配 313 的图块。  每个平铺单元都包含 32 个线程。  由于本地的 GPU 调试在一个软件模拟器中发生，有四个活动的GPU线程。  四个线程同时执行指令。然后继续移动到下一条指令。  
  
     在 GPU 线程窗口，有四个活动GPU 线程和位于[tile\_barrier::wait](../Topic/tile_barrier::wait%20Method.md) GPU 线程信息块语句大约处定义行 21 \(`t_idx.barrier.wait();`\)的28个线程。  全部 32 GPU 线程属于第一个平铺，`tile[0]`。  指向包含当前线程行的箭头。  若要切换到其他线程，请使用下列方法之一：  
  
    -   在GPU线程窗口中线程可以切换到行，请打开快捷菜单中选择 **切换到线程**。  如果行表示多个线程，您将按线程坐标切换到第一个线程。  
  
    -   在相应的文本框中输入线程的平铺和线程值会，然后选择**切换线程** 按钮。  
  
     调用堆栈窗口显示当前 GPU 线程的调用堆栈。  
  
### 使用“并行堆栈”窗口  
  
1.  若要打开"并行堆栈"窗口，请在菜单栏上，依次选择 **调试**，**窗口**，**并行堆栈**。  
  
     可以使用"并行堆栈窗口同时检查多个 GPU 线程堆栈帧。  
  
2.  将并行栈”窗口停靠在 Visual Studio 底部。  
  
3.  确保在左上角的框中选择**“线程”**。  在下图中，"并行堆栈"窗口在GPU线程窗口显示GPU 线程的调用堆栈的集中视图。  
  
     ![包含 4 个活动线程的并行堆栈窗口](../../parallel/amp/media/campd.png "CampD")  
“并行堆栈”窗口  
  
     32 线程在 `parallel_for_each` 函数调用中从 `_kernel_stub` 以转到的 lambda语句以及 `sum_kernel_tiled` 函数，在并行降低发生的地方。28 从 32 个线程继续到 [tile\_barrier::wait](../Topic/tile_barrier::wait%20Method.md) 语句并保存阻止在行 22，而其他 4 个线程在 `sum_kernel_tiled` 函数保持活动在 30 行。  
  
     可以检查可在"并行堆栈"窗口中提供丰富的数据提示中的 GPU 线程窗口GPU 线程的属性。  为此，请将鼠标对准 **sum\_kernel\_tiled**堆栈帧上。  下图所示为数据提示。  
  
     ![并行堆栈窗口的数据提示](../../parallel/amp/media/campe.png "CampE")  
GPU 线程数据提示  
  
     有关“并行栈”窗口的更多信息，请参阅[使用“并行堆栈”窗口](../Topic/Using%20the%20Parallel%20Stacks%20Window.md)。  
  
### 显示“并行监视”窗口  
  
1.  若要打开"并行"监视"窗口，请在菜单栏上，依次选择 **调试**，**窗口**，**并行监视**，**并行监视 1**。  
  
     可以使用并行监视窗口来检查跨多个线程的一个表达式的值。  
  
2.  将Parallel Watch 1窗口停靠在 Visual Studio 底部。  在"并行监视"窗口具有 32 行，。  每个对应于出现在 GPU 线程窗口和"并行堆栈"窗口的GPU 线程。  现在，可以输入其值要在所有 32 GPU 线程中检查的表达式。  
  
3.  选择 **添加监视** 列标头，输入 `localIdx`，然后选择 Enter 键。  
  
4.  再次选择 **添加监视** 列标头，键入 `globalIdx`，然后选择 Enter 键。  
  
5.  再次选择 **添加监视** 列标头，键入 `localA[localIdx[0]]`，然后选择 Enter 键。  
  
     您可以通过选择相应的列标题来指定表达式来排序。  
  
     选择 **localA\[localIdx\[0\]\]** 列标头进行排序列。  下面图按 **localA\[localIdx\[0\]\]**显示排序结果。  
  
     ![包含分类结果的并行监视窗口](../../parallel/amp/media/campf.png "CampF")  
 排序结果  
  
     可以通过选中按钮然后选择**在 Excel 中打开**来导出在并行监视窗口的内容到Excel 。  如果在开发计算机上安装有 Excel，这将打开包含该内容的 Excel 工作表。  
  
6.  在并行监视窗口的右上角，有一个可以使用布尔表达式来筛选文件内容的筛选器控件。  筛选器控件文本框输入 `localA[localIdx[0]] > 20000` 的 Enter 键。  
  
     窗口现在包含 `localA[localIdx[0]]` 值大于 20000 的线程。  内容由仍 `localA[localIdx[0]]` 列排序，这是之前执行排序操作。  
  
## 标志 GPU 线程  
 可以在GPU 线程窗口通过对它们标记来制定特有的GPU线程，并行监视窗口，或者在"并行堆栈"窗口的数据提示。  如果在 GPU 线程窗口的一行包含多个线程，标志该行，包含在行的所有线程。  
  
### 标记GPU线程  
  
1.  选择在并行监视 1 窗口**\[线程\]** 列标题来通过平铺索引和线程索引来进行排序。  
  
2.  在菜单栏上，依次选择 **调试继续**，其中四个对于进程活动的线程转换为下个障碍 \(定义在 AMPMapReduce.cpp 行 32\)。  
  
3.  在包含四个处于活动状态的线程的行的左侧选择标志符号。  
  
     下面的插图在 GPU 线程窗口显示四个活动并且被标记的线程。  
  
     ![包含已标记线程的 GPU 线程窗口](../../parallel/amp/media/campg.png "CampG")  
GPU 线程窗口中的活动线程  
  
     并行"监视"窗口和"并行堆栈"窗口的数据提示将指示两个已标记线程。  
  
4.  如果您要关注所标志的四个线程，则在GPU线程 并行监视和"并行堆栈"窗口，选择显示被标记的线程。  
  
     在任何窗口或在 **调试位置** 工具栏仅选择显示标记的按钮。  下面的插图显示了在 **调试位置** 工具栏中显示只标记的按钮。  
  
     ![具有“仅显示已标记项”图标的“调试位置”工具栏](../Image/CampH.png "CampH")  
仅显示已标记项”按钮  
  
     现在 GPU 线程，并行监视和"并行堆栈"窗口仅显示标记的线程。  
  
## 冻结和解冻GPU线程  
 您可以从 GPU 线程窗口或并行监视窗口冻结 \(挂起\) 和解冻 \(恢复\) GPU 线程。  可以以相同的方法冻结和解冻线程 CPU ；有关信息，请参见 [如何：使用“线程”窗口](../Topic/How%20to:%20Use%20the%20Threads%20Window.md)。  
  
### 冻结和解冻GPU线程  
  
1.  选择 **仅显示标记** 按钮可以显示所有线程。  
  
2.  在菜单工具条，选择**“调试”**，选择**“继续”**。  
  
3.  打开活动行的快捷菜单，然后选择**“冻结”**。  
  
     下面的GPU 线程窗口插图显示，所有四个线程已冻结。  
  
     ![显示已冻结线程的 GPU 线程窗口](../../parallel/amp/media/campk.png "CampK")  
GPU 线程窗口中的已冻结线程  
  
     同样，并行监视窗口显示所有四个线程已冻结。  
  
4.  在菜单栏上，依次选择 **调试**，使用 **继续**来使下面 四个GPU线程继续过行 22的障碍到达3 行的断点。  GPU线程窗口显示，四个以前冻结的线程保留冻结和并且活动状态。  
  
5.  在菜单工具条，选择**“调试”**，选择**“继续”**。  
  
6.  从并行监视窗口，还可以单独解冻一个或同时解冻多个 GPU线程。  
  
### 分组GPU线程  
  
1.  在**GPU 线程** 窗口中的线程的快捷菜单，选择 **分组依据**，选择 **地址**。  
  
     在GPU线程窗口的线程由地址组合。  反汇编中每组线程所在的指令地址。24[tile\_barrier::wait 方法](../Topic/tile_barrier::wait%20Method.md) 的执行位置是行22中的线程 。线程12位于行32的障碍的指令中。  线程中的四个被标志。  八个线程在行 30的断点处。  线程中的已冻结。  下图显示了GPU线程窗口中处于分组模式下的线程。  
  
     ![其中的线程按地址进行分组的 GPU 线程窗口](../../parallel/amp/media/campl.png "CampL")  
GPU 线程窗口中的已分组线程  
  
2.  可以通过打开并行监视窗口中的数据网格的快捷菜单，选择 **分组依据**，再选择对应于要分组线程的菜单项执行 **分组依据** 操作。  
  
## 运行所有线程到特定代码中的指定位置。  
 在特定平铺中，通过使用 **将当前 Tile 运行到光标处**即可运行所有线程到包含光标的行。  
  
### 运行所有线程到光标指示的位置  
  
1.  冻结的线程在快捷菜单上，选择 **解冻**。  
  
2.  在代码编辑器中，将光标置于行 30。  
  
3.  在代码编辑器快捷菜单中，选择 **将当前 Tile 运行到光标处**。  
  
     以前被阻止在行 21 的障碍的 24 个线程继续到行 32。  在 **GPU 线程** 窗口中显示。  
  
## 请参阅  
 [C\+\+ AMP 概述](../../parallel/amp/cpp-amp-overview.md)   
 [调试 GPU 代码](../Topic/Debugging%20GPU%20Code.md)   
 [如何：使用“GPU 线程”窗口](../Topic/How%20to:%20Use%20the%20GPU%20Threads%20Window.md)   
 [如何：使用“并行监视”窗口](../Topic/How%20to:%20Use%20the%20Parallel%20Watch%20Window.md)   
 [使用并发可视化工具分析 C\+\+ AMP 代码](http://go.microsoft.com/fwlink/?LinkID=253987&clcid=0x409)