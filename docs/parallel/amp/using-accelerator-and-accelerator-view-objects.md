---
title: 使用 accelerator 和 accelerator_view 对象 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 18f0dc66-8236-4420-9f46-1a14f2c3fba1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9e0f86467de8256eaecbfbf42765de551a1e2f6e
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33690606"
---
# <a name="using-accelerator-and-acceleratorview-objects"></a>使用 accelerator 和 accelerator_view 对象
你可以使用[快捷键](../../parallel/amp/reference/accelerator-class.md)和[accelerator_view](../../parallel/amp/reference/accelerator-view-class.md)指定设备或仿真程序在运行 c + + AMP 代码的类。 系统可能具有多个设备或仿真程序的内存、 共享的内存支持、 调试支持或双精度支持量上存在差异。 C + + Accelerated Massive Parallelism (c + + AMP) 提供 Api，可用于检查可用快捷键、 设置另一个用作默认值、 指定多个 accelerator_view 上以便 parallel_for_each，多个调用和执行特殊的调试任务。  
  
## <a name="using-the-default-accelerator"></a>使用默认快捷键  
 C + + AMP 运行时选取默认快捷键，除非你编写代码以选取一个。 则运行时会选择默认快捷键，如下所示：  
  
1.  如果在调试模式下运行应用程序，加速器支持调试。  
  
2.  否则为如果设置 CPPAMP_DEFAULT_ACCELERATOR 环境变量，指定的快捷键。  
  
3.  否则为非仿真的设备。  
  
4.  否则为具有最大程度的可用内存的设备。  
  
5.  否则为不附加到显示设备。  
  
 此外，运行时指定`access_type`的`access_type_auto`默认快捷键。 这意味着如果它支持，并且其性能特征 （带宽和延迟） 都已知为专用 （非共享） 的内存相同，默认快捷键都将使用共享的内存。  
  
 你可以确定默认快捷键的属性，方法是构造默认快捷键并检查其属性。 下面的代码示例将打印路径，快捷键内存、 共享的内存支持、 双精度支持和有限的双精度支持的默认快捷键的量。  
  
```cpp  
void default_properties() {  
    accelerator default_acc;  
    std::wcout << default_acc.device_path << "\n";  
    std::wcout << default_acc.dedicated_memory << "\n";  
    std::wcout << (accs[i].supports_cpu_shared_memory ?   
        "CPU shared memory: true" : "CPU shared memory: false") << "\n";  
    std::wcout << (accs[i].supports_double_precision ?   
        "double precision: true" : "double precision: false") << "\n";  
    std::wcout << (accs[i].supports_limited_double_precision ?   
        "limited double precision: true" : "limited double precision: false") << "\n";  
}  
 
```  
  
### <a name="cppampdefaultaccelerator-environment-variable"></a>CPPAMP_DEFAULT_ACCELERATOR 环境变量  
 你可以设置 CPPAMP_DEFAULT_ACCELERATOR 环境变量，以指定`accelerator::device_path`的默认快捷键。 路径与硬件相关。 下面的代码使用`accelerator::get_all`函数来检索可用快捷键的列表，然后显示的路径和每个加速器的特征。  
  
```cpp  
void list_all_accelerators()  
{  
    std::vector<accelerator> accs = accelerator::get_all();  
  
    for (int i = 0; i <accs.size(); i++) {  
        std::wcout << accs[i].device_path << "\n";  
        std::wcout << accs[i].dedicated_memory << "\n";  
        std::wcout << (accs[i].supports_cpu_shared_memory ?   
            "CPU shared memory: true" : "CPU shared memory: false") << "\n";  
        std::wcout << (accs[i].supports_double_precision ?   
            "double precision: true" : "double precision: false") << "\n";  
        std::wcout << (accs[i].supports_limited_double_precision ?   
            "limited double precision: true" : "limited double precision: false") << "\n";  
    }  
}  
```  
  
## <a name="selecting-an-accelerator"></a>选择加速器  
 若要选择加速器，使用`accelerator::get_all`方法检索可用快捷键的列表，然后选择一个基于其属性。 此示例演示如何选择具有最多内存的快捷键：  
  
```cpp  
void pick_with_most_memory()  
{  
    std::vector<accelerator> accs = accelerator::get_all();
    accelerator acc_chosen = accs[0];  
    
    for (int i = 0; i <accs.size(); i++) {  
        if (accs[i].dedicated_memory> acc_chosen.dedicated_memory) {  
            acc_chosen = accs[i];  
        }  
    }  
 
    std::wcout << "The accelerator with the most memory is "    
        << acc_chosen.device_path << "\n"  
        << acc_chosen.dedicated_memory << ".\n";  
}  
```  
  
