---
title: 枚举 (C++/CX)
ms.date: 12/30/2016
ms.assetid: 99fbbe28-c1cd-43af-9ead-60f90eba6e68
ms.openlocfilehash: 54e413e65b3130b9b83e6d1ed56b5ee87b84e0a3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225756"
---
# <a name="enums-ccx"></a>枚举 (C++/CX)

C + +/CX 支持 `public enum class` 关键字，该关键字类似于标准 c + + `scoped  enum` 。 当你使用通过 `public enum class` 关键字声明的枚举数时，必须使用枚举标识符确定每个枚举值的范围。

### <a name="remarks"></a>备注

没有 `public enum class` 访问说明符（如）的将 **`public`** 被视为标准 c + +[范围枚举](../cpp/enumerations-cpp.md)。

`public enum class`或 `public enum struct` 声明可以有任何整数类型的基础类型，尽管 Windows 运行时本身要求类型为 int32，或者是 uint32 （对于标志枚举）。 以下语法描述 `public enum class` 或 `public enum struct`的一部分。

此示例演示如何定义公共枚举类：

[!code-cpp[cx_enums#01](../cppcx/codesnippet/CPP/cpp/class1.h#01)]

下一个示例演示如何使用枚举类：

[!code-cpp[cx_enums#02](../cppcx/codesnippet/CPP/cpp/class1.h#02)]

### <a name="examples"></a>示例

后续示例演示如何声明枚举。

[!code-cpp[cx_enums#03](../cppcx/codesnippet/CPP/cpp/class1.h#03)]

下一个示例演示如何强制转换为数字等效值和执行比较。 请注意，枚举数 `One` 的使用通过 `Enum1` 枚举标识符来确定范围，枚举数 `First` 通过 `Enum2`来确定范围。

[!code-cpp[cx_enums#04](../cppcx/codesnippet/CPP/cpp/class1.h#04)]

## <a name="see-also"></a>另请参阅

[类型系统](../cppcx/type-system-c-cx.md)<br/>
[C + +/CX 语言参考](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[命名空间引用](../cppcx/namespaces-reference-c-cx.md)
