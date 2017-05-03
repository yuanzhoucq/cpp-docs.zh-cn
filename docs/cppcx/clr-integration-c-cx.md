---
title: "CLR 集成 (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "01/22/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 76e213cf-2f3d-4181-b35b-9fd25d5b307c
caps.latest.revision: 10
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 10
---
# CLR 集成 (C++/CX)
某些 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 类型在 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 以及基于公共语言运行时 \(CLR\) 的语言中接收特殊处理。 本文讨论一种语言中的几种类型如何映射到另一种语言。 例如，CLR 将 Windows.Foundation.IVector 映射到 System.Collections.IList，将 Windows.Foundation.IMap 映射到 System.Collections.IDictionary，等等。 同样，[!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 特别映射诸如 Platform::Delegate 和 Platform::String 这些类型。  
  
## 将 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 映射到 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]  
 当 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 读取 Windows 元数据 \(.winmd\) 文件时，编译器会自动将公共 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 命名空间和类型映射到 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 命名空间和类型。 例如，数值 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 类型 `UInt32` 自动映射到 `default::uint32`。  
  
 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 将其他几种 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 类型映射到 **Platform** 命名空间。 例如，**Windows::Foundation** HSTRING 句柄（表示只读 Unicode 文本字符串）会映射到 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] `Platform::String` 类。 当 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 操作返回错误 HRESULT 时，它会映射到 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] `Platform::Exception`。 有关详细信息，请参阅[Built\-in Types](http://msdn.microsoft.com/zh-cn/acc196fd-09da-4882-b554-6c94685ec75f)。  
  
 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 还会映射 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 命名空间中的某些类型以增强类型的功能。 对于这些类型，[!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 提供特定于 C\+\+ 并且在类型的标准 .winmd 文件中不可用的帮助器构造函数和方法。  
  
 下表显示支持新构造函数和帮助器方法的值结构。 如果以前编写了使用结构初始化列表的代码，请将它更改为使用新添加的构造函数。  
  
 **Windows::Foundation**  
  
-   点  
  
-   Rect  
  
-   大小  
  
 **Windows::UI**  
  
-   颜色  
  
 **Windows::UI::Xaml**  
  
-   CornerRadius  
  
-   持续时间  
  
-   GridLength  
  
-   Thickness  
  
 **Windows::UI::Xaml::Interop**  
  
1.  TypeName  
  
 **Windows::UI::Xaml::Media**  
  
-   矩阵  
  
 **Windows::UI::Xaml::Media::Animation**  
  
-   KeyTime  
  
-   RepeatBehavior  
  
 **Windows::UI::Xaml::Media::Media3D**  
  
-   Matrix3D  
  
## 将 CLR 映射到 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]  
 当 Visual C\+\+ 或 C\# 编译器读取 .winmd 文件时，它们会自动将元数据文件中的某些类型映射到相应 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 或 CLR 类型。 例如在 CLR 中，IVector\<T\> 接口会映射到 IList\<T\>。 但在 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 中，IVector\<T\> 接口不会映射到另一种类型。  
  
 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 中的 IReference\<T\> 会映射到 .NET 中的 Nullable\<T\>。  
  
## 请参阅  
 [与其他语言的互操作性](../cppcx/interoperating-with-other-languages-c-cx.md)