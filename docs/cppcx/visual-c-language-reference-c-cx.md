---
title: "Visual C++ 语言参考 (C++-CX) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3f6abf92-4e5e-4ed8-8e11-f9252380d30a
caps.latest.revision: 27
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 27
---
# Visual C++ 语言参考 (C++-CX)
[!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)] \([!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]\) 是 C\+\+ 语言的一组扩展，通过这些扩展，可用一种尽可能接近现代 C\+\+ 的惯用语法创建 Windows 应用和 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 组件。 使用 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 通过本机代码编写 Windows 应用和组件，而本机代码可与 Visual C\#、Visual Basic、JavaScript 和其他支持 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 的语言轻松交互。 少数情况下需要直接访问原始 COM 接口或非异常代码，在这些情况下可使用 [Windows 运行时 C\+\+ 模板库 \(WRL\)](~/windows/windows-runtime-cpp-template-library-wrl.md)。  
  
 新模型代表 Windows 上的下一代本机 C\+\+ 编程。 你可以使用它来创建：  
  
-   使用 XAML 定义用户界面和使用本机堆栈的 C\+\+ Windows 应用。 有关详细信息，请参阅[在 C\+\+ \(Windows 10\) 中创建一个“hello world”应用](http://msdn.microsoft.com/library/windows/apps/dn996906.aspx)。  
  
-   可供基于 JavaScript 的 Windows 应用使用的 C\+\+ [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 组件。 有关详细信息，请参阅[用 C\+\+ 创建 Windows 运行时组件](http://msdn.microsoft.com/library/hh441569.aspx)[用 C\+\+ 创建 Windows 运行时组件](http://msdn.microsoft.com/library/5b7251e6-4271-4f13-af80-c1cf5b1489bf)。  
  
-   Windows DirectX 游戏和图形密集型应用程序。 有关详细信息，请参阅[使用 DirectX 创建简单的通用 Windows 平台 \(UWP\) 游戏](http://msdn.microsoft.com/library/windows/apps/xaml/mt210793.aspx)。  
  
## 相关文章  
  
|||  
|-|-|  
|[快速参考](../cppcx/quick-reference-c-cx.md)|[!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)] \([!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]\) 的关键字和运算符表。|  
|[类型系统](../cppcx/type-system-c-cx.md)|描述基本的 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 类型和编程构造，以及如何利用 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 来使用和创建 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]类型。|  
|[生成应用程序和库](../cppcx/building-apps-and-libraries-c-cx.md)|讨论如何使用 IDE 生成应用程序并链接到静态库和 DLL。|  
|[与其他语言的互操作性](../cppcx/interoperating-with-other-languages-c-cx.md)|讨论用 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 编写的组件如何才能与用 JavaScript、任何托管语言或 [!INCLUDE[cppwrl](../cppcx/includes/cppwrl-md.md)]编写的组件一起使用。|  
|[线程处理和封送处理](../cppcx/threading-and-marshaling-c-cx.md)|讨论如何为你创建的组件指定线程处理和封送行为。|  
|[命名空间参考](../cppcx/namespaces-reference-c-cx.md)|默认命名空间、平台命名空间、Platform::Collections 和相关命名空间的参考文档。|  
|[通用 Windows 平台应用中不支持的 CRT 函数](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)|列出 Windows 运行时应用中不可用的 CRT 函数。|  
|[如何指导使用 Windows 10 应用](http://msdn.microsoft.com/library/windows/apps/xaml/mt244352.aspx)|提供有关 Windows 10 应用的深入指导以及详细信息的链接。|  
  
1.  [C\+\+\/CX \[n\] 的第 0 部分：简介](http://blogs.msdn.com/b/vcblog/archive/2012/08/29/cxxcxpart00anintroduction.aspx)  
  
2.  [C\+\+\/CX \[n\] 的第 0 部分：简介](http://blogs.msdn.com/b/vcblog/archive/2012/08/29/cxxcxpart00anintroduction.aspx)  
  
3.  [C\+\+\/CX \[n\] 的第 2 部分：带尖角符号的类型](http://blogs.msdn.com/b/vcblog/archive/2012/09/17/cxxcxpart02typesthatwearhats.aspx)  
  
4.  [C\+\+\/CX \[n\] 的第 3 部分：正在构造](http://blogs.msdn.com/b/vcblog/archive/2012/10/05/cxxcxpart03underconstruction.aspx)  
  
5.  [C\+\+\/CX \[n\] 的第 4 部分：静态成员函数](http://blogs.msdn.com/b/vcblog/archive/2012/10/19/cxxcxpart04staticmemberfunctions.aspx)