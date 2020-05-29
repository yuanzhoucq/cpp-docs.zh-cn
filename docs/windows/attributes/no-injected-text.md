---
title: no_injected_text （C++ COM 特性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.no_injected_text
helpviewer_keywords:
- no_injected_text attribute
ms.assetid: 5256f808-e41e-4f4a-9ea5-e447919f5696
ms.openlocfilehash: 5f98be3478b2e1eeb4b464f1784f3f4ece22d8a4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166609"
---
# <a name="no_injected_text"></a>no_injected_text

阻止编译器将代码注入到属性使用的结果中。

## <a name="syntax"></a>语法

```cpp
[ no_injected_text(boolean) ];
```

### <a name="parameters"></a>parameters

*boolean*<br/>
可有可无如果你不想注入代码，**则为 true** ; 如果允许注入代码，则为**false** 。 默认值为**true** 。

## <a name="remarks"></a>备注

**No_injected_text** C++属性最常见的用法是[/fx](../../build/reference/fx-merge-injected-code.md)编译器选项，该选项将**no_injected_text**属性插入 .mrg 文件中。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|任何位置|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另请参阅

[编译器特性](compiler-attributes.md)
