---
title: v1_enum （C++ COM 特性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.v1_enum
helpviewer_keywords:
- v1_enum attribute
ms.assetid: 2fe92d92-81b9-4a1c-b6ce-437d0eb770ca
ms.openlocfilehash: 1a189f6f1c5ef9d4ae77df9f1eda3f3671ddaf52
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166102"
---
# <a name="v1_enum"></a>v1_enum

指示指定的枚举类型传输为32位实体，而不是16位默认值。

## <a name="syntax"></a>语法

```cpp
[v1_enum]
```

## <a name="remarks"></a>备注

**V1_enum** C++特性具有与[v1_enum](/windows/win32/Midl/v1-enum) MIDL 特性相同的功能。

## <a name="example"></a>示例

以下代码演示了如何使用**v1_enum**：

```cpp
// cpp_attr_ref_v1_enum.cpp
// compile with: /LD
[module(name="MyLibrary")];

[export, v1_enum]
enum eList {
   e1 = 1, e2 = 2
};
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|枚举类型|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另请参阅

[IDL 特性](idl-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 特性](typedef-enum-union-and-struct-attributes.md)
