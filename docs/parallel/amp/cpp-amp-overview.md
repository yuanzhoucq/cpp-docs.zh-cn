---
title: "C++ AMP 概述 | Microsoft Docs"
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
  - "C + + Accelerated Massive Parallelism 要求"
  - "C + + Accelerated Massive Parallelism，体系结构"
  - "C++ AMP"
  - "C + + Accelerated Massive Parallelism 概述"
  - "C++ Accelerated Massive Parallelism"
ms.assetid: 9e593b06-6e3c-43e9-8bae-6d89efdd39fc
caps.latest.revision: 60
caps.handback.revision: 60
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C++ AMP 概述
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

C + + Accelerated Massive Parallelism (c + + AMP) 通过利用在离散图形卡上的数据并行硬件的图形处理单元 (GPU) 如加快了 c + + 代码的执行。 通过使用 c + + AMP，您可以多维数据的算法进行编码，以便可以通过在异构硬件上使用并行加速执行。 C + + AMP 编程模型包括多维数组、 索引、 内存传输、 平铺和数学函数库。 C + + AMP 语言扩展可用于控制数据如何从 CPU 移动到 GPU 并返回，以便您可以提高性能。  
  
## <a name="system-requirements"></a>系统要求  
  
- [!INCLUDE[win7](../../build/includes/win7_md.md)]、[!INCLUDE[win8](../../build/includes/win8_md.md)]、[!INCLUDE[winsvr08_r2](../Token/winsvr08_r2_md.md)] 或 [!INCLUDE[winserver8](../../build/includes/winserver8_md.md)]  
  
-   DirectX 11 功能级别 11.0 或更高版本的硬件  
  
-   在软件模拟器上进行调试 [!INCLUDE[win8](../../build/includes/win8_md.md)] 或 [!INCLUDE[winserver8](../../build/includes/winserver8_md.md)] 是必需的。 对于在硬件上进行的调试，您必须为图形卡安装驱动程序。 有关详细信息，请参阅 [调试 GPU 代码](../Topic/Debugging%20GPU%20Code.md)。  
  
## <a name="introduction"></a>介绍  
 下面的两个示例说明了 c + + AMP 的主要组件。 假定您想要添加两个一维数组的对应元素。 例如，您可能想要添加 `{1, 2, 3, 4, 5}` 和 `{6, 7, 8, 9, 10}` 获取 `{7, 9, 11, 13, 15}`。 如果不使用 c + + AMP，您可以编写以下代码以添加一些数字并显示结果。  
  
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
  
 该代码的重要部分是，如下所示︰  
  
-   数据︰ 数据包含三个数组。 所有具有相同的秩为 (1) 和长度 （五个）。  
  
-   次迭代︰ 第一 `for` 循环提供用于循环访问数组中元素的机制。 您想要执行计算总和的代码包含在第一个 `for` 块。  
  
-   索引︰ `idx` 变量访问数组的各个元素。  
  
 使用 c + + AMP，你可能会改为编写下面的代码。  
  
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
 [=](index<1> idx) restrict(amp)  
    {  
        sum[idx] = a[idx] + b[idx];  
    }  
    );  
  
    // Print the results. The expected output is "7, 9, 11, 13, 15".  
    for (int i = 0; i < size; i++) {  
        std::cout << sum[i] << "\n";  
    }  
}  
  
