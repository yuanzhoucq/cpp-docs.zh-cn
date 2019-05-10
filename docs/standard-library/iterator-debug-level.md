---
title: _ITERATOR_DEBUG_LEVEL
ms.date: 11/04/2016
f1_keywords:
- _ITERATOR_DEBUG_LEVEL
helpviewer_keywords:
- _ITERATOR_DEBUG_LEVEL
ms.assetid: 718549cd-a9a9-4ab3-867b-aac00b321e67
ms.openlocfilehash: a584fe5a97e251205e750507b27e53e6e7b9a20e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62224189"
---
# <a name="iteratordebuglevel"></a>_ITERATOR_DEBUG_LEVEL

_ITERATOR_DEBUG_LEVEL 宏控制是否[检查迭代器](../standard-library/checked-iterators.md)并[调试迭代器支持](../standard-library/debug-iterator-support.md)已启用。 该宏取代并结合了较旧的 _SECURE_SCL 和 _HAS_ITERATOR_DEBUGGING 宏的功能。

## <a name="macro-values"></a>宏值

下表总结了 _ITERATOR_DEBUG_LEVEL 宏的可能值。

|编译模式|宏值|描述|
|----------------------|----------------|-----------------|
|**调试**|||
||0|禁用经过检查的迭代器，并禁用迭代器调试。|
||1|启用经过检查的迭代器，禁用迭代器调试。|
||2（默认值）|启用迭代器调试；经过检查的迭代器不相关。|
|**发布**|||
||0（默认值）|禁用经过检查的迭代器。|
||1|启用经过检查的迭代器；迭代器调试不相关。|

在发布模式下，如果 _ITERATOR_DEBUG_LEVEL 指定为 2，则编译器也会生成错误。

## <a name="remarks"></a>备注

_ITERATOR_DEBUG_LEVEL 宏控制是否[检查迭代器](../standard-library/checked-iterators.md)是否已启用，并在调试模式下，是否[调试迭代器支持](../standard-library/debug-iterator-support.md)已启用。 如果 _ITERATOR_DEBUG_LEVEL 定义为 1 或 2，请确保检查迭代器，不会覆盖容器的边界。 如果 _ITERATOR_DEBUG_LEVEL 为 0，则不会检查迭代器。 如果 _ITERATOR_DEBUG_LEVEL 定义为 1，任何不安全的迭代器使用会导致运行时错误并终止程序。 如果 _ITERATOR_DEBUG_LEVEL 定义为 2，不安全的迭代器使用会导致出现断言和运行时错误对话框，您可以进入调试器。

由于 _ITERATOR_DEBUG_LEVEL 宏支持与 _SECURE_SCL 和 _HAS_ITERATOR_DEBUGGING 宏类似的功能，您可能会不确定要在特定情况下使用的哪个宏和宏值。 为避免混淆，我们建议使用仅 _ITERATOR_DEBUG_LEVEL 宏。 此表描述了要使用的各种值的 _SECURE_SCL 和 _HAS_ITERATOR_DEBUGGING 现有代码中的等效 _ITERATOR_DEBUG_LEVEL 宏值。

|**_ITERATOR_DEBUG_LEVEL** |**_SECURE_SCL** |**_HAS_ITERATOR_DEBUGGING**|
|---|---|---|
|0（发布默认值）|0（已禁用）|0（已禁用）|
|1|1（已启用）|0（已禁用）|
|2（调试默认值）|（不相关）|1（在调试模式中启用）|

有关如何禁用经过检查的迭代器的警告信息，请参阅 [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md)。

### <a name="example"></a>示例

若要指定 _ITERATOR_DEBUG_LEVEL 宏的值，请使用[/D](../build/reference/d-preprocessor-definitions.md)编译器选项来定义命令行上或使用`#define`之前C++标准库标头都包含在源文件中。 例如，在命令行中，若要编译*sample.cpp*在调试模式下以及使用调试迭代器支持，可以指定在 _ITERATOR_DEBUG_LEVEL 宏的定义：

`cl /EHsc /Zi /MDd /D_ITERATOR_DEBUG_LEVEL=1 sample.cpp`

在源文件中，请在定义迭代器的任何标准库标头前指定宏。

```cpp
// sample.cpp

#define _ITERATOR_DEBUG_LEVEL 1

#include <vector>

// ...
```

## <a name="see-also"></a>请参阅

[Checked Iterators](../standard-library/checked-iterators.md)<br/>
[Debug Iterator Support](../standard-library/debug-iterator-support.md)<br/>
[：C++ 标准库](../standard-library/safe-libraries-cpp-standard-library.md)<br/>
