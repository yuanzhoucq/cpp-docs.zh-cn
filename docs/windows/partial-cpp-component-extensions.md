---
title: 部分 （c + + 组件扩展） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- partial_CPP
dev_langs:
- C++
helpviewer_keywords:
- partial
- C++/CX, partial
ms.assetid: 43adf1f5-10c5-44aa-a66f-7507e2bdabf8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 92fd30b0b420080d33f9938bec4891ac80ac660d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597073"
---
# <a name="partial--c-component-extensions"></a>部分（C++ 组件扩展）

**分部**关键字，相同的 ref 类，以编写独立地在不同的文件中的不同部分。

## <a name="all-runtimes"></a>所有运行时

（此语言功能仅适用于 Windows 运行时。）

## <a name="windows-runtime"></a>Windows 运行时

有两个分部定义的 ref 类**分部**关键字应用于定义的第一个匹配项，这通常是通过自动生成的代码，以便在人工程序员不经常使用关键字。 有关类的所有后续部分定义，省略**分部**从修饰符*类键*关键字和类标识符。 当编译器遇到以前定义的 ref 类和类标识符但没有**分部**关键字，它在内部将合并到一个定义的 ref 类定义的部件的所有。

### <a name="syntax"></a>语法

```cpp
partial class-key identifier {
   /* The first part of the partial class definition. 
      This is typically auto-generated */
}
// ...
class-key identifier {
   /* The subsequent part(s) of the class definition. The same 
      identifier is specified, but the "partial" keyword is omitted. */
}
```

### <a name="parameters"></a>参数

*类键*  
声明类或结构的 Windows 运行时支持的关键字。 任一**ref 类**，**值类**， **ref 结构**，或者**值结构**。

*identifier*  
定义类型的名称。

### <a name="remarks"></a>备注

分部类支持在其中修改一个文件，并自动代码生成软件中的类定义的一部分的方案，例如，在 XAML 设计器 — 修改另一个文件中的相同类中的代码。 通过使用分部类，您可以防止覆盖您的代码的自动代码生成器。 在 Visual Studio 项目中，**分部**修饰符自动应用于生成的文件。

内容： 有两个例外，分部类定义可以包含任何内容的完整类定义可能包含如果**分部**关键字被省略。 但是，不能指定类可访问性 (例如， `public partial class X { ... };`)，或**declspec**。

访问说明符的分部类定义中使用*标识符*不会影响在后续部分或完整类定义中的默认可访问性*标识符*。 允许静态数据成员的内联定义。

声明： 类的分部定义*标识符*只引入名称*标识符*，但*标识符*不能以需要类的方式使用定义。 名称*标识符*不能使用知道的大小*标识符*，或使用基或成员*标识符*直到编译器遇到的完整定义后*标识符*。

编号和排序： 可以有零个或多个分部类定义*标识符*。 每个分部类定义*标识符*必须从词法上位于之前的一个完整定义*标识符*(如果没有完整定义; 否则，类不能使用除像前向声明），但需要在前面的前向声明*标识符*。 所有的类密钥必须匹配。

完整定义： 在类的完整定义点*标识符*，行为是相同的像的定义*标识符*，声明了所有基类、 成员等中的顺序它们已遇到和定义分部类中。

模板： 局部类不能为模板。

泛型： 如果的完整定义可以为泛型，分部类可以是泛型。 但每个部分和完整的类必须具有完全相同泛型的参数，包括正式参数名称。

有关如何使用详细信息**分部**关键字，请参阅[分部类 (C + + /cli CX)](http://go.microsoft.com/fwlink/p/?LinkId=249023)。

### <a name="requirements"></a>要求

编译器选项：`/ZW`

## <a name="common-language-runtime"></a>公共语言运行时

（此语言功能不适用于公共语言运行时。）

## <a name="see-also"></a>请参阅

[分部类 (C + + /cli CX)](http://go.microsoft.com/fwlink/p/?LinkId=249023)