```  
  
 相同的基本元素都不存在，但使用 c + + AMP 构造︰  
  
-   数据︰ 您使用 c + + 数组来构造三个 c + + AMP [array_view](../../parallel/amp/reference/array-view-class.md) 对象。 提供四个值来构造 `array_view` 对象︰ 数据值、 排名、 元素类型和长度 `array_view` 中每个维度对象。 秩和类型作为类型参数传递。 作为构造函数参数传递的数据和长度。 在此示例中，传递给构造函数的 c + + 数组是一维。 秩和长度用于构造中的数据的矩形形状 `array_view` 对象，并使用值来填充数组的数据。 运行时库还包括 [array 类](../../parallel/amp/reference/array-class.md), ，它具有类似于一个接口 `array_view` 类，并在本文稍后部分讨论。  
  
-   迭代︰ [parallel_for_each 函数 (c + + AMP)](../Topic/parallel_for_each%20Function%20\(C++%20AMP\).md) 提供一种机制，用于循环访问的数据元素，或 *计算域*。 在此示例中，指定的计算域 `sum.extent`。 您想要执行的代码包含在 lambda 表达式中，或 *内核函数*。  `restrict(amp)` 该值指示在使用仅 c + + AMP 可为其加速的 c + + 语言的子集。  
  
-   索引︰ [index 类](../../parallel/amp/reference/index-class.md) 变量， `idx`, ，用秩为 1 以匹配的秩声明 `array_view` 对象。 通过使用索引，您可以访问的各个元素 `array_view` 对象。  
  
## <a name="shaping-and-indexing-data-index-and-extent"></a>形成和索引数据: index 和 extent  
 必须定义数据值，并声明数据的形状，然后才能运行内核代码。 所有数据被都定义为数组 （矩形），并且可以定义数组具有任何秩 （维数）。 数据可以是任意大小中的任何维度。  
  
### <a name="index-class"></a>index 类  
  [Index 类](../../parallel/amp/reference/index-class.md) 指定中的某个位置 `array` 或 `array_view` 通过将于每个维度中的来源的偏移量封装到一个对象的对象。 当您访问该数组中的某个位置时，您传递 `index` 对象的索引运算符，与 `[]`, ，而不是整数索引的列表。 可以通过访问每个维度中的元素 [array:: operator （) 运算符](../Topic/array::operator\(\)%20Operator.md) 或 [array_view::operator() 运算符](../Topic/array_view::operator\(\)%20Operator.md)。  
  
 下面的示例创建一个一维索引，它指定第三个元素中的一维 `array_view` 对象。 索引用于打印中的第三个元素 `array_view` 对象。 输出为 3。  
  
```cpp  
 
int aCPP[] = {1, 2, 3, 4, 5};  
array_view<int, 1> a(5, aCPP);

index<1> idx(2);

std::cout <<a[idx] <<"\n";    
// Output: 3  
 
```  
  
 下面的示例创建一个二维索引，它指定的元素，行 = 1 和列 = 2 中一个二维 `array_view` 对象。 中的第一个参数 `index` 构造函数为行组件中，且第二个参数为表列组件。 输出为 6。  
  
```cpp  
 
int aCPP[] = {1, 2, 3,  
    4, 5, 6};  
array_view<int, 2> a(2, 3, aCPP);

index<2> idx(1, 2);

std::cout <<a[idx] <<"\n";  
// Output: 6  
 
```  
  
 下面的示例创建一个三维的索引，它指定的元素位置深度 = 0 时，行 = 1，并且该列 = 3 中的三维 `array_view` 对象。 请注意，第一个参数是深度组件、 第二个参数是表示行的分量和第三个参数是列组件。 输出为 8。  
  
```cpp  
 
int aCPP[] = {  
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12,   
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12};  
 
array_view<int, 3> a(2, 3, 4, aCPP);

// Specifies the element at 3, 1, 0.  
index<3> idx(0, 1, 3);

std::cout <<a[idx] <<"\n";  
 
// Output: 8  
 
```  
  
### <a name="extent-class"></a>extent 类  
  [Extent 类](../../parallel/amp/reference/extent-class-cpp-amp.md) 的每个维度中指定的数据长度 `array` 或 `array_view` 对象。 您可以创建扩展盘区并使用它来创建 `array` 或 `array_view` 对象。 您还可以检索现有的扩展盘区 `array` 或 `array_view` 对象。 下面的示例输出中的每个维度的范围的长度 `array_view` 对象。  
  
```cpp  
 
int aCPP[] = {  
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12,   
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12};  
// There are 3 rows and 4 columns, and the depth is two.  
array_view<int, 3> a(2, 3, 4, aCPP);

std::cout <<"The number of columns is " <<a.extent[2] <<"\n";  
std::cout <<"The number of rows is " <<a.extent[1] <<"\n";  
std::cout <<"The depth is " <<a.extent[0]<<"\n";  
std::cout <<"Length in most significant dimension is " <<a.extent[0] <<"\n";  
 
