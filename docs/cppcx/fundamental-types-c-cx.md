---
title: 基本类型 (C++/CX)
ms.date: 01/22/2017
ms.assetid: c9f82907-25f2-440b-91d6-afb8dbd46ea6
ms.openlocfilehash: 3d484d9490a0a5b2ee2e7f92381528124b47701c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230995"
---
# <a name="fundamental-types-ccx"></a>基本类型 (C++/CX)

除了标准的 c + + 内置类型外，c + +/CX 还支持由 Windows 运行时体系结构定义的类型系统，方法是为映射到标准 c + + 类型的 Windows 运行时基础类型提供 typedef。 C + +/CX 实现了布尔、字符和数字基本类型。 这些 typedef 在永远不需要显式指定的 `default` 命名空间中进行定义。 此外，c + +/CX 为某些 Windows 运行时类型和接口提供包装和具体实现。

## <a name="boolean-and-character-types"></a>布尔值和字符类型

下表列出了内置布尔值和字符类型及其的标准 C++ 等效项。

|命名空间|C + +/CX 名称|定义|标准 C++ 名称|值的范围|
|---------------|-----------------------------------------------------------------------|----------------|-------------------------|---------------------|
|平台|布尔值|8 位布尔值。|bool|**`true`**（非零）和 **`false`** （零）|
|default|char16|表示 Unicode (UTF-16) 码位的 16 位非数字值。|wchar_t<br /><br /> -或-<br /><br /> L'c'|（由 Unicode 标准指定）|

## <a name="numeric-types"></a>数字类型

下表列出了内置数值类型。 数值类型在 `default` 命名空间中进行声明，是用于对应 C++ 内置类型的 typedef。 在 Windows 运行时中并不支持所有 c + + 内置类型（例如 long）。 为了保持一致性和清晰性，建议使用 c + +/CX 名称。

|C + +/CX 名称|定义|标准 C++ 名称|值的范围|
|-----------------------------------------------------------------------|----------------|-------------------------|---------------------|
|int8|8 位带符号数值。|signed char|-128 到127|
|uint8|8 位无符号数值。|unsigned char|0 到 255|
|int16|16 位带符号整数。|short|-32768 到32767|
|uint16|16 位无符号整数。|unsigned short|0 到 65,535|
|int32|32 位带符号整数。|int|-2147483648 到2147483647|
|uint32|32 位无符号整数。|unsigned int|0 到 4,294,967,295|
|int64|64 位带符号整数。|长时间-或-__int64|-9223372036854、775808到9223372036854775807|
|uint64|64 位无符号整数。|无符号长长或无符号 __int64|0 到 18,446,744,073,709,551,615|
|float32|32 位 IEEE 754 浮点数。|float|3.4E +/- 38（7 位数）|
|float64|64 位 IEEE 754 浮点数。|Double|1.7E +/- 308（15 位数）|

## <a name="windows-runtime-types"></a>Windows 运行时类型

下表列出了一些由 Windows 运行时体系结构定义并内置于 c + +/CX 中的其他类型。 Object 和 String 是引用类型。 其他类型是值类型。 所有这些类型都在 `Platform` 命名空间中进行声明。 有关完整列表，请参见 [Platform namespace](../cppcx/platform-namespace-c-cx.md)。

|名称|定义|
|----------|----------------|
|Object|表示任意 Windows 运行时类型。|
|字符串|一系列表示文本的字符。|
|Rect|一组浮点数，共四个，表示一个矩形的位置和大小。|
|SizeT|指定高度和宽度的一对有序浮点数。|
|点|定义二维平面中的点的一对有序浮点 x 坐标和 y 坐标。|
|Guid|用作唯一标识符的 128 位非数字值。|
|UIntPtr|（仅供内部使用。）用作指针的无符号64位值。|
|IntPtr|（仅供内部使用。） 用作指针的已签名64位值。|

## <a name="see-also"></a>另请参阅

[类型系统](../cppcx/type-system-c-cx.md)
