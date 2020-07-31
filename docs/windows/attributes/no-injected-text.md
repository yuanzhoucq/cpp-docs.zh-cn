---
title: no_injected_text （c + + COM 特性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.no_injected_text
helpviewer_keywords:
- no_injected_text attribute
ms.assetid: 5256f808-e41e-4f4a-9ea5-e447919f5696
ms.openlocfilehash: 7e5c822c45888f41e8dd849f25658d0139e6fda0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87201240"
---
# <a name="no_injected_text"></a>no_injected_text

阻止编译器将代码注入到属性使用的结果中。

## <a name="syntax"></a>语法

```cpp
[ no_injected_text(boolean) ];
```

### <a name="parameters"></a>参数

*boolean*<br/>
（可选） **`true`** 如果你不希望插入代码，则 **`false`** 允许注入代码。 **`true`** 默认值为。

## <a name="remarks"></a>备注

**No_injected_text** c + + 特性最常见的用法是[/fx](../../build/reference/fx-merge-injected-code.md)编译器选项，该选项将**no_injected_text**特性插入到 .mrg 文件中。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用于**|任何位置|
|**且**|否|
|**必需属性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另请参阅

[编译器特性](compiler-attributes.md)