```  
  
 下面的示例创建 `array_view` 对象都将具有同一维度为上例中，但本示例中的对象使用 `extent` 对象而不是使用中的显式参数 `array_view` 构造函数。  
  
```cpp  
 
int aCPP[] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24};  
extent<3> e(2, 3, 4);

array_view<int, 3> a(e, aCPP);

std::cout <<"The number of columns is " <<a.extent[2] <<"\n";  
std::cout <<"The number of rows is " <<a.extent[1] <<"\n";  
std::cout <<"The depth is " <<a.extent[0] <<"\n";  
 
```  
  
## <a name="moving-data-to-the-accelerator-array-and-arrayview"></a>将数据移动到快捷键: array 和 array_view  
 中的运行时库定义了两个数据容器，用于将数据移到快捷键。 它们是 [array 类](../../parallel/amp/reference/array-class.md) 和 [array_view 类](../../parallel/amp/reference/array-view-class.md)。  `array` 类是一个容器类构造的对象时创建的数据的深层副本。  `array_view` 类是一个包装类，当在内核函数访问数据时，复制数据。 当源设备上所需要的数据时返回复制的数据。  
  
### <a name="array-class"></a>array 类  
 当 `array` 构造对象时，如果您使用的构造函数，包括指向数据集中的数据的深层副本在快捷键上创建。 在内核函数修改加速器的副本。 在内核函数执行完成后，必须将数据复制回源数据结构。 下面的示例用 10 乘以一个向量中的每个元素。 在内核函数完成后，[向量转换运算符 —] 后 brokenlink-(...用于将数据复制的 /Topic/array::operator%20std::vector%3Cvalue_type%3E%20Operator.md)is 传回的向量对象。  
  
```cpp  
 
std::vector<int> data(5);

for (int count = 0; count <5; count++)   
{  
    data[count] = count;  
}  
 
array<int, 1> a(5, data.begin(), data.end());

 
parallel_for_each(
    a.extent, 
 [=, &a](index<1> idx) restrict(amp)  
 {  
    a[idx] = a[idx]* 10;  
 });

 
data = a;  
for (int i = 0; i <5; i++)   
{  
    std::cout <<data[i] <<"\n";  
}  
 
