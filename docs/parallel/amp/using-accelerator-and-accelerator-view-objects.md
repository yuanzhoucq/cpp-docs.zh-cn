---
title: "使用 accelerator 和 accelerator_view 对象 | Microsoft Docs"
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
ms.assetid: 18f0dc66-8236-4420-9f46-1a14f2c3fba1
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 accelerator 和 accelerator_view 对象
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您可以使用 [加速器](../../parallel/amp/reference/accelerator-class.md) 和 [accelerator_view](../../parallel/amp/reference/accelerator-view-class.md) 类来指定设备或仿真器运行 c + + AMP 代码。 一个系统可能有多个设备或仿真程序的内存量、 共享的内存支持、 调试支持或双精度支持上存在差异。 C + + Accelerated Massive Parallelism (c + + AMP) 提供了可用于检查可用快捷键将其中一个为默认设置，指定对 parallel_for_each，多个调用的多个 accelerator_view 上，执行特殊的调试任务的 Api。  
  
## <a name="using-the-default-accelerator"></a>使用默认快捷键  
 C + + AMP 运行时选取默认快捷键，除非您编写代码来选取其中一个。 则运行时会选择在默认快捷键，如下所示︰  
  
1.  如果在调试模式下运行该应用程序，加速器支持调试。  
  
2.  否则为指定由 CPPAMP_DEFAULT_ACCELERATOR 环境变量，如果将其设置的加速器。  
  
3.  否则为非模拟设备。  
  
4.  否则为具有最大程度的可用内存的设备。  
  
5.  否则为未附加到显示设备。  
  
 此外，运行时指定了 `access_type` 的 `access_type_auto` 默认快捷键。 这意味着在默认快捷键使用共享的内存，如果它受支持，并且已知其性能特征 （带宽和延迟） 都是相同 （非共享） 的专用内存。  
  
 您可以通过建立在默认快捷键并检查其属性来确定默认快捷键的属性。 下面的代码示例打印路径，加速器内存、 共享的内存支持、 双精度支持和有限的双精度支持在默认快捷键的量。  
  
```cpp  
 
void default_properties() {  
    accelerator default_acc;  
    std::wcout <<default_acc.device_path <<"\n";  
    std::wcout <<default_acc.dedicated_memory <<"\n";  
    std::wcout <<(accs[i].supports_cpu_shared_memory    
 "CPU shared memory: true" : "CPU shared memory: false") <<"\n";  
    std::wcout <<(accs[i].supports_double_precision    
 "double precision: true" : "double precision: false") <<"\n";  
    std::wcout <<(accs[i].supports_limited_double_precision    
 "limited double precision: true" : "limited double precision: false") <<"\n";  
}  
 
```  
  
### <a name="cppampdefaultaccelerator-environment-variable"></a>CPPAMP_DEFAULT_ACCELERATOR 环境变量  
 您可以设置 CPPAMP_DEFAULT_ACCELERATOR 环境变量以指定 `accelerator::device_path` 在默认快捷键。 路径是依赖于硬件。 下面的代码使用 `accelerator::get_all` 函数来检索可用快捷键的列表，然后显示的路径和每个加速器的特征。  
  
```cpp  
 
void list_all_accelerators()  
{  
    std::vector<accelerator> accs = accelerator::get_all();
for (int i = 0; i <accs.size();

i++) {  
    std::wcout <<accs[i].device_path <<"\n";  
    std::wcout <<accs[i].dedicated_memory <<"\n";  
    std::wcout <<(accs[i].supports_cpu_shared_memory    
 "CPU shared memory: true" : "CPU shared memory: false") <<"\n";  
    std::wcout <<(accs[i].supports_double_precision    
 "double precision: true" : "double precision: false") <<"\n";  
    std::wcout <<(accs[i].supports_limited_double_precision    
 "limited double precision: true" : "limited double precision: false") <<"\n";  
 }  
}  
 
```  
  
