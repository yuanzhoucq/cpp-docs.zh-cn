---
title: 在 UWP 应用中使用 c + + AMP
ms.date: 11/04/2016
ms.assetid: 85577298-2c28-4209-9470-eb21048615db
ms.openlocfilehash: 9e17cb8691408d664f403b53e9cd8ad70fe6e5e0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447746"
---
# <a name="using-c-amp-in-uwp-apps"></a>在 UWP 应用中使用 c + + AMP

可以使用通用 Windows 平台 (UWP) 应用程序中的 c + + AMP (c + + Accelerated Massive Parallelism) 在 GPU （图形处理单元） 或其他计算加速器上执行计算。 但是，C++ AMP 不提供用于直接处理 Windows 运行时类型的 API，并且 Windows 运行时不提供 C++ AMP 包装器。 当你在代码（包括你自己创建的代码）中使用Windows 运行时类型时，必须将它们转换为与 C++ AMP 兼容的类型。

## <a name="performance-considerations"></a>性能注意事项

如果正在使用 Visual c + + 组件扩展 C + + /cli CX 创建通用 Windows 平台 (UWP) 应用，我们建议使用纯旧数据 (POD) 类型和连续存储 — 例如，`std::vector`或 C 样式数组 — 将数据与 c + + AMP 一起使用。 这可以帮助您获得更高的性能比使用非 POD 类型或 Windows RT 容器，因为没有封送处理有发生。

在 c + + AMP 内核，访问数据存储在这种方式，我们只需封装`std::vector`或数组中的存储`concurrency::array_view`，然后使用数组视图中的`concurrency::parallel_for_each`循环：

```cpp
// simple vector addition example
std::vector<int> data0(1024, 1);
std::vector<int> data1(1024, 2);
std::vector<int> data_out(data0.size(), 0);

concurrency::array_view<int, 1> av0(data0.size(), data0);
concurrency::array_view<int, 1> av1(data1.size(), data1);
concurrency::array_view<int, 1> av2(data_out.size(), data2);

av2.discard_data();

concurrency::parallel_for_each(av0.extent, [=](concurrency::index<1> idx) restrict(amp)
    {
        av2[idx] = av0[idx] + av1[idx];
    });
```

## <a name="marshaling-windows-runtime-types"></a>排列 Windows 运行时类型

与 Windows 运行时 Api 时，你可能想要在如 Windows 运行时容器中存储的数据使用 c + + AMP`Platform::Array<T>^`或在复杂数据类型，例如通过使用声明的类或结构**ref**关键字或**值**关键字。 在这些情况下，必须执行一些额外工作，以使数据可供 c + + AMP。

### <a name="platformarrayt-where-t-is-a-pod-type"></a>Platform:: array\<T > ^，其中 T 为 POD 类型

当遇到`Platform::Array<T>^`和 T 为 POD 类型，你可以只需通过使用访问其基础存储`get`成员函数：

```cpp
Platform::Array<float>^ arr; // Assume that this was returned by a Windows Runtime API
concurrency::array_view<float, 1> av(arr->Length, &arr->get(0));
```

如果 T 不是 POD 类型，使用下一节中所述的技术与 c + + AMP 中使用的数据。

### <a name="windows-runtime-types-ref-classes-and-value-classes"></a>Windows 运行时类型: 引用类和值类

C + + AMP 不支持复杂数据类型。 这包括非 POD 类型和通过使用声明的任何类型**ref**关键字或**值**关键字。 如果不支持的类型中使用`restrict(amp)`生成上下文，编译时错误。

遇到不支持的类型，可以将复制到其数据的有趣部分`concurrency::array`对象。 除了使数据可用于 c + + AMP 可使用，此手动复制方法还可以提高性能，通过最大化数据局部性以及确保不会使用的数据不会复制到快捷键。 可以通过使用提高性能进一步*暂存数组*，这是一种特殊形式`concurrency::array`，它提供对 AMP 运行时数组应进行优化和其他数组之间的频繁传输上的提示指定的加速器。

```cpp
// pixel_color.h
ref class pixel_color sealed
{
public:
    pixel_color(Platform::String^ color_name, int red, int green, int blue)
    {
        name = color_name;
        r = red;
        g = green;
        b = blue;
    }

    property Platform::String^ name;
    property int r;
    property int g;
    property int b;
};

// Some other file

std::vector<pixel_color^> pixels (256);

for (pixel_color ^pixel : pixels)
{
    pixels.push_back(ref new pixel_color("blue", 0, 0, 255));
}

// Create the accelerators
auto cpuAccelerator = concurrency::accelerator(concurrency::accelerator::cpu_accelerator);
auto devAccelerator = concurrency::accelerator(concurrency::accelerator::default_accelerator);

// Create the staging arrays
concurrency::array<float, 1> red_vec(256, cpuAccelerator.default_view, devAccelerator.default_view);
concurrency::array<float, 1>  blue_vec(256, cpuAccelerator.default_view, devAccelerator.default_view);

// Extract data from the complex array of structs into staging arrays.
concurrency::parallel_for(0, 256, [&](int i)
    {
        red_vec[i] = pixels[i]->r;
        blue_vec[i] = pixels[i]->b;
    });

// Array views are still used to copy data to the accelerator
concurrency::array_view<float, 1> av_red(red_vec);
concurrency::array_view<float, 1> av_blue(blue_vec);

// Change all pixels from blue to red.
concurrency::parallel_for_each(av_red.extent, [=](index<1> idx) restrict(amp)
    {
        av_red[idx] = 255;
        av_blue[idx] = 0;
    });
```

## <a name="see-also"></a>请参阅

[创建第一个 UWP 应用使用 c + +](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)<br/>
[用 C++ 创建 Windows 运行时组件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)