```  
  
### <a name="arrayview-class"></a>array_view 类  
  `array_view` 具有几乎相同的成员 `array` 类，但基础行为并不相同。 数据传递到 `array_view` 构造函数不复制在 GPU 上，这一点与 `array` 构造函数。 相反，数据复制给快捷键执行内核函数时。 因此，如果创建两个 `array_view` 对象使用相同的数据，同时 `array_view` 对象引用同一个内存空间。 执行此操作时，您必须同步任何多线程的访问。 使用的主要优点 `array_view` 类是移动数据时，才有必要。  
  
### <a name="comparison-of-array-and-arrayview"></a>array 和 array_view 的比较  
 下表汇总的相似之处并之间的差异 `array` 和 `array_view` 类。  
  
|描述|array 类|array_view 类|  
|-----------------|-----------------|-----------------------|  
|当确定排名|在编译时。|在编译时。|  
|当确定范围|在运行时。|在运行时。|  
|形状|矩形。|矩形。|  
|数据存储|是数据容器。|是的数据包装。|  
|复制|在定义的显式和深层副本。|当在内核函数访问时的隐式副本。|  
|数据检索|通过将数组数据复制回 CPU 线程上的对象。|通过直接访问的 `array_view` 对象，或通过调用 [array_view:: synchronize 方法](../Topic/array_view::synchronize%20Method.md) 并继续访问原始容器上的数据。|  
  
### <a name="shared-memory-with-array-and-arrayview"></a>共享的内存、 array 和 array_view  
 共享的内存是 CPU 和加速器可以访问的内存。 使用共享内存可以消除或极大地减少了 CPU 和快捷键之间复制数据的开销。 尽管共享内存，但不能由 CPU 和加速器，同时访问，这样会导致未定义的行为。  
  
 `array` 对象可以用于指定对使用共享内存细化的控制，如果相关联的加速器支持它。 快捷键是否支持共享的内存由加速器的 [supports_cpu_shared_memory](../Topic/accelerator::supports_cpu_shared_memory%20Data%20Member.md) 属性，它返回 `true` 支持共享的内存时。 如果支持共享的内存，则默认值 [access_type 枚举](../Topic/access_type%20Enumeration.md) 对于内存分配加速器由 `default_cpu_access_type` 属性。 默认情况下， `array` 和 `array_view` 对象需要在同一个 `access_type` 关联为主 `accelerator`。  
  
 通过设置 [array:: cpu_access_type 数据成员](../Topic/array::cpu_access_type%20Data%20Member.md) 属性 `array` 显式，您可以练习细粒度控制通过如何共享内存的使用，以便您可以优化硬件的性能特征，根据其计算内核的内存访问模式对该应用程序。  `array_view` 反映相同 `cpu_access_type` 作为 `array` 是与其相关联; 或者，如果 array_view 构造不使用数据源，其 `access_type` 反映了第一次后，即可分配存储的环境。 也就是说，如果它第一次访问主机 (CPU)，然后其行为就像创建对 CPU 数据源和共享 `access_type` 的 `accelerator_view` 通过捕获相关联; 但是，如果先访问 `accelerator_view`, ，则其行为就像通过创建 `array` 上，创建 `accelerator_view` 和共享 `array`的 `access_type`。  
  
 下面的代码示例演示如何确定是否在默认快捷键支持共享的内存，然后创建具有不同 cpu_access_type 配置的多个数组。  
  
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
  
## <a name="executing-code-over-data-parallelforeach"></a>对数据执行代码: parallel_for_each  
  [Parallel_for_each](../Topic/parallel_for_each%20Function%20\(C++%20AMP\).md) 函数定义你想要在针对中的数据的加速器上运行的代码 `array` 或 `array_view` 对象。 请考虑本主题的简介中的以下代码。  
  
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
  
  `parallel_for_each` 方法采用两个参数，计算域和 lambda 表达式。  
  
  *计算域* 是 `extent` 对象或 `tiled_extent` 对象，它定义的一组线程来并行执行的创建。 为计算域中的每个元素生成一个线程。 在这种情况下， `extent` 对象是一维，具有五个元素。 因此，五个线程才会启动。  
  
  *Lambda 表达式* 定义在每个线程上运行的代码。 Capture 子句 `[=]`, ，指定 lambda 表达式的主体通过值，该值在这种情况下访问所有捕获的变量 `a`, ，`b`, ，和 `sum`。 在此示例中，参数列表将创建一维 `index` 变量名为 `idx`。 值 `idx[0]` 是 0，在第一个线程，将会增加一个在每个后续线程。  `restrict(amp)` 该值指示在使用仅 c + + AMP 可为其加速的 c + + 语言的子集。  中介绍了对都有限制修饰符的函数的限制 [限制 (c + + AMP)](../../cpp/restrict-cpp-amp.md)。 有关详细信息，请参阅， [Lambda 表达式语法](../../cpp/lambda-expression-syntax.md)。  
  
 Lambda 表达式可以包括要执行的代码，或者它可以调用单独的内核函数。 在内核函数必须包括 `restrict(amp)` 修饰符。 下面的示例是等效于上述示例中，但它调用单独的内核函数。  
  
```cpp  
  
#include <amp.h>  
#include <iostream>  
using namespace concurrency;  
  
void AddElements(index<1> idx, array_view<int, 1> sum, array_view<int, 1> a, array_view<int, 1> b) restrict(amp)  
{  
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
 [=](index<1> idx) restrict(amp)  
        {  
            AddElements(idx, sum, a, b);  
        }  
    );  
  
    for (int i = 0; i < 5; i++) {  
        std::cout << sum[i] << "\n";  
    }  
}  
  
