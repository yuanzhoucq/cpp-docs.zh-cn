---
title: 使用 accelerator 和 accelerator_view 对象
ms.date: 11/04/2016
ms.assetid: 18f0dc66-8236-4420-9f46-1a14f2c3fba1
ms.openlocfilehash: 80d9c26f636cc736f90eacddea07a8fc31caff93
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512885"
---
# <a name="using-accelerator-and-accelerator_view-objects"></a>使用 accelerator 和 accelerator_view 对象

您可以使用[加速器](../../parallel/amp/reference/accelerator-class.md)和[accelerator_view](../../parallel/amp/reference/accelerator-view-class.md)类来指定要在其上运行C++ AMP 代码的设备或仿真程序。 系统可能有多个设备或仿真程序，它们的内存量、共享内存支持、调试支持或双精度支持有所不同。 C++加速的大规模并行C++度（AMP）提供可用于检查可用加速器的 api，将一个加速器设置为默认值，为多个对 parallel_for_each 的调用指定多个 accelerator_views，并执行特殊的调试任务。

## <a name="using-the-default-accelerator"></a>使用默认快捷键

C++ AMP 运行时选取默认加速器，除非你编写代码来选择特定加速器。 运行时选择默认快捷键，如下所示：

1. 如果应用在调试模式下运行，则为支持调试的快捷键。

2. 否则，由 CPPAMP_DEFAULT_ACCELERATOR 环境变量指定的快捷键（如果已设置）。

3. 否则为非模拟设备。

4. 否则为具有最大可用内存量的设备。

5. 否则，不会连接到显示器的设备。

此外，运行时还为`access_type`默认`access_type_auto`快捷键指定了的。 这意味着，如果支持共享内存，并且已知其性能特征（带宽和延迟）与专用（非共享）内存相同，则它将使用共享内存。

可以通过构造默认快捷键并检查其属性来确定默认快捷键的属性。 下面的代码示例将打印默认快捷键的路径、加速器内存量、共享内存支持、双精度支持和有限的双精度支持。

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

### <a name="cppamp_default_accelerator-environment-variable"></a>CPPAMP_DEFAULT_ACCELERATOR 环境变量

可以设置 CPPAMP_DEFAULT_ACCELERATOR 环境变量以指定`accelerator::device_path`默认快捷键的。 路径与硬件相关。 下面的代码使用`accelerator::get_all`函数检索可用加速器的列表，然后显示每个快捷键的路径和特征。

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

