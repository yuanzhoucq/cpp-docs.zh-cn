---
title: CLR 集成 (C++/CX)
ms.date: 01/22/2017
ms.assetid: 76e213cf-2f3d-4181-b35b-9fd25d5b307c
ms.openlocfilehash: 44ef35d1a62706cae37285c06547a8b9b7deb35c
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740296"
---
# <a name="clr-integration-ccx"></a>CLR 集成 (C++/CX)

某些 Windows 运行时类型接收/Cx 中C++的特殊处理以及基于公共语言运行时（CLR）的语言。 本文讨论一种语言中的几种类型如何映射到另一种语言。 例如，CLR 将 Windows.Foundation.IVector 映射到 System.Collections.IList，将 Windows.Foundation.IMap 映射到 System.Collections.IDictionary，等等。 同样， C++/cx 专门映射类型，如 Platform：:D 委托和 platform：： String。

## <a name="mapping-the-windows-runtime-to-ccx"></a>将 Windows 运行时映射到C++/cx

当C++/Cx 读取 Windows 元数据（winmd）文件时，编译器会自动将常见 Windows 运行时命名空间和类型C++映射到/cx 命名空间和类型。 例如，数字 Windows 运行时类型`UInt32`自动映射到。 `default::uint32`

C++/CX 将一些其他 Windows 运行时类型映射到**平台**命名空间。 例如， **Windows：： Foundation** HSTRING 句柄（表示只读 Unicode 文本字符串）映射到C++/cx `Platform::String`类。 当 Windows 运行时操作返回错误 HRESULT 时，它将映射到C++/cx。 `Platform::Exception`

C++/Cx 还映射 Windows 运行时命名空间中的某些类型以增强类型的功能。 对于这些类型， C++/cx 提供了 helper 构造函数和特定于C++类型的标准 winmd 文件中无法使用的方法。

下表显示支持新构造函数和帮助器方法的值结构。 如果以前编写了使用结构初始化列表的代码，请将它更改为使用新添加的构造函数。

**Windows::Foundation**

- 点

- Rect

- Size

**Windows::UI**

- 颜色

**Windows::UI::Xaml**

- CornerRadius

- Duration

- GridLength

- Thickness

**Windows::UI::Xaml::Interop**

- TypeName

**Windows::UI::Xaml::Media**

- 矩阵

**Windows::UI::Xaml::Media::Animation**

- KeyTime

- RepeatBehavior

**Windows::UI::Xaml::Media::Media3D**

- Matrix3D

## <a name="mapping-the-clr-to-ccx"></a>将 CLR 映射到C++/cx

当 Microsoft C++或C#编译器读取 winmd 文件时，它们会将元数据文件中的某些类型自动映射到C++适当的/cx 或 CLR 类型。 例如，在 CLR 中，IVector\<t > 接口映射到 IList\<t >。 但在C++/cx 中，IVector\<T > 接口未映射到另一种类型。

IReference\<t > 在 Windows 运行时映射到 .net 中\<的可以为 null 的 t >。

## <a name="see-also"></a>请参阅

[与其他语言进行互操作](../cppcx/interoperating-with-other-languages-c-cx.md)