```  
  
## <a name="accelerating-code-tiles-and-barriers"></a>加速代码: 平铺和屏障  
 您可以通过使用平铺获得其他的加速。 平铺将线程划分为相等的矩形子集或 *磁贴*。 确定基于您的数据集以及您在编码的算法的相应的磁贴大小。 对于每个线程，您有权 *全局* 相对于整个数据元素的位置 `array` 或 `array_view` 并允许访问 *本地* 相对于图块的位置。 使用本地的索引值可以简化您的代码，因为无需编写代码以将从全局到本地的索引值翻译。 若要使用平铺，调用 [extent:: tile 方法](../Topic/extent::tile%20Method.md) 中计算域上 `parallel_for_each` 方法，并使用 [tiled_index](../../parallel/amp/reference/tiled-index-class.md) lambda 表达式中的对象。  
  
 与典型的应用程序磁贴中的元素相关以某种方式的代码具有访问和跟踪在图块之间的值。 使用 [tile_static 关键字](../../cpp/tile-static-keyword.md) 关键字和 [tile_barrier:: wait 方法](../Topic/tile_barrier::wait%20Method.md) 为实现此目的。 一个具有变量 `tile_static` 关键字的整个图块中，具有一个作用域，并且为每个图块中创建的变量的实例。 您必须处理同步磁贴线程访问该变量。  [Tile_barrier:: wait 方法](../Topic/tile_barrier::wait%20Method.md) 停止执行当前线程，直至磁贴中的所有线程都已都达到调用 `tile_barrier::wait`。 因此可以通过使用在该图块之间累积值 `tile_static` 变量。 然后您可以完成任何需要访问的所有值的计算。  
  
 下图描绘抽样在磁贴中排列的数据的二维的数组。  
  
 ![平铺范围中的索引值](../../parallel/amp/media/camptiledgridexample.png "CampTiledGridExample")  
  
 下面的代码示例使用上面的关系图中的采样数据。 这段代码通过磁贴中值的平均值替换磁贴中的每个值。  
  
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

 
parallel_for_each(*// Create threads for sample.extent and divide the extent into 2 x 2 tiles.  
    sample.extent.tile<2,2>(), 
 [=](tiled_index<2,2> idx) restrict(amp)  
 { *// Create a 2 x 2 array to hold the values in this tile.  
    tile_static int nums[2][2]; *// Copy the values for the tile into the 2 x 2 array.  
    nums[idx.local[1]][idx.local[0]] = sample[idx.global]; *// When all the threads have executed and the 2 x 2 array is complete, find the average.  
    idx.barrier.wait();
int sum = nums[0][0] + nums[0][1] + nums[1][0] + nums[1][1]; *// Copy the average into the array_view.  
    average[idx.global] = sum / 4;  
 });

 
for (int i = 0; i <4; i++) {  
    for (int j = 0; j <6; j++) {  
    std::cout <<average(i,j) <<" ";  
 }  
    std::cout <<"\n";  
}  
 
// Output:  
// 3 3 8 8 3 3  
// 3 3 8 8 3 3  
// 5 5 2 2 4 4  
// 5 5 2 2 4 4  
 
```  
  
## <a name="math-libraries"></a>数学库  
 C + + AMP 包括两个数学库。 中的双精度库 [concurrency:: precise_math Namespace](../../parallel/amp/reference/concurrency-precise-math-namespace.md) 为双精度功能提供支持。 它还支持对于单精度函数，尽管在硬件上的双精度支持，则仍需要。 它将符合 [C99 规范 (ISO/IEC 9899)](http://go.microsoft.com/fwlink/LinkId=225887)。 该加速器必须支持完整双精度。 您可以确定是否是通过检查的值 [accelerator:: supports_double_precision 数据成员](../Topic/accelerator::supports_double_precision%20Data%20Member.md)。 快速的数学库，请在 [concurrency:: fast_math Namespace](../../parallel/amp/reference/concurrency-fast-math-namespace.md), ，包含另一套数学函数。 这些函数，仅支持 `float` 操作数，更快地执行，但并不那么精确的双精度算术库中。 函数都包含在 \< amp_math.h > 标头文件和所有声明与 `restrict(amp)`。 中的函数 \< cmath> 标头文件导入这两 `fast_math` 和 `precise_math` 命名空间。  `restrict` 关键字用于区分 \< cmath> 版本和 c + + AMP 版本。 下面的代码计算的以 10 为基数的对数，使用计算域中的每个值的快速方法。  
  
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
            logs[idx] = concurrency::fast_math::log10(logs[idx]);  
        }  
    );  
  
    for (int i = 0; i < 6; i++) {  
        std::cout << logs[i] << "\n";  
    }  
}  
  
