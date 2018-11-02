---
title: 属性 (C++/CX)
ms.date: 01/22/2017
ms.assetid: 64c7bc56-3191-4cd5-bdf4-476d07d285d5
ms.openlocfilehash: a4aadb853ac26d353cbee5f7c0c81436a4c1dfc9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50609388"
---
# <a name="properties-ccx"></a>属性 (C++/CX)

Windows 运行时类型将作为属性公开公共数据。 客户端代码像公共数据成员一样访问该属性。 在内部，该属性实现为包含一个 get 访问器方法、一个 set 访问器方法或二者的块。 通过使用访问器方法，你可以在检索值的前后执行其他操作，例如，可以触发事件或执行验证检查。

### <a name="remarks"></a>备注

属性值包含在私有变量（也称 “后备存储”）中，它与该属性的类型相同。 一个属性可以同时包含 set 访问器（将值赋给后备存储）和 get 访问器（检索后备存储的值）。 如果只提供 get 访问器，则属性是只读的，如果只提供 set 访问器，则属性是只写的，如果两种访问器都提供，则属性是可读写的（可修改）。

 trivial 属性是读/写属性，编译器自动为其实现访问器和后备存储。 你无法访问编译器的实现。 但是，你可以声明一个自定义属性并显式声明其访问器和后备存储。 在访问器中，可以执行所需的任何逻辑，如验证对 set 访问器的输入、根据属性值计算值、访问数据库或在属性变化时触发事件。

实例化 C++/CX ref 类后，在调用其构造函数之前将使用零实例化其内存；因此，在声明时将为所有属性分配默认值零或 nullptr。

### <a name="examples"></a>示例

下面的代码示例演示如何声明和访问属性。 第一个属性 `Name`称为“trivial”  属性，因为编译器自动生成 `set` 访问器、 `get` 访问器和一个后备存储。

第二个属性 `Doctor`是只读属性，因为它指定只显式声明 *访问器的* 属性块 `get` 。 因为声明了属性块，所以必须显式声明一个后备存储，即私有 String^ 变量 `doctor_`。 通常，只读属性只返回后备存储的值。 只有该类自身可以设置后备存储的值，通常是在构造函数中。

第三个属性 `Quantity`是一个读/写属性，因为它声明一个同时声明 `set` 访问器和 `get` 访问器的属性块。

`set` 访问器对所赋的值执行用户定义的有效性测试。 与 C# 不同，此处的名称 *value* 只是 `set` 访问器中参数的标识符，而不是一个关键字。 如果 *value* 不大于零，则将引发 Platform::InvalidArgumentException。 否则，使用所赋的值更新后备存储 `quantity_`。

请注意，属性无法在成员列表中初始化。 当然，你可以初始化成员列表中的后备存储变量。

[!code-cpp[cx_properties#01](../cppcx/codesnippet/CPP/cx_properties/class1.h#01)]

## <a name="see-also"></a>请参阅

[类型系统](../cppcx/type-system-c-cx.md)<br/>
[Visual c + + 语言参考](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[命名空间参考](../cppcx/namespaces-reference-c-cx.md)