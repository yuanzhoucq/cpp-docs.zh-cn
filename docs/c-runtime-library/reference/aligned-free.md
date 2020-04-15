---
title: _aligned_free
ms.date: 4/2/2020
api_name:
- _aligned_free
- _o__aligned_free
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-heap-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- aligned_free
- _aligned_free
helpviewer_keywords:
- _aligned_free function
- aligned_free function
ms.assetid: ed1ce952-cdfc-4682-85cc-f75d4101603d
ms.openlocfilehash: a6e5f0dcd0bbea436ecdad7abb1fd6fc948f80dc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350719"
---
# <a name="_aligned_free"></a>_aligned_free

释放使用 [_aligned_malloc](aligned-malloc.md) 或 [_aligned_offset_malloc](aligned-offset-malloc.md) 分配的内存块。

## <a name="syntax"></a>语法

```C
void _aligned_free (
   void *memblock
);
```

### <a name="parameters"></a>参数

*memblock*<br/>
指向返回到 `_aligned_malloc` 或 `_aligned_offset_malloc` 函数的内存块的指针。

## <a name="remarks"></a>备注

**_aligned_free**被标记`__declspec(noalias)`，这意味着保证函数不修改全局变量。 有关详细信息，请参阅 [noalias](../../cpp/noalias.md)。

此函数不会验证其参数，这与其他 _aligned CRT 函数不同。 如果*memblock*是 NULL 指针，则此函数仅执行任何操作。 它不会更改 `errno`，也不会调用无效的参数处理程序。 如果由于未使用先前分配内存块的 _aligned 函数或者由于一些不可预见的灾难而使内存不一致，从而导致函数中出现错误，函数将从 [_RPT、_RPTF、_RPTW、_RPTFW 宏](rpt-rptf-rptw-rptfw-macros.md)生成调试报告。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_aligned_free**|\<malloc.h>|

## <a name="example"></a>示例

有关详细信息，请参阅 [_aligned_malloc](aligned-malloc.md)。

## <a name="see-also"></a>另请参阅

[数据对齐](../../c-runtime-library/data-alignment.md)
