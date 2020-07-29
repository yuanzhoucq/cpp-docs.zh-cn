---
title: emitidl （c + + COM 特性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.emitidl
helpviewer_keywords:
- emitidl attribute
ms.assetid: 85b80c56-578e-4392-ac03-8443c74ebb7d
ms.openlocfilehash: 4ddf71c385414a28c2b616b359a93a637abc24aa
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222129"
---
# <a name="emitidl"></a>emitidl

指定是否处理所有后续 IDL 特性并将其放置在生成的 .idl 文件中。

## <a name="syntax"></a>语法

```cpp
[ emitidl(state, defaultimports=boolean) ];
```

### <a name="parameters"></a>参数

State<br/>
以下可能的值之一： **`true`** 、 **`false`** 、 `forced` 、 `restricted` 、 `push` 或 `pop` 。

- 如果 **`true`** 为，则在生成的 .idl 文件中放置在源代码文件中遇到的任何 idl 类别属性。 这是**emitidl**的默认设置。

- 如果 **`false`** 为，则在源代码文件中遇到的任何 idl 类别特性都不会放置在生成的 .idl 文件中。

- 如果 `restricted` 为，则允许 IDL 特性位于文件中，而无需[模块](module-cpp.md)特性。 编译器不会生成 .idl 文件。

- 如果为 `forced` ，则重写后续 `restricted` 特性， `module` 如果文件中存在 IDL 特性，则需要文件具有属性。

- `push`允许你将当前**emitidl**设置保存到内部**emitidl**堆栈，并 `pop` 使你能够将**emitidl**设置为内部**emitidl**堆栈顶部的任何值。

`defaultimports=`*布尔值* \(可有可无

- 如果*布尔值*为 **`true`** ，则会将 docobj 导入到生成的 .idl 文件中。 此外，如果与您的源代码中的 .h 文件同名的 .idl 文件位于 .h 文件所在 `#include` 的目录中，则生成的 .idl 文件包含该 .idl 文件的导入语句。

- 如果*布尔值*为 **`false`** ，则不会将 docobj 导入到生成的 .idl 文件中。 必须显式导入包含[import](import.md)的 .idl 文件。

## <a name="remarks"></a>备注

在源代码文件中遇到**emitidl** c + + 属性后，idl 类别属性将放置在生成的 .idl 文件中。 如果没有**emitidl**属性，则源代码文件中的 IDL 属性将输出到生成的 .idl 文件。

源代码文件中可以有多个**emitidl**属性。 如果 `[emitidl(false)];` 在没有后续的文件中遇到 `[emitidl(true)];` ，则不会将任何属性处理到生成的 .idl 文件中。

编译器每次遇到一个新文件时， **emitidl**将隐式设置为 **`true`** 。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用于**|任何位置|
|**且**|否|
|**必需属性**|无|
|**无效的特性**|无|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另请参阅

[编译器特性](compiler-attributes.md)<br/>
[独立属性](stand-alone-attributes.md)
