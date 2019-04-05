---
title: no_injected_text （c + + COM 属性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.no_injected_text
helpviewer_keywords:
- no_injected_text attribute
ms.assetid: 5256f808-e41e-4f4a-9ea5-e447919f5696
ms.openlocfilehash: 354643020e704a87daa2e56e923b6a0a704bf0b5
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59038364"
---
# <a name="noinjectedtext"></a>no_injected_text

禁止编译器注入代码作为特性使用结果。

## <a name="syntax"></a>语法

```cpp
[ no_injected_text(boolean) ];
```

### <a name="parameters"></a>参数

*boolean*<br/>
（可选）**，则返回 true**如果你想注入，没有代码**false**若要允许代码注入。 **true**是默认值。

## <a name="remarks"></a>备注

最常见用法**no_injected_text** c + + 属性是通过[/Fx](../../build/reference/fx-merge-injected-code.md)编译器选项，将插入**no_injected_text**属性拖动到.mrg 文件。

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

[编译器特性](compiler-attributes.md)