若要选择加速器，请使用`accelerator::get_all`方法检索可用加速器的列表，然后根据其属性选择一个快捷键。 此示例演示如何选取具有最多内存的加速器：

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
> 返回的一项加速器`accelerator::get_all`是 CPU 加速器。 不能在 CPU 加速器上执行代码。 若要筛选出 CPU 加速器，请将返回`accelerator::get_all`的快捷键的[device_path](reference/accelerator-class.md#device_path)属性的值与[快捷键：： cpu_accelerator](reference/accelerator-class.md#cpu_accelerator)的值进行比较。 有关详细信息，请参阅本文中的 "特殊加速器" 部分。

## <a name="shared-memory"></a>共享内存

共享内存是可以由 CPU 和加速器访问的内存。 使用共享内存可消除或大大降低在 CPU 和加速器之间复制数据的开销。 尽管内存是共享的，但它不能同时由 CPU 和加速器进行访问，这样做会导致未定义的行为。 如果快捷键支持 shared memory，则加速器属性[supports_cpu_shared_memory](reference/accelerator-class.md#supports_cpu_shared_memory)返回**true** ，[ default_cpu_access_type](reference/accelerator-class.md#default_cpu_access_type)属性获取为其 分配的内存的默认[access_type](reference/concurrency-namespace-enums-amp.md#access_type)例如， 与在上访问的 `accelerator` `accelerator` `array_view``accelerator`关联的数组。

AMP 运行时自动为每个`accelerator`选择`access_type`最佳默认值，但共享内存的性能特征（带宽和延迟）比专用（非共享）加速器内存的更糟C++从 CPU 读取，或从 CPU 写入。 如果共享内存执行以及用于从 CPU 进行读取和写入的专用内存，则运行时默认为`access_type_read_write`; 否则，运行时将选择一个更保守`access_type`的默认值，并允许应用在内存访问其计算内核的模式受益于不同`access_type`的。

下面的代码示例演示如何确定默认快捷键是否支持共享内存，然后重写其默认访问类型并`accelerator_view`从其创建。

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

`accelerator_view`始终反映`accelerator`与相关联的，并且不提供用于重写或更改其`access_type`的接口。 `default_cpu_access_type`

## <a name="changing-the-default-accelerator"></a>更改默认快捷键

可以通过调用`accelerator::set_default`方法来更改默认快捷键。 你只能在每次应用程序执行时更改默认快捷键一次，并且你必须在 GPU 上执行任何代码之前对其进行更改。 任何用于更改加速器的后续函数调用都将返回**false**。 如果要在调用`parallel_for_each`中使用其他加速器，请参阅本文中的 "使用多个加速器" 一节。 下面的代码示例将默认快捷键设置为一个未模拟、未连接到显示器并支持双精度的快捷键。

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

## <a name="using-multiple-accelerators"></a>使用多个加速器

可以通过两种方式在应用中使用多个加速器：

- 可以将对象`accelerator_view`传递给对[parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each)方法的调用。

- 您可以使用特定 `accelerator_view`的对象构造数组对象。 C + AMP 运行时将从 lambda 表达式`accelerator_view`中捕获的**数组**对象中提取对象。

## <a name="special-accelerators"></a>特殊加速器

三个特殊加速器的设备路径可用作`accelerator`类的属性：

- [加速器：:d Irect3d_ref 数据成员](reference/accelerator-class.md#direct3d_ref)：此单线程加速器使用 CPU 上的软件来模拟一般的图形卡。 默认情况下，它用于调试，但它在生产环境中不起作用，因为它比硬件加速器要慢。 此外，它仅在 DirectX SDK 和 Windows SDK 中提供，并且不太可能安装在客户的计算机上。 有关详细信息，请参阅[调试 GPU 代码](/visualstudio/debugger/debugging-gpu-code)。

- [加速器：:d Irect3d_warp 数据成员](reference/accelerator-class.md#direct3d_warp)：此加速器提供一个回退解决方案，用于C++在使用流式处理 simd 扩展（SSE）的多核 cpu 上执行 AMP 代码。

- [加速器：： Cpu_accelerator 数据成员](reference/accelerator-class.md#cpu_accelerator)：您可以使用此快捷键设置过渡阵列。 它无法执行C++ AMP 代码。 有关详细信息，请参阅本机代码博客中的并行编程中的[暂存阵列C++ ](https://blogs.msdn.microsoft.com/nativeconcurrency/2011/11/09/staging-arrays-in-c-amp/) 。

## <a name="interoperability"></a>互操作性

C++ AMP 运行时支持`accelerator_view`类和 Direct3D [ID3D11Device 接口](/windows/win32/api/d3d11/nn-d3d11-id3d11device)之间的互操作性。 [Create_accelerator_view](reference/concurrency-direct3d-namespace-functions-amp.md#create_accelerator_view)方法采用`IUnknown`接口并返回一个`accelerator_view`对象。 [Get_device](reference/concurrency-direct3d-namespace-functions-amp.md#get_device)方法采用`accelerator_view` `IUnknown`对象并返回接口。

## <a name="see-also"></a>请参阅

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[调试 GPU 代码](/visualstudio/debugger/debugging-gpu-code)<br/>
[accelerator_view 类](../../parallel/amp/reference/accelerator-view-class.md)