## <a name="selecting-an-accelerator"></a>选择加速器  
 若要选择加速器，请使用 `accelerator::get_all` 方法来检索可用快捷键的列表，然后选择一个基于其属性。 此示例演示如何选择具有最多内存的加速器︰  
  
```cpp  
 
void pick_with_most_memory()  
{  
    std::vector<accelerator> accs = accelerator::get_all();
accelerator acc_chosen = accs[0];  
    for (int i = 0; i <accs.size();

i++) {  
    if (accs[i].dedicated_memory> acc_chosen.dedicated_memory) {  
    acc_chosen = accs[i];  
 }  
 }  
 
    std::wcout <<"The accelerator with the most memory is "    
 <<acc_chosen.device_path <<"\n"  
 <<acc_chosen.dedicated_memory <<".\n";  
}  
 
```  
  
> [!NOTE]
>  一个由返回加速器 `accelerator::get_all` 是 CPU 快捷键。 不能在 CPU 快捷键上执行代码。 若要筛选出 CPU 快捷键，请将的值进行比较 [device_path](../Topic/accelerator::device_path%20Data%20Member.md) 属性所返回的加速器 `accelerator::get_all` 值为 [accelerator:: cpu_accelerator](../Topic/accelerator::cpu_accelerator%20Data%20Member.md)。 有关详细信息，请参阅此文章中的"特殊加速器"部分。  
  
## <a name="shared-memory"></a>共享的内存  
 共享的内存是 CPU 和加速器可以访问的内存。 使用共享内存可以消除或极大地减少了 CPU 和快捷键之间复制数据的开销。 尽管共享内存，但不能由 CPU 和加速器，同时访问，这样会导致未定义的行为。 快捷键属性 [supports_cpu_shared_memory](../Topic/accelerator::supports_cpu_shared_memory%20Data%20Member.md) 返回 `true` 快捷键支持共享的内存，如果与 [default_cpu_access_type](../Topic/accelerator::default_cpu_access_type%20Data%20Member.md) 属性获取的默认 [access_type](../Topic/access_type%20Enumeration.md) 上分配的内存为 `accelerator`— 例如， `array`与相关联 `accelerator`, ，或 `array_view` 对象上访问 `accelerator`。  
  
 C + + AMP 运行时将自动选择最佳默认 `access_type` 为每个 `accelerator`, ，但从 CPU，从 CPU，或这两者编写读取时，共享内存的性能特征 （带宽和延迟） 可以会比专用 （非共享） 加速器内存更糟。 如果共享的内存执行以及读取和写入来自 CPU 的专用内存时，运行时默认为 `access_type_read_write`; 否则为则运行时会选择更加保守默认 `access_type`, ，并允许应用程序以重写它，如果其计算内核的内存访问模式中得到好处来自不同 `access_type`。  
  
 下面的代码示例演示如何确定是否在默认快捷键支持共享的内存，然后重写其默认访问类型并创建 `accelerator_view` 从它。  
  
```cpp  
#include <amp.h>  
#include <iostream>  
  
using namespace Concurrency;  
  
int main()  
{  
  accelerator acc = accelerator(accelerator::default_accelerator);  
  
  // Early out if the default accelerator doesn’t support shared memory.  
  if(!acc.supports_cpu_shared_memory)  
  {  
    std::cout << "The default accelerator does not support shared memory" << std::endl;  
    return 1;  
  }  
  
  // Override the default CPU access type.  
  acc.set_default_cpu_access_type(access_type_read_write);  
  
  // Create an accelerator_view from the default accelerator. The  
  // accelerator_view reflects the default_cpu_access_type of the  
  // accelerator it’s associated with.  
  accelerator_view acc_v = acc.default_view;  
}  
  
```  
  
  `accelerator_view` 始终反映 `default_cpu_access_type` 的 `accelerator` 与其相关联，并不提供任何接口，以重写或更改其 `access_type`。  
  
