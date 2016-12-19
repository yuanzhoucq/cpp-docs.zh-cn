---
title: "在 Windows 应用商店应用程序中使用 C++ AMP | Microsoft Docs"
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
ms.assetid: 85577298-2c28-4209-9470-eb21048615db
caps.latest.revision: 14
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在 Windows 应用商店应用程序中使用 C++ AMP
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

可以在您的 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中使用 C\+\+ AMP \(C\+\+ Accelerated Massive Parallelism\) 来执行 GPU（图形处理单元）或其他计算加速器上的计算。  但是，C\+\+ AMP 不提供用于处理 Windows 运行时 \(WinRT\) 类型的 API，并且 WinRT 不提供 C\+\+ AMP 包装器。  当您使用代码（包括那些您自己创建的代码）中的 WinRT 类型时，您必须将它们转换为与 C\+\+ AMP 兼容的类型。  
  
## 性能注意事项  
 如果您使用 [!INCLUDE[cppwrt](../../build/reference/includes/cppwrt_md.md)] \([!INCLUDE[cppwrt_short](../../build/reference/includes/cppwrt_short_md.md)]\) 创建自己的 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)]应用程序，我们建议您对于将使用 C\+\+ AMP. 处理的数据使用纯旧数据 \(POD\) 和连续存储（如 `std::vector`）或 C 样式数组。  由于不必产生封送，因此与使用非 POD 类型或 Windows RT 容器相比，这将帮您获得更高的性能。  
  
 在 C\+\+ AMP 内核中，如需访问以这种方式存储的数据，请将 `std::vector` 或数组存储打包到 `concurrency::array_view` 中，再在 `concurrency::parallel_for_each` 循环中使用数组视图：  
  
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
  
## 排列 Windows 运行时类型  
 使用 WinRT API 时，您可能希望使用存储在 WinRT 容器中的数据上的 C\+\+ AMP （例如 `Platform::Array<T>^`）或复杂的数据类型（例如通过使用`ref` 关键字或 `value` 关键字声明的类或结构）。  在这些情况下，必须执行一些额外工作使数据可用于 C\+\+ AMP。  
  
### Platform::Array\<T\>^，其中 T 为 POD 类型  
 当遇到 `Platform::Array<T>^` 且 T 为 POD 类型时，只需通过使用 `get` 成员函数就可访问基础存储：  
  
```cpp  
Platform::Array<float>^ arr; // Assume that this was returned by a Windows Runtime API  
concurrency::array_view<float, 1> av(arr->Length, &arr->get(0));  
  
```  
  
 如果 T 不是 POD 类型，请使用下述方法来通过 C\+\+ AMP 处理数据。  
  
### Windows 运行时类型: 引用类和值类  
 C\+\+ AMP 不支持复杂的数据类型。  这包括非 POD 类型和使用 `ref` 关键字或 `value` 关键字进行声明的任何类型。  如果在 `restrict(amp)` 上下文使用不支持的类型，则会生成编译时错误。  
  
 遇到不支持的类型时，您可以将其数据中有意义的部分复制到 `concurrency::array` 对象中。  除使 C\+\+ AMP 可使用数据外，此手动复制方法还可通过最大化数据局部性以及确保不使用的数据不复制到加速器中来提升性能。  可以通过使用*暂存数组*进一步提升性能。暂存数组是 `concurrency::array` 的一种特殊形式，可以向 AMP 运行时提供关于数组应进行优化的提示，以便其自身与指定加速器上的其他数组可以频繁转移。  
  
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
..property int b;  
};  
  
// Some other file  
std::vector<pixel_color^> pixels (256);   
  
for(pixel_color ^pixel : pixels)   
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
  red_vec[i] = pixels[i]->r; blue_vec[i] = pixels[i]->b;  
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
  
## 请参阅  
 [Create your first Windows Store app using C\+\+](http://go.microsoft.com/fwlink/p/?LinkId=249073)   
 [Creating Windows Runtime Components in C\+\+](http://go.microsoft.com/fwlink/p/?LinkId=249076)