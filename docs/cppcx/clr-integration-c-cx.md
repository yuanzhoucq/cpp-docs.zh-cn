---
title: CLR 集成 (C + + /cli CX) |Microsoft 文档
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 76e213cf-2f3d-4181-b35b-9fd25d5b307c
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 50b455bd3b6fd4a96c3181b60904cb7a3250e866
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="clr-integration-ccx"></a>CLR 集成 (C++/CX)
某些 Windows 运行时类型中接收特殊处理在 C + + /cli CX 以及基于公共语言运行时 (CLR) 的语言。 本文讨论一种语言中的几种类型如何映射到另一种语言。 例如，CLR 将 Windows.Foundation.IVector 映射到 System.Collections.IList，将 Windows.Foundation.IMap 映射到 System.Collections.IDictionary，等等。 同样，C + + /cli CX 特别映射诸如 platform:: delegate 和 platform:: string 类型。  
  
## <a name="mapping-the-windows-runtime-to-ccx"></a>将 Windows 运行时映射到 C + + /cli CX  
 当 C + + /cli CX 读取 Windows 元数据 (.winmd) 文件，编译器会自动映射公共 Windows 运行时命名空间和类型到 C + + /CX 命名空间和类型。 例如，数值的 Windows 运行时类型`UInt32`自动映射到`default::uint32`。  
  
 C + + /cli CX 映射到多个其他 Windows 运行时类型**平台**命名空间。 例如， **windows:: foundation** HSTRING 句柄，它表示只读 Unicode 文本字符串，映射到 C + + /cli CX`Platform::String`类。 在 Windows 运行时操作返回的错误 HRESULT 时，它将映射到 C + + /cli CX `Platform::Exception`。 有关详细信息，请参阅 [Built-in Types](http://msdn.microsoft.com/en-us/acc196fd-09da-4882-b554-6c94685ec75f)。  
  
 C + + /cli CX 还会将映射 Windows 运行时命名空间中的某些类型以增强类型的功能。 对于这些类型中，单击 C + + /cli CX 提供帮助器构造函数和方法的特定于 c + + 和该类型的标准.winmd 文件中不可用。  
  
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
  
## <a name="mapping-the-clr-to-ccx"></a>将 CLR 映射到 C + + /cli CX  
 在 Visual c + + 或 C# 编译器读取.winmd 文件，它们自动映射元数据文件中的某些类型到适当的 C + + /cli CX 或 CLR 类型。 例如，在 CLR 中，IVector\<T > 接口映射到 IList\<T >。 但在 C + + /cli CX、 IVector\<T > 接口未映射到另一种类型。  
  
 IReference\<T > 在 Windows 运行时将映射到可以为 Null\<T >.NET 中。  
  
## <a name="see-also"></a>请参阅  
 [与其他语言的互操作性](../cppcx/interoperating-with-other-languages-c-cx.md)