## <a name="changing-the-default-accelerator"></a>更改默认快捷键  
 您可以通过调用来更改默认快捷键 `accelerator::set_default` 方法。 仅在后，每个应用程序执行，并且您必须将其更改在 GPU 上执行任何代码前，您可以更改默认快捷键。 若要更改快捷键的任何后续的函数调用返回 `false`。 如果想要对的调用中使用不同的加速器 `parallel_for_each`, ，阅读这篇文章中的"使用多个加速器"一节。 下面的代码示例将在默认快捷键设置为一个未仿真、 未连接到一个显示器，并支持双精度。  
  
```cpp  
 
    bool pick_accelerator()  
{  
    std::vector<accelerator> accs = accelerator::get_all();
accelerator chosen_one;  
 
    auto result = 
    std::find_if(accs.begin(), accs.end(), [] (const accelerator& acc)  
 {  
    return !acc.is_emulated&& 
    acc.supports_double_precision&& 
 !acc.has_display;  
 });

 
    if (result != accs.end())  
    chosen_one = *(result);

 
    std::wcout <<chosen_one.description <<std::endl;  
 
    bool success = accelerator::set_default(chosen_one.device_path);

    return success;  
}  
 
```  
  
## <a name="using-multiple-accelerators"></a>使用多个加速器  
 有两种方法要在您的应用程序中使用多个加速器︰  
  
-   您可以将传递 `accelerator_view` 对象传递给调用 [parallel_for_each](../Topic/parallel_for_each%20Function%20\(C++%20AMP\).md) 方法。  
  
-   您可以构造 `array` 对象使用特定 `accelerator_view` 对象。 C + AMP 运行时将提取 `accelerator_view` 对象从捕获 `array` lambda 表达式中的对象。  
  
## <a name="special-accelerators"></a>特殊加速器  
 三个特殊加速器的设备路径是否为属性的可用 `accelerator` 类︰  
  
- [accelerator:: direct3d_ref 数据成员](../Topic/accelerator::direct3d_ref%20Data%20Member.md)︰ 此单线程加速器使用 CPU 上的软件来模拟泛型图形卡。 使用默认情况下进行调试，但并不用于生产，因为它比硬件加速器要慢。 此外，它只是在 DirectX SDK 和 Windows SDK，也可不太可能安装到您的客户的计算机上。 有关详细信息，请参阅 [调试 GPU 代码](../Topic/Debugging%20GPU%20Code.md)。  
  
- [accelerator:: direct3d_warp 数据成员](../Topic/accelerator::direct3d_warp%20Data%20Member.md)︰ 此加速器提供了一个回退解决方案，用于使用流式处理 SIMD 扩展 (SSE) 的多核 Cpu 上执行 c + + AMP 代码。  
  
- [accelerator:: cpu_accelerator 数据成员](../Topic/accelerator::cpu_accelerator%20Data%20Member.md)︰ 可用于此加速器设置暂存数组。 它不能执行 c + + AMP 代码。 有关详细信息，请参阅 [c + + AMP 中的临时数组](http://go.microsoft.com/fwlink/p/LinkId=248485) 将发布到本机代码博客中的并行编程。  
  
## <a name="interoperability"></a>互操作性  
 C + + AMP 运行时支持之间的互操作性 `accelerator_view` 类和 Direct3D [ID3D11Device 接口](http://go.microsoft.com/fwlink/p/LinkId=248488)。  [Create_accelerator_view](../Topic/create_accelerator_view%20Function.md) 方法采用 `IUnknown` 接口，并返回 `accelerator_view` 对象。  [Get_device](http://msdn.microsoft.com/zh-cn/8194125e-8396-4d62-aa8a-65831dea8439) 方法采用 `accelerator_view` 对象，并返回 `IUknown` 接口。  
  
## <a name="see-also"></a>另请参阅  
 [C + + AMP (c + + Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)   
 [调试 GPU 代码](../Topic/Debugging%20GPU%20Code.md)   
 [accelerator_view 类](../../parallel/amp/reference/accelerator-view-class.md)
