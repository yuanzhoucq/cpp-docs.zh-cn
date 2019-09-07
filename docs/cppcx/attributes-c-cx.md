---
title: 特性 (C++/CX)
ms.date: 12/30/2016
ms.assetid: 4438e03c-4de3-433d-abcc-31aa863bc0e0
ms.openlocfilehash: 77962dc2d4b7f6bda90a5376e5154782365a4106
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740381"
---
# <a name="attributes-ccx"></a>特性 (C++/CX)

特性是一种特殊的 ref 类，可在方括号中预置，以便 Windows 运行时类型和方法来指定元数据创建中的某些行为。 一些预定义的属性（例如， [Windows：： Foundation：： Metadata：： WebHostHidden](/uwp/api/Windows.Foundation.Metadata.WebHostHiddenAttribute)）通常在/cx C++代码中使用。 此示例演示如何将特性应用于类：

[!code-cpp[cx_attributes#01](../cppcx/codesnippet/CPP/cx_attributes/class1.h#01)]

## <a name="custom-attributes"></a>自定义特性

还可以定义自定义特性。 自定义属性必须符合以下 Windows 运行时规则：

- 自定义特性只能包含公共字段。

- 自定义特性字段可在将特性应用于类时初始化。

- 字段可属于下列类型之一：

   - int32 (int)

   - uint32 (unsigned int)

   - bool

   - Platform::String^

   - Windows::Foundation::HResult

   - Platform::Type^

   - 公共枚举类（包括用户定义的枚举）

下一个示例演示如何定义自定义特性，并在你使用它时进行初始化。

[!code-cpp[cx_attributes#02](../cppcx/codesnippet/CPP/cx_attributes/class1.h#02)]

## <a name="see-also"></a>请参阅

[类型系统 (C++/CX)](../cppcx/type-system-c-cx.md)<br/>
[C++/CX 语言参考](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[命名空间参考](../cppcx/namespaces-reference-c-cx.md)
