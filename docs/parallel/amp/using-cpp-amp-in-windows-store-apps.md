---
title: "在 Windows 应用商店应用中使用 c + + AMP |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 85577298-2c28-4209-9470-eb21048615db
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3fa6b42dd4e00f3b5314806933d06b3c1534b4d7
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/03/2018
---
# <a name="using-c-amp-in-windows-store-apps"></a>在 Windows 应用商店应用程序中使用 C++ AMP
你可以在使用 c + + AMP (c + + Accelerated Massive Parallelism) 你[!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)]应用在 GPU （图形处理单元） 或其他计算加速器上执行计算。 但是，C++ AMP 不提供用于直接处理 Windows 运行时类型的 API，并且 Windows 运行时不提供 C++ AMP 包装器。 当你在代码（包括你自己创建的代码）中使用Windows 运行时类型时，必须将它们转换为与 C++ AMP 兼容的类型。  
  
## <a name="performance-considerations"></a>性能注意事项  
 如果你使用[!INCLUDE[cppwrt](../../build/reference/includes/cppwrt_md.md)]([!INCLUDE[cppwrt_short](../../build/reference/includes/cppwrt_short_md.md)]) 来创建你[!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)]应用程序中，我们建议你使用连续存储配合纯旧数据 (POD) 类型 — 例如，`std::vector`或 C 样式数组-将用于 c + + AMP 的数据。 这可以帮助你实现更高的性能比使用非 POD 类型或 Windows RT 容器，因为没有封送处理具有发生。  
  
 C + + AMP 内核，访问数据存储在这种方式，只需包装`std::vector`或数组中的存储`concurrency::array_view`，然后使用中的数组视图`concurrency::parallel_for_each`循环：  
  
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
 使用 Windows 运行时 API 时，可能需要对存储在 Windows 运行时容器（例如 `Platform::Array<T>^`）或复杂数据类型（例如通过使用 `ref` 关键字或 `value` 关键字声明的类或结构）中的数据应用 C++ AMP。 在这些情况下，你需要执行一些额外的工作，以使数据可用于 c + + AMP。  
  
### <a name="platformarrayt-where-t-is-a-pod-type"></a>Platform:: array\<T > ^，其中 T 为 POD 类型  
 当遇到`Platform::Array<T>^`，T 是 POD 类型，你可以使用访问其基础存储`get`成员函数：  
  
```cpp  
Platform::Array<float>^ arr; // Assume that this was returned by a Windows Runtime API  
concurrency::array_view<float, 1> av(arr->Length, &arr->get(0));
```  
  
 如果 T 不是 POD 类型，使用以下部分中所述的技术来与 c + + AMP 中使用的数据。  
  
### <a name="windows-runtime-types-ref-classes-and-value-classes"></a>Windows 运行时类型: 引用类和值类  
 C + + AMP 不支持复杂数据类型。 这包括非 POD 类型和通过使用声明的任何类型`ref`关键字或`value`关键字。 如果在中使用类型不受支持`restrict(amp)`生成上下文，编译时错误。  
  
 当你遇到类型不受支持时，你可以复制到其数据值得关注的部分`concurrency::array`对象。 除了使数据可用于 c + + AMP 来使用，此手动复制方法还可提高性能，通过最大化数据位置，并通过确保不会使用的数据不复制到快捷键。 您可以通过改进性能进一步*暂存数组*，这是一种特殊形式的`concurrency::array`，它提供对数组应适合与其他阵列之间的频繁传输 AMP 运行时的提示指定的加速键。  
  
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
 [创建使用 c + + 对第一个 Windows 应用商店应用程序](http://go.microsoft.com/fwlink/p/?linkid=249073)   
 [C + + 创建 Windows 运行时组件](http://go.microsoft.com/fwlink/p/?linkid=249076)



