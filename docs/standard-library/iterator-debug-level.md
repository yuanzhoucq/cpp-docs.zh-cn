---
title: _ITERATOR_DEBUG_LEVEL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- _ITERATOR_DEBUG_LEVEL
dev_langs:
- C++
helpviewer_keywords:
- _ITERATOR_DEBUG_LEVEL
ms.assetid: 718549cd-a9a9-4ab3-867b-aac00b321e67
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3b317358a00879d4430b94ea29ab547761044e56
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="iteratordebuglevel"></a>_ITERATOR_DEBUG_LEVEL

`_ITERATOR_DEBUG_LEVEL` 宏控制是否启用[经过检查的迭代器](../standard-library/checked-iterators.md)和[调试迭代器支持](../standard-library/debug-iterator-support.md)。 该宏取代并合并了较旧的宏 `_SECURE_SCL` 和 `_HAS_ITERATOR_DEBUGGING` 的功能。

## <a name="macro-values"></a>宏值

下表总结了 `_ITERATOR_DEBUG_LEVEL` 宏的可能值。

|编译模式|宏值|描述|
|----------------------|----------------|-----------------|
|**调试**|||
||0|禁用经过检查的迭代器，并禁用迭代器调试。|
||1|启用经过检查的迭代器，禁用迭代器调试。|
||2（默认值）|启用迭代器调试；经过检查的迭代器不相关。|
|**发布**|||
||0（默认值）|禁用经过检查的迭代器。|
||1|启用经过检查的迭代器；迭代器调试不相关。|

在发布模式下，如果将 `_ITERATOR_DEBUG_LEVEL` 指定为 2，则编译器会生成一个错误。

## <a name="remarks"></a>备注

`_ITERATOR_DEBUG_LEVEL` 宏控制是否启用[经过检查的迭代器](../standard-library/checked-iterators.md)，在调试模式下，此宏控制是否启用[调试迭代器支持](../standard-library/debug-iterator-support.md)。 如果将 `_ITERATOR_DEBUG_LEVEL` 定义为 1 或 2，检查迭代器可确保容器的边界不被覆盖。 如果 `_ITERATOR_DEBUG_LEVEL` 为 0，则迭代器未经过检查。 如果 `_ITERATOR_DEBUG_LEVEL` 定义为 1，任何迭代器的非安全使用都会导致运行时错误，并且程序会终止。 如果 `_ITERATOR_DEBUG_LEVEL` 定义为 2，迭代器的非安全使用会导致出现断言和一个可用以中断调试器的运行时错误对话框。

因为宏 `_ITERATOR_DEBUG_LEVEL` 支持类似于宏 `_SECURE_SCL` 和 `_HAS_ITERATOR_DEBUGGING` 的功能，所以在某些特定情况下可能不确定应使用哪个宏和宏值。 为避免混淆，建议仅使用 `_ITERATOR_DEBUG_LEVEL` 宏。 此表介绍了现有代码中用于 `_SECURE_SCL` 和 `_HAS_ITERATOR_DEBUGGING` 的各种值的等效 `_ITERATOR_DEBUG_LEVEL` 宏值。

|**_ITERATOR_DEBUG_LEVEL** |**_SECURE_SCL** |**_HAS_ITERATOR_DEBUGGING**|
|---|---|---|
|0（发布默认值）|0（已禁用）|0（已禁用）|
|1|1（已启用）|0（已禁用）|
|2（调试默认值）|（不相关）|1（在调试模式中启用）|

有关如何禁用经过检查的迭代器的警告信息，请参阅 [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md)。

### <a name="example"></a>示例

若要为 `_ITERATOR_DEBUG_LEVEL` 宏指定值，请使用 [/D](../build/reference/d-preprocessor-definitions.md) 编译器选项在命令行上对其进行定义，或在将 C++ 标准库标头包含在源文件前使用 `#define`。 例如，在命令行中，若要在调试模式下编译 *sample.cpp* 并使用调试迭代器支持，则可指定 `_ITERATOR_DEBUG_LEVEL` 宏定义：

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
[安全库：C++ 标准库](../standard-library/safe-libraries-cpp-standard-library.md)<br/>
