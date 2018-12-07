---
title: 堆常量
ms.date: 11/04/2016
f1_keywords:
- _HEAPBADPTR
- _HEAPEMPTY
- _HEAPBADBEGIN
- _HEAPOK
- _HEAPBADNODE
- _HEAPEND
helpviewer_keywords:
- _HEAPOK constants
- _HEAPEND constants
- HEAPBADBEGIN constants
- _HEAPBADNODE constants
- HEAPBADNODE constants
- HEAPBADPTR constants
- _HEAPEMPTY constants
- HEAPEND constants
- HEAPOK constants
- HEAPEMPTY constants
- _HEAPBADBEGIN constants
- _HEAPBADPTR constants
- heap constants
ms.assetid: 3f751bb9-2dc4-486f-b5f5-9061c96d3754
ms.openlocfilehash: 9419ae53cd04812f45f5feeee73fa0f89c408a0c
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2018
ms.locfileid: "51522293"
---
# <a name="heap-constants"></a>堆常量

## <a name="syntax"></a>语法

```

#include <malloc.h>
```

## <a name="remarks"></a>备注

这些常量提供表示堆状态的返回值。

|返回的常量|含义|
|--------------|-------------|
|`_HEAPBADBEGIN`|初始头信息未找到或无效。|
|`_HEAPBADNODE`|找到错误节点，或堆已损坏。|
|`_HEAPBADPTR`|_HEAPINFO 结构的 _pentry 字段不包含堆中的有效指针（仅限 `_heapwalk` 例程）。|
|`_HEAPEMPTY`|尚未初始化堆。|
|`_HEAPEND`|已成功到达堆的结尾处（仅限 `_heapwalk` 例程）。|
|`_HEAPOK`|堆是一致的（仅限 `_heapset` 和 `_heapchk` 例程）。 目前未出现错误；_HEAPINFO 结构包含下一个条目的信息（仅限 `_heapwalk` 例程）。|

## <a name="see-also"></a>请参阅

[_heapchk](../c-runtime-library/reference/heapchk.md)<br/>
[_heapset](../c-runtime-library/heapset.md)<br/>
[_heapwalk](../c-runtime-library/reference/heapwalk.md)<br/>
[全局常量](../c-runtime-library/global-constants.md)