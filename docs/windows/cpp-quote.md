---
title: cpp_quote |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.cpp_quote
dev_langs:
- C++
helpviewer_keywords:
- cpp_quote attribute
ms.assetid: f75327ff-42bd-498b-9177-7ffa25427e1f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: da9e378ff75ec67660b0c29a5765be88a2c06496
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43205661"
---
# <a name="cppquote"></a>cpp_quote

将指定的字符串，而无需引号字符，发送到生成的.idl 文件。

## <a name="syntax"></a>语法

```cpp
[ cpp_quote(
   "statement"
) ];
```

### <a name="parameters"></a>参数

statement  
C 的指令。

## <a name="remarks"></a>备注

**Cpp_quote** c + + 特性会非常有用，如果你想要将预处理器指令放在.idl 文件中。

此外可以使用**cpp_quote**并生成一个.h 文件作为 MIDL 编译的一部分。 例如，如果必须使用 c + + IDL 特性，但不能使用此文件执行一些任务的 c + + 头文件，然后您可以编译它创建 MIDL 生成.h 文件，您应能够使用。

**Cpp_quote**属性具有相同的功能[cpp_quote](/windows/desktop/Midl/cpp-quote) MIDL 特性。

## <a name="example"></a>示例

有关示例，请参阅[双](../windows/dual.md)有关的示例使用如何使用**cpp_quote**。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|任何位置|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。

## <a name="see-also"></a>请参阅

[IDL 特性](../windows/idl-attributes.md)  
[独立特性](../windows/stand-alone-attributes.md)  