> [!NOTE]
>  返回的加速器之一`accelerator::get_all`是 CPU 快捷键。 不能在 CPU 快捷键执行代码。 若要筛选出 CPU 快捷键，请将的值进行比较[device_path](reference/accelerator-class.md#device_path)属性返回的加速器`accelerator::get_all`值为[accelerator:: cpu_accelerator](reference/accelerator-class.md#cpu_accelerator)。 有关详细信息，请参阅此文章中的"特殊快捷键"部分。  
  
## <a name="shared-memory"></a>共享的内存  
 共享的内存是 CPU 和快捷键可以访问的内存。 共享内存的使用可以消除或大幅减少 CPU 和快捷键之间复制数据的开销。 尽管内存共享的不能 CPU 和快捷键，同时访问和这样做会导致未定义的行为。 快捷键属性[supports_cpu_shared_memory](reference/accelerator-class.md#supports_cpu_shared_memory)返回`true`如果快捷键支持共享的内存和[default_cpu_access_type](reference/accelerator-class.md#default_cpu_access_type)属性获取默认[access_type](reference/concurrency-namespace-enums-amp.md#access_type)上分配的内存`accelerator`— 例如，`array`与关联`accelerator`，或`array_view`对象上访问`accelerator`。 
  
 C + + AMP 运行时会自动选择最佳默认`access_type`每个`accelerator`，但在读取时，共享内存的性能特征 （带宽和延迟） 可以是不如那些专用 （非共享） 加速器内存从编写从和 / 或 CPU，CPU。 如果共享的内存执行以及读取和写入 CPU 中的专用内存时，运行时将默认为`access_type_read_write`; 否则为则运行时会选择更保守的默认`access_type`，并允许应用程序以重写此方法如果内存访问其计算内核模式受益于不同`access_type`。  
  
 下面的代码示例演示如何确定是否默认快捷键支持共享的内存，然后重写其默认访问类型并创建`accelerator_view`从它。  
  
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
    acc.set_default_cpu_access_type(access_type_read_write);  
  
    // Create an accelerator_view from the default accelerator. The  
    // accelerator_view reflects the default_cpu_access_type of the  
    // accelerator it’s associated with.  
    accelerator_view acc_v = acc.default_view;  
}  
```  
  
 `accelerator_view`始终反映`default_cpu_access_type`的`accelerator`与其相关联，并提供没有界面以重写或更改其`access_type`。  
  
## <a name="changing-the-default-accelerator"></a>更改默认快捷键  
 你可以通过调用来更改默认快捷键`accelerator::set_default`方法。 仅当每个应用程序执行，你必须更改它在 GPU 上执行任何代码之前，你可以更改默认快捷键。 若要更改快捷键任何后续的函数调用返回`false`。 如果你想要对的调用中使用不同的快捷键`parallel_for_each`，阅读此文章中的"使用多个快捷键"部分。 下面的代码示例将设置为一个非仿真、 未连接到的显示器，并支持双精度的默认快捷键。  
  
```cpp  
bool pick_accelerator()  
{  
    std::vector<accelerator> accs = accelerator::get_all();
    accelerator chosen_one;  
 
    auto result = std::find_if(accs.begin(), accs.end(), 
        [] (const accelerator& acc) {  
            return !acc.is_emulated && 
                acc.supports_double_precision && 
                !acc.has_display;  
        });
  
    if (result != accs.end()) {  
        chosen_one = *(result);
    }
  
    std::wcout <<chosen_one.description <<std::endl;  
    bool success = accelerator::set_default(chosen_one.device_path);
    return success;  
}  
```  
  
## <a name="using-multiple-accelerators"></a>使用多个快捷键  
 有两种方法可以在应用中使用多个快捷键：  

-   你可以将传递`accelerator_view`对象对的调用与[parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each)方法。  
  
-   您可以构造`array`对象使用特定`accelerator_view`对象。 C + AMP 运行时将选取`accelerator_view`对象从捕获`array`lambda 表达式中的对象。  
  
## <a name="special-accelerators"></a>特殊的快捷键  
 三个特殊快捷键的设备路径都可用作属性`accelerator`类：  
  
- [accelerator:: direct3d_ref 数据成员](reference/accelerator-class.md#direct3d_ref)： 此单线程的加速器使用 CPU 上软件来模拟泛型图形卡。 它用于默认情况下调试，但它不是在生产环境中有用因为低于硬件加速器。 另外，它将仅可用于 DirectX SDK 和 Windows SDK 中，并且它不太可能在客户的计算机上安装。 有关详细信息，请参阅[调试 GPU 代码](/visualstudio/debugger/debugging-gpu-code)。  
  
- [accelerator:: direct3d_warp 数据成员](reference/accelerator-class.md#direct3d_warp)： 此加速器提供用于使用流式处理 SIMD 扩展 (SSE) 的多核 Cpu 上执行 c + + AMP 代码的回退解决方案。  
  
- [accelerator:: cpu_accelerator 数据成员](reference/accelerator-class.md#cpu_accelerator)： 可用于此加速器设置暂存数组。 它不能执行 c + + AMP 代码。 有关详细信息，请参阅[c + + AMP 中的临时数组](http://go.microsoft.com/fwlink/p/?linkId=248485)在本机代码博客中的并行编程上发布。  
  
## <a name="interoperability"></a>互操作性  
 C + + AMP 运行时支持之间的互操作性`accelerator_view`类和 Direct3D [ID3D11Device 接口](http://go.microsoft.com/fwlink/p/?linkId=248488)。 [Create_accelerator_view](reference/concurrency-direct3d-namespace-functions-amp.md#create_accelerator_view)方法采用`IUnknown`接口并返回`accelerator_view`对象。 [Get_device](http://msdn.microsoft.com/en-us/8194125e-8396-4d62-aa8a-65831dea8439)方法采用`accelerator_view`对象，并返回`IUknown`接口。  
  
## <a name="see-also"></a>请参阅  
 [C + + AMP (c + + Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)   
 [调试 GPU 代码](/visualstudio/debugger/debugging-gpu-code)   
 [accelerator_view 类](../../parallel/amp/reference/accelerator-view-class.md)
