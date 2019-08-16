---
title: cpp_quote (C++ COM 特性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.cpp_quote
helpviewer_keywords:
- cpp_quote attribute
ms.assetid: f75327ff-42bd-498b-9177-7ffa25427e1f
ms.openlocfilehash: 905c9fc41b1b42dffe9c7b39fae0b096cdc24950
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501767"
---
# <a name="cpp_quote"></a>cpp_quote

向生成的 .idl 文件发出指定的字符串 (不含引号字符)。

## <a name="syntax"></a>语法

```cpp
[ cpp_quote("statement") ];
```

### <a name="parameters"></a>参数

statement<br/>
C 指令。

## <a name="remarks"></a>备注

如果要将预处理器指令放入 .idl 文件, 则**cpp_quote** C++特性非常有用。

还可以使用**cpp_quote**并生成 .h 文件作为 MIDL 编译的一部分。 例如, 如果你有一个C++使用C++ IDL 特性但无法将此文件用于某些任务的标头文件, 则可以对其进行编译, 以创建一个应能使用的 MIDL 生成的 .h 文件。

**Cpp_quote**特性具有与[cpp_quote](/windows/win32/Midl/cpp-quote) MIDL 特性相同的功能。

## <a name="example"></a>示例

有关示例, 请参阅[双重](dual.md)示例使用如何使用**cpp_quote**。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用于**|任何位置|
|**可重复**|No|
|**必需的特性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[独立特性](stand-alone-attributes.md)