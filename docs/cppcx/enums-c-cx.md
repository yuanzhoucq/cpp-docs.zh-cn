---
title: 枚举 (C++/CX)
ms.date: 12/30/2016
ms.assetid: 99fbbe28-c1cd-43af-9ead-60f90eba6e68
ms.openlocfilehash: f16a288a0b928b74ef42de5781fd1b54930927d6
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345821"
---
# <a name="enums-ccx"></a>枚举 (C++/CX)

C++/CX 支持`public enum class`关键字，它是类似于标准C++ `scoped  enum`。 当你使用通过 `public enum class` 关键字声明的枚举数时，必须使用枚举标识符确定每个枚举值的范围。

### <a name="remarks"></a>备注

没有访问说明符（如 `public enum class` ）的 `public`将作为标准 C++ [范围枚举](../cpp/enumerations-cpp.md)处理。

一个`public enum class`或`public enum struct`声明可以具有任何整型类型的基础类型，尽管 Windows 运行时本身要求类型是 int32 或者 uint32 对于标志枚举。 以下语法描述 `public enum class` 或 `public enum struct`的一部分。

此示例演示如何定义公共枚举类：

[!code-cpp[cx_enums#01](../cppcx/codesnippet/CPP/cpp/class1.h#01)]

下一个示例演示如何使用枚举类：

[!code-cpp[cx_enums#02](../cppcx/codesnippet/CPP/cpp/class1.h#02)]

### <a name="examples"></a>示例

后续示例演示如何声明枚举。

[!code-cpp[cx_enums#03](../cppcx/codesnippet/CPP/cpp/class1.h#03)]

下一个示例演示如何强制转换为数字等效值和执行比较。 请注意，枚举数 `One` 的使用通过 `Enum1` 枚举标识符来确定范围，枚举数 `First` 通过 `Enum2`来确定范围。

[!code-cpp[cx_enums#04](../cppcx/codesnippet/CPP/cpp/class1.h#04)]

## <a name="see-also"></a>请参阅

[类型系统](../cppcx/type-system-c-cx.md)<br/>
[VisualC++语言参考](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[命名空间参考](../cppcx/namespaces-reference-c-cx.md)
