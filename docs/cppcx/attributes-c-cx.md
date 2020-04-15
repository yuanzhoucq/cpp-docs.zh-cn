---
title: 特性 (C++/CX)
ms.date: 12/30/2016
ms.assetid: 4438e03c-4de3-433d-abcc-31aa863bc0e0
ms.openlocfilehash: 437432ce32497311a9a91237118d6088881662a1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371871"
---
# <a name="attributes-ccx"></a>特性 (C++/CX)

属性是一种特殊的 ref 类，可以在方括号中预置到 Windows 运行时类型和方法，以指定元数据创建中的某些行为。 多个预定义属性（例如[，Windows：：基础：元数据：：WebHostHidden）](/uwp/api/Windows.Foundation.Metadata.WebHostHiddenAttribute)通常用于C++/CX 代码。 此示例演示如何将特性应用于类：

[!code-cpp[cx_attributes#01](../cppcx/codesnippet/CPP/cx_attributes/class1.h#01)]

## <a name="custom-attributes"></a>自定义属性

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

## <a name="see-also"></a>另请参阅

[类型系统 (C++/CX)](../cppcx/type-system-c-cx.md)<br/>
[C++/CX 语言参考](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[命名空间参考](../cppcx/namespaces-reference-c-cx.md)
