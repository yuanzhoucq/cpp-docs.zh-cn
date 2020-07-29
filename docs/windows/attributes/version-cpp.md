---
title: version （c + + COM 特性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.version
helpviewer_keywords:
- version attribute
- version information, version attribute
ms.assetid: db6ce5d8-82c2-4329-b1a8-8ca2f67342cb
ms.openlocfilehash: b537f56c39c33abc52897cf53ea2cc0fb24ee458
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213796"
---
# <a name="version-c"></a>version (C++)

标识类的多个版本中的特定版本。

## <a name="syntax"></a>语法

```cpp
[ version("version") ]
```

### <a name="parameters"></a>参数

*version*<br/>
`coclass` 的版本号。 如果未指定，则将1.0 放置在 .idl 文件中。

## <a name="remarks"></a>备注

**版本**c + + 特性具有与[版本](/windows/win32/Midl/version)MIDL 特性相同的功能，并将传递到生成的 .idl 文件。

## <a name="example"></a>示例

有关**版本**的示例用法，请参阅可[绑定](bindable.md)的示例。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用于**|**`class`**, **`struct`**|
|**且**|否|
|**必需属性**|**coclass**|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另请参阅

[编译器特性](compiler-attributes.md)<br/>
[类特性](class-attributes.md)
