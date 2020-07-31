---
title: 装箱 (C++/CX)
ms.date: 12/30/2016
ms.assetid: edfb12fa-2a9b-42f6-bdac-d4d76cb8274e
ms.openlocfilehash: 59c7f8ec56a912ed993316fba093b87bd85e16b1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233530"
---
# <a name="boxing-ccx"></a>装箱 (C++/CX)

*Boxing*在将变量传递给采用 Platform：： Object ^ 作为其输入类型的方法时，装箱会将值类型变量（如[Windows：： Foundation：:D atetime](/uwp/api/windows.foundation.datetime)）或基础标量类型（如 **`int`** ）封装在 ref 类中。 [Platform::Object^](../cppcx/platform-object-class.md)

## <a name="passing-a-value-type-to-an-object-parameter"></a>将值类型传递给 Object^ 参数

虽然无需显式装箱变量以将该其传递给类型 [Platform::Object^](../cppcx/platform-object-class.md)的方法参数，但当你检索之前已装箱的值时，必须显式转换回原始类型。

[!code-cpp[cx_boxing#01](../cppcx/codesnippet/CPP/cx_boxing/class1.cpp#01)]

### <a name="using-platformiboxt-to-support-nullable-value-types"></a>使用 Platform：： IBox \<T> 支持可以为 null 的值类型

C# 和 Visual Basic 支持可以为 null 的值类型的概念。 在 c + +/CX 中，你可以使用 `Platform::IBox<T>` 类型来公开支持可以为 null 的值类型参数的公共方法。 下面的示例演示 c + +/CX 公共方法，该方法在 c # 调用方为某个参数传递 null 时返回 null。

[!code-cpp[cx_boxing#02](../cppcx/codesnippet/CPP/cx_boxing/class1.h#02)]

在 C# XAML 客户端中，可按以下方式使用它：

```

// C# client code
    BoxingDemo.Class1 obj = new BoxingDemo.Class1();
    int? a = null;
    int? b = 5;
    var result = obj.Multiply(a,b); //result = null
```

## <a name="see-also"></a>另请参阅

[类型系统 (C++/CX)](../cppcx/type-system-c-cx.md)<br/>
[强制转换 (C++/CX)](../cppcx/casting-c-cx.md)<br/>
[C + +/CX 语言参考](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[命名空间引用](../cppcx/namespaces-reference-c-cx.md)
