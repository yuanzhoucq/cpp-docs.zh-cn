---
title: _ITERATOR_DEBUG_LEVEL
ms.date: 11/04/2016
f1_keywords:
- _ITERATOR_DEBUG_LEVEL
helpviewer_keywords:
- _ITERATOR_DEBUG_LEVEL
ms.assetid: 718549cd-a9a9-4ab3-867b-aac00b321e67
ms.openlocfilehash: 7b573127518969accdfdcc4a25a50269dd6aa002
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456401"
---
# <a name="iteratordebuglevel"></a>_ITERATOR_DEBUG_LEVEL

_ITERATOR_DEBUG_LEVEL 宏控制是否启用[检查迭代](../standard-library/checked-iterators.md)[器和调试迭代器支持](../standard-library/debug-iterator-support.md)。 此宏取代并组合了较旧的 _SECURE_SCL 和 _HAS_ITERATOR_DEBUGGING 宏的功能。

## <a name="macro-values"></a>宏值

下表汇总了 _ITERATOR_DEBUG_LEVEL 宏的可能值。

|编译模式|宏值|描述|
|----------------------|----------------|-----------------|
|**调试**|||
||0|禁用经过检查的迭代器，并禁用迭代器调试。|
||1|启用经过检查的迭代器，禁用迭代器调试。|
||2（默认值）|启用迭代器调试；经过检查的迭代器不相关。|
|**发布**|||
||0（默认值）|禁用经过检查的迭代器。|
||1|启用经过检查的迭代器；迭代器调试不相关。|

在发布模式下, 如果将 _ITERATOR_DEBUG_LEVEL 指定为 2, 则编译器将生成错误。

## <a name="remarks"></a>备注

_ITERATOR_DEBUG_LEVEL 宏控制是否启用[检查迭代](../standard-library/checked-iterators.md)器, 并控制调试模式下是否启用了[调试迭代器支持](../standard-library/debug-iterator-support.md)。 如果将 _ITERATOR_DEBUG_LEVEL 定义为1或 2, 则检查迭代器可确保容器的边界不会被覆盖。 如果 _ITERATOR_DEBUG_LEVEL 为 0, 则不检查迭代器。 当 _ITERATOR_DEBUG_LEVEL 定义为1时, 任何不安全迭代器都将导致运行时错误, 并且程序将终止。 当 _ITERATOR_DEBUG_LEVEL 定义为2时, 不安全迭代器使用会导致断言和运行时错误对话框, 使你可以中断到调试器。

由于 _ITERATOR_DEBUG_LEVEL 宏支持与 _SECURE_SCL 和 _HAS_ITERATOR_DEBUGGING 宏类似的功能, 因此您可能不确定在特定情况下使用哪个宏和宏值。 为了避免混淆, 我们建议您仅使用 _ITERATOR_DEBUG_LEVEL 宏。 此表描述了用于现有代码中的 _SECURE_SCL 和 _HAS_ITERATOR_DEBUGGING 的各种值的等效 _ITERATOR_DEBUG_LEVEL 宏值。

|**_ITERATOR_DEBUG_LEVEL** |**_SECURE_SCL** |**_HAS_ITERATOR_DEBUGGING**|
|---|---|---|
|0（发布默认值）|0（已禁用）|0（已禁用）|
|1|1（已启用）|0（已禁用）|
|2（调试默认值）|（不相关）|1（在调试模式中启用）|

有关如何禁用经过检查的迭代器的警告信息，请参阅 [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md)。

### <a name="example"></a>示例

若要为 _ITERATOR_DEBUG_LEVEL 宏指定值, 请使用[/d](../build/reference/d-preprocessor-definitions.md)编译器选项在命令行上对其进行定义, 或在`#define`将C++标准库标头包含在源文件中之前使用。 例如, 在命令行中, 若要在调试模式下编译*sample* , 并使用调试迭代器支持, 可以指定 _ITERATOR_DEBUG_LEVEL 宏定义:

`cl /EHsc /Zi /MDd /D_ITERATOR_DEBUG_LEVEL=1 sample.cpp`

在源文件中，请在定义迭代器的任何标准库标头前指定宏。

```cpp
// sample.cpp

#define _ITERATOR_DEBUG_LEVEL 1

#include <vector>

// ...
```

## <a name="see-also"></a>请参阅

[经过检查的迭代器](../standard-library/checked-iterators.md)\
[调试迭代器支持](../standard-library/debug-iterator-support.md)\
[：C++ 标准库](../standard-library/safe-libraries-cpp-standard-library.md)
