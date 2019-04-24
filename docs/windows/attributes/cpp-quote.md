---
title: cpp_quote (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.cpp_quote
helpviewer_keywords:
- cpp_quote attribute
ms.assetid: f75327ff-42bd-498b-9177-7ffa25427e1f
ms.openlocfilehash: 378435ced5a541785b7b32bc9d2f408034d5a2d8
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59024671"
---
# <a name="cppquote"></a>cpp_quote

将指定的字符串，而无需引号字符，发送到生成的.idl 文件。

## <a name="syntax"></a>语法

```cpp
[ cpp_quote("statement") ];
```

### <a name="parameters"></a>参数

statement<br/>
C 的指令。

## <a name="remarks"></a>备注

**Cpp_quote** C++特性会非常有用，如果你想要将预处理器指令放在.idl 文件中。

此外可以使用**cpp_quote**并生成一个.h 文件作为 MIDL 编译的一部分。 例如，如果你有C++使用的标头文件C++然后 IDL 特性，但不能使用此文件执行一些任务，您可以将其编译为创建 MIDL 生成.h 文件，您应能够使用。

**Cpp_quote**属性具有相同的功能[cpp_quote](/windows/desktop/Midl/cpp-quote) MIDL 特性。

## <a name="example"></a>示例

有关示例，请参阅[双](dual.md)有关的示例使用如何使用**cpp_quote**。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|任何位置|
|**可重复**|否|
|**必需的特性**|None|
|**无效的特性**|None|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[独立特性](stand-alone-attributes.md)