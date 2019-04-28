---
title: 基本类型 (C++/CX)
ms.date: 01/22/2017
ms.assetid: c9f82907-25f2-440b-91d6-afb8dbd46ea6
ms.openlocfilehash: 2bd5be01b868fd3086c2064edfd4ca343db425be
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301444"
---
# <a name="fundamental-types-ccx"></a>基本类型 (C++/CX)

除了标准C++内置类型C++/CX 支持的类型系统的基本 Windows 运行时类型映射到标准，从而 typedef 定义由 Windows 运行时体系结构的C++类型... C++/CX 实现一个布尔值、 字符和数值基本类型。 这些 typedef 在永远不需要显式指定的 `default` 命名空间中进行定义。 此外， C++/CX 提供了包装和具体实现某些 Windows 运行时类型和接口。

## <a name="boolean-and-character-types"></a>布尔值和字符类型

下表列出了内置布尔值和字符类型及其的标准 C++ 等效项。

|命名空间|C++/CX 名称|定义|标准 C++ 名称|值的范围|
|---------------|-----------------------------------------------------------------------|----------------|-------------------------|---------------------|
|平台|Boolean|8 位布尔值。|bool|**true** （非零） 和**false** （零）|
|default|char16|表示 Unicode (UTF-16) 码位的 16 位非数字值。|wchar_t<br /><br /> 或<br /><br /> L'c'|（由 Unicode 标准指定）|

## <a name="numeric-types"></a>数值类型

下表列出了内置数值类型。 数值类型在 `default` 命名空间中进行声明，是用于对应 C++ 内置类型的 typedef。 并非所有C++内置类型 (例如 long) 支持在 Windows 运行时中。 以保持一致性和清晰起见，我们建议你使用C++/CX 名称。

|C++/CX 名称|定义|标准 C++ 名称|值的范围|
|-----------------------------------------------------------------------|----------------|-------------------------|---------------------|
|int8|8 位带符号数值。|signed char|-128 到 127|
|uint8|8 位无符号数值。|unsigned char|0 到 255|
|int16|16 位带符号整数。|short|-32,768 到 32,767|
|uint16|16 位无符号整数。|unsigned short|0 到 65,535|
|int32|32 位带符号整数。|int|-2,147,483,648 到 2,147,483,647|
|uint32|32 位无符号整数。|unsigned int|0 到 4,294,967,295|
|int64|64 位带符号整数。|long long  -or- __int64|-9,223,372,036,854、 到 9223372036854775807 775,808|
|uint64|64 位无符号整数。|无符号长长的或 unsigned __int64|0 到 18,446,744,073,709,551,615|
|float32|32 位 IEEE 754 浮点数。|float|3.4E +/- 38（7 位数）|
|float64|64 位 IEEE 754 浮点数。|double|1.7E +/- 308（15 位数）|

## <a name="windows-runtime-types"></a>Windows 运行时类型

下表列出了一些其他类型的定义由 Windows 运行时体系结构和内置于C++/CX。 Object 和 String 是引用类型。 其他类型是值类型。 所有这些类型都在 `Platform` 命名空间中进行声明。 有关完整列表，请参见 [Platform namespace](../cppcx/platform-namespace-c-cx.md)。

|名称|定义|
|----------|----------------|
|对象|表示任何 Windows 运行时类型。|
|String|一系列表示文本的字符。|
|Rect|一组浮点数，共四个，表示一个矩形的位置和大小。|
|SizeT|指定高度和宽度的一对有序浮点数。|
|点|定义二维平面中的点的一对有序浮点 x 坐标和 y 坐标。|
|GUID|用作唯一标识符的 128 位非数字值。|
|UIntPtr|（仅限内部使用。）用作指针的 64 位无符号值。|
|IntPtr|（仅限内部使用。）用作指针的 64 位带符号值。|

## <a name="see-also"></a>请参阅

[类型系统](../cppcx/type-system-c-cx.md)