```  
  
## <a name="graphics-library"></a>图形库  
 C + + AMP 包括专为加速图形编程的图形库。 仅在支持本机的图形功能的设备上使用此库。 方法位于 [concurrency:: graphics Namespace](../../parallel/amp/reference/concurrency-graphics-namespace.md) 以及包含在 \< amp_graphics.h > 标头文件。 图形库的关键组件包括︰  
  
- [texture 类](../../parallel/amp/reference/texture-class.md)︰ 可以使用纹理类以从内存或从文件创建纹理。 纹理类似于数组，因为它们包含的数据，并且它们类似于在标准模板库 (STL) 分配和复制构造方面的容器。 有关详细信息，请参阅 [STL 容器](../../standard-library/stl-containers.md)。 模板参数 `texture` 类就是类似的元素类型和级别。 秩可以是 1、 2 或 3。 元素类型可以是在本文的后面进行介绍的短矢量类型之一。  
  
- [writeonly_texture_view 类](../../parallel/amp/reference/writeonly-texture-view-class.md)︰ 提供对任何纹理的只写访问。  
  
- [短矢量库](http://msdn.microsoft.com/zh-cn/4c4f5bed-c396-493b-a238-c347563f645f)︰ 定义的短矢量类型，长度为 2、 3 和 4 根据一组 `int`, ，`uint`, ，`float`, ，`double`, ，[norm](../../parallel/amp/reference/norm-class.md), ，或 [unorm](../../parallel/amp/reference/unorm-class.md)。  
  
## <a name="includewin8appnamelongtokenwin8appnamelongmdmd-apps"></a>[!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序  
 像其他 c + + 库，您可以使用 c + + AMP 中您 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序。 这些文章介绍如何将 c + + AMP 代码包含在应用程序使用 c + +、 C#、 Visual Basic 或 JavaScript 创建︰  
  
- [在 Windows 应用商店应用中使用 c + + AMP](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)  
  
- [演练︰ 在 c + + 中创建基本 Windows 运行时组件并从 JavaScript 中调用](http://go.microsoft.com/fwlink/p/LinkId=249077)  
  
- [Bing 地图行程优化器，以 JavaScript 和 c + + 的 Window 应用商店应用](http://go.microsoft.com/fwlink/p/LinkId=249078)  
  
- [如何使用 c + + AMP 从 C# 中使用 Windows 运行时](http://go.microsoft.com/fwlink/p/LinkId=249080)  
  
- [如何使用 C# 中的 c + + AMP](http://go.microsoft.com/fwlink/p/LinkId=249081)  
  
- [从托管代码调用本机函数](../../dotnet/calling-native-functions-from-managed-code.md)  
  
## <a name="c-amp-and-concurrency-visualizer"></a>C++ AMP 和并发可视化工具  
 并发可视化工具包括用于分析性能的 c + + AMP 代码的支持。 这些文章介绍了这些功能︰  
  
- [GPU 活动关系图](../Topic/GPU%20Activity%20Graph.md)  
  
- [GPU 活动 （分页）](../Topic/GPU%20Activity%20\(Paging\).md)  
  
- [GPU 活动 （此进程）](../Topic/GPU%20Activity%20\(This%20Process\).md)  
  
- [GPU 活动 （其他进程）](../Topic/GPU%20Activity%20\(Other%20Processes\).md)  
  
- [通道 （线程视图）](../Topic/Channels%20\(Threads%20View\).md)  
  
- [使用并发可视化工具分析 c + + AMP 代码](http://go.microsoft.com/fwlink/LinkID=253987&clcid=0x409)  
  
## <a name="performance-recommendations"></a>性能建议  
 取模和个无符号整数的减法有性能明显高于模数和部门的有符号整数。 我们建议使用无符号的整数，在可能的情况。  
  
## <a name="see-also"></a>另请参阅  
 [C + + AMP (c + + Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)   
 [Lambda 表达式语法](../../cpp/lambda-expression-syntax.md)   
 [参考 (c + + AMP)](../../parallel/amp/reference/reference-cpp-amp.md)   
 [本机代码博客中的并行编程](http://go.microsoft.com/fwlink/p/LinkId=238472)
