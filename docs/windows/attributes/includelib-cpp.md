---
title: includelib （C++ COM 特性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.includelib
helpviewer_keywords:
- includelib attribute
ms.assetid: cd90ea6e-5ae8-4f11-b8d1-662db95412b2
ms.openlocfilehash: 4022a3f1f2d4ccaabe65c24065be8e1c846d604d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214835"
---
# <a name="includelib-c"></a>includelib (C++)

导致在生成的 .idl 文件中包含 .idl 或 .h 文件。

## <a name="syntax"></a>语法

```cpp
[ includelib(name.idl) ];
```

### <a name="parameters"></a>parameters

*名称 .idl*<br/>
要包含在生成的 .idl 文件中的 .idl 文件的名称。

## <a name="remarks"></a>备注

**Includelib** C++特性会导致在生成的 .idl 文件中包含 .idl 或 .h 文件，`importlib` 语句之后。

## <a name="example"></a>示例

下面的代码显示在 .cpp 文件中：

```cpp
// cpp_attr_ref_includelib.cpp
// compile with: /LD
[module(name="MyLib")];
[includelib("includelib.idl")];
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|任何位置|
|**可重复**|是|
|**必需的特性**|无|
|**无效的特性**|无|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另请参阅

[IDL 特性](idl-attributes.md)<br/>
[独立特性](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[include](include-cpp.md)<br/>
[importlib](importlib.md)
