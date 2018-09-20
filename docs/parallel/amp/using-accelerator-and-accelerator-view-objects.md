---
title: 使用 accelerator 和 accelerator_view 对象 |Microsoft Docs
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
ms.openlocfilehash: c6427c9b30706cd7854cc1335e7459232ed1fa4a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402858"
---
# <a name="using-accelerator-and-acceleratorview-objects"></a>使用 accelerator 和 accelerator_view 对象

可以使用[accelerator](../../parallel/amp/reference/accelerator-class.md)并[accelerator_view](../../parallel/amp/reference/accelerator-view-class.md)类来指定设备或仿真器上运行 c + + AMP 代码。 系统可能有多个设备或仿真程序的内存量、 共享的内存支持、 调试支持或双精度支持不同的。 C + + Accelerated Massive Parallelism (c + + AMP) 提供了可用于检查可用快捷键设置一个默认值，指定对 parallel_for_each，多个调用多个加速器视图，执行特殊调试任务的 Api。

## <a name="using-the-default-accelerator"></a>使用默认快捷键

C + + AMP 运行时会选择默认快捷键，除非编写代码选择一个。 运行时选择默认快捷键，如下所示：

1. 如果在调试模式下运行应用程序，加速器支持调试。

2. 否则为如果将其设置 CPPAMP_DEFAULT_ACCELERATOR 环境变量，指定的加速器。

3. 否则为非模拟设备。

4. 否则为设备具有的最大可用内存量。

5. 否则为不附加到该显示屏的设备。

此外，运行时指定`access_type`的`access_type_auto`为默认快捷键。 这意味着默认快捷键使用共享的内存，如果它受支持，并且已知其性能特征 （带宽和延迟） 可与专用 （非共享） 内存相同。

可以通过构造默认快捷键并检查其属性来确定默认快捷键的属性。 下面的代码示例输出路径、 快捷键内存、 共享的内存支持、 双精度支持和默认快捷键的有限的双精度支持的数量。

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

可以设置 CPPAMP_DEFAULT_ACCELERATOR 环境变量以指定`accelerator::device_path`默认快捷键。 路径与硬件相关。 下面的代码使用`accelerator::get_all`函数来检索可用快捷键的列表，然后显示的路径和每个加速器的特征。

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

## <a name="selecting-an-accelerator"></a>选择一个快捷键

若要选择的快捷键，请使用`accelerator::get_all`方法来检索可用快捷键的列表，然后选择一个根据其属性。 此示例演示如何为具有最多内存的加速器：

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
> 一个返回的加速器`accelerator::get_all`是 CPU 快捷键。 无法在 CPU 加速器上执行代码。 若要筛选 CPU 快捷键，请将的值进行比较[device_path](reference/accelerator-class.md#device_path)属性返回的快捷键`accelerator::get_all`值为[accelerator:: cpu_accelerator](reference/accelerator-class.md#cpu_accelerator)。 有关详细信息，请参阅此文章中的"特殊快捷键"部分。

## <a name="shared-memory"></a>共享的内存

共享的内存是在 CPU 和加速器可以访问的内存。 使用共享内存消除或显著降低 CPU 和快捷键之间复制数据的开销。 尽管共享内存，但不能由 CPU 和加速器同时访问，这样会导致未定义的行为。 快捷键属性[supports_cpu_shared_memory](reference/accelerator-class.md#supports_cpu_shared_memory)返回**true**如果快捷键支持共享的内存，并且[default_cpu_access_type](reference/accelerator-class.md#default_cpu_access_type)属性获取默认值[access_type](reference/concurrency-namespace-enums-amp.md#access_type)上分配的内存`accelerator`— 例如，**数组**与关联`accelerator`，或`array_view`上访问的对象`accelerator`.

C + + AMP 运行时会自动选择最佳默认`access_type`为每个`accelerator`，但读取共享内存的性能特征 （带宽和延迟） 可能比不上专用 （非共享） 快捷键内存从编写从和 / 或 CPU，CPU。 如果共享的内存以及读取和写入从 CPU 的专用内存执行，运行时默认为`access_type_read_write`; 否则为则运行时会选择更保守的默认`access_type`，并允许此应用可以重写它如果内存访问计算内核模式受益于其他`access_type`。

下面的代码示例演示如何确定是否默认快捷键支持共享的内存，然后重写默认访问类型并创建`accelerator_view`从它。

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

`accelerator_view`始终反映`default_cpu_access_type`的`accelerator`它关联，并且它不提供接口来替代或更改其`access_type`。

## <a name="changing-the-default-accelerator"></a>更改默认快捷键

您可以通过调用来更改默认快捷键`accelerator::set_default`方法。 仅在每个应用程序执行，必须将其更改之前在 GPU 上执行的任何代码后，您可以更改默认快捷键。 任何后续的函数调用来更改加速器返回**false**。 如果你想要在调用中使用不同的快捷键`parallel_for_each`，阅读这篇文章中的"使用多个快捷键"一节。 下面的代码示例将默认快捷键设置为一个非仿真、 未连接到显示，并支持双精度。

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

有两种方法在应用中使用多个快捷键：

- 可以将传递`accelerator_view`对的调用的对象[parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each)方法。

- 您可以构造**数组**对象使用特定于`accelerator_view`对象。 C + AMP 运行时将选取`accelerator_view`对象从捕获**数组**lambda 表达式中的对象。

## <a name="special-accelerators"></a>特殊快捷键

三个特殊快捷键的设备路径是属性的形式提供`accelerator`类：

- [accelerator::direct3d_ref 数据成员](reference/accelerator-class.md#direct3d_ref)： 此单线程的快捷键使用 CPU 上软件来模拟泛型图形卡。 使用默认情况下进行调试，但并不用于生产，因为它是比硬件快捷键慢。 此外，它仅在 DirectX SDK 和 Windows SDK 中提供，它是不太可能安装在客户的计算机上。 有关详细信息，请参阅[调试 GPU 代码](/visualstudio/debugger/debugging-gpu-code)。

- [accelerator::direct3d_warp 数据成员](reference/accelerator-class.md#direct3d_warp)： 此快捷键提供用于使用流式处理 SIMD 扩展 (SSE) 的多核 Cpu 上执行 c + + AMP 代码的回退解决方案。

- [accelerator:: cpu_accelerator 数据成员](reference/accelerator-class.md#cpu_accelerator)： 你可以使用此快捷键设置暂存数组。 它不能执行 c + + AMP 代码。 有关详细信息，请参阅[c + + AMP 中的临时数组](https://blogs.msdn.microsoft.com/nativeconcurrency/2011/11/09/staging-arrays-in-c-amp/)本机代码博客中的并行编程上发布。

## <a name="interoperability"></a>互操作性

C + + AMP 运行时支持之间的互操作性`accelerator_view`类和 Direct3D [ID3D11Device 接口](/windows/desktop/api/d3d11/nn-d3d11-id3d11device)。 [Create_accelerator_view](reference/concurrency-direct3d-namespace-functions-amp.md#create_accelerator_view)方法采用`IUnknown`接口，并返回`accelerator_view`对象。 [Get_device](reference/concurrency-direct3d-namespace-functions-amp.md#get_device)方法采用`accelerator_view`对象，并返回`IUnknown`接口。

## <a name="see-also"></a>请参阅

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[调试 GPU 代码](/visualstudio/debugger/debugging-gpu-code)<br/>
[accelerator_view 类](../../parallel/amp/reference/accelerator-view